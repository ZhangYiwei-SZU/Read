# 用于预训练BERT的数据集
:label:`sec_bert-dataset`
为了预训练 :numref:`sec_bert`中实现的BERT模型，我们需要以理想的格式生成数据集，以便于两个预训练任务：遮蔽语言模型和下一句预测。一方面，最初的BERT模型是在两个庞大的图书语料库和英语维基百科（参见 :numref:`subsec_bert_pretraining_tasks`）的合集上预训练的，但它很难吸引这本书的大多数读者。另一方面，现成的预训练BERT模型可能不适合医学等特定领域的应用。因此，在定制的数据集上对BERT进行预训练变得越来越流行。为了方便BERT预训练的演示，我们使用了较小的语料库WikiText-2 :cite:`Merity.Xiong.Bradbury.ea.2016`。
与 :numref:`sec_word2vec_data`中用于预训练word2vec的PTB数据集相比，WikiText-2（1）保留了原来的标点符号，适合于下一句预测；（2）保留了原来的大小写和数字；（3）大了一倍以上。
```{.python .input}
#@tab pytorch
from d2l import torch as d2l
import os
import random
import torch
```
在WikiText-2数据集中，每行代表一个段落，其中在任意标点符号及其前面的词元之间插入空格。保留至少有两句话的段落。为了简单起见，我们仅使用句号作为分隔符来拆分句子。我们将更复杂的句子拆分技术的讨论留在本节末尾的练习中。
## 为预训练任务定义辅助函数
在下文中，我们首先为BERT的两个预训练任务实现辅助函数。这些辅助函数将在稍后将原始文本语料库转换为理想格式的数据集时调用，以预训练BERT。
### 生成下一句预测任务的数据
根据 :numref:`subsec_nsp`的描述，`_get_next_sentence`函数生成二分类任务的训练样本。
下面的函数通过调用`_get_next_sentence`函数从输入`paragraph`生成用于下一句预测的训练样本。这里`paragraph`是句子列表，其中每个句子都是词元列表。自变量`max_len`指定预训练期间的BERT输入序列的最大长度。
### 生成遮蔽语言模型任务的数据
:label:`subsec_prepare_mlm_data`
为了从BERT输入序列生成遮蔽语言模型的训练样本，我们定义了以下`_replace_mlm_tokens`函数。在其输入中，`tokens`是表示BERT输入序列的词元的列表，`candidate_pred_positions`是不包括特殊词元的BERT输入序列的词元索引的列表（特殊词元在遮蔽语言模型任务中不被预测），以及`num_mlm_preds`指示预测的数量（选择15%要预测的随机词元）。在 :numref:`subsec_mlm`中定义遮蔽语言模型任务之后，在每个预测位置，输入可以由特殊的“掩码”词元或随机词元替换，或者保持不变。最后，该函数返回可能替换后的输入词元、发生预测的词元索引和这些预测的标签。
通过调用前述的`_replace_mlm_tokens`函数，以下函数将BERT输入序列（`tokens`）作为输入，并返回输入词元的索引（在 :numref:`subsec_mlm`中描述的可能的词元替换之后）、发生预测的词元索引以及这些预测的标签索引。
## 将文本转换为预训练数据集
现在我们几乎准备好为BERT预训练定制一个`Dataset`类。在此之前，我们仍然需要定义辅助函数`_pad_bert_inputs`来将特殊的“&lt;mask&gt;”词元附加到输入。它的参数`examples`包含来自两个预训练任务的辅助函数`_get_nsp_data_from_paragraph`和`_get_mlm_data_from_tokens`的输出。
```{.python .input}
#@tab pytorch
#@save
def _pad_bert_inputs(examples, max_len, vocab):
    max_num_mlm_preds = round(max_len * 0.15)
    all_token_ids, all_segments, valid_lens,  = [], [], []
    all_pred_positions, all_mlm_weights, all_mlm_labels = [], [], []
    nsp_labels = []
    for (token_ids, pred_positions, mlm_pred_label_ids, segments,
         is_next) in examples:
        all_token_ids.append(torch.tensor(token_ids + [vocab['<pad>']] * (
            max_len - len(token_ids)), dtype=torch.long))
        all_segments.append(torch.tensor(segments + [0] * (
            max_len - len(segments)), dtype=torch.long))
        # valid_lens不包括'<pad>'的计数
        valid_lens.append(torch.tensor(len(token_ids), dtype=torch.float32))
        all_pred_positions.append(torch.tensor(pred_positions + [0] * (
            max_num_mlm_preds - len(pred_positions)), dtype=torch.long))
        # 填充词元的预测将通过乘以0权重在损失中过滤掉
        all_mlm_weights.append(
            torch.tensor([1.0] * len(mlm_pred_label_ids) + [0.0] * (
                max_num_mlm_preds - len(pred_positions)),
                dtype=torch.float32))
        all_mlm_labels.append(torch.tensor(mlm_pred_label_ids + [0] * (
            max_num_mlm_preds - len(mlm_pred_label_ids)), dtype=torch.long))
        nsp_labels.append(torch.tensor(is_next, dtype=torch.long))
    return (all_token_ids, all_segments, valid_lens, all_pred_positions,
            all_mlm_weights, all_mlm_labels, nsp_labels)
```
将用于生成两个预训练任务的训练样本的辅助函数和用于填充输入的辅助函数放在一起，我们定义以下`_WikiTextDataset`类为用于预训练BERT的WikiText-2数据集。通过实现`__getitem__ `函数，我们可以任意访问WikiText-2语料库的一对句子生成的预训练样本（遮蔽语言模型和下一句预测）样本。
最初的BERT模型使用词表大小为30000的WordPiece嵌入 :cite:`Wu.Schuster.Chen.ea.2016`。WordPiece的词元化方法是对 :numref:`subsec_Byte_Pair_Encoding`中原有的字节对编码算法稍作修改。为简单起见，我们使用`d2l.tokenize`函数进行词元化。出现次数少于5次的不频繁词元将被过滤掉。
```{.python .input}
#@tab pytorch
#@save
class _WikiTextDataset(torch.utils.data.Dataset):
    def __init__(self, paragraphs, max_len):
        # 输入paragraphs[i]是代表段落的句子字符串列表；
        # 而输出paragraphs[i]是代表段落的句子列表，其中每个句子都是词元列表
        paragraphs = [d2l.tokenize(
            paragraph, token='word') for paragraph in paragraphs]
        sentences = [sentence for paragraph in paragraphs
                     for sentence in paragraph]
        self.vocab = d2l.Vocab(sentences, min_freq=5, reserved_tokens=[
            '<pad>', '<mask>', '<cls>', '<sep>'])
        # 获取下一句子预测任务的数据
        examples = []
        for paragraph in paragraphs:
            examples.extend(_get_nsp_data_from_paragraph(
                paragraph, paragraphs, self.vocab, max_len))
        # 获取遮蔽语言模型任务的数据
        examples = [(_get_mlm_data_from_tokens(tokens, self.vocab)
                      + (segments, is_next))
                     for tokens, segments, is_next in examples]
        # 填充输入
        (self.all_token_ids, self.all_segments, self.valid_lens,
         self.all_pred_positions, self.all_mlm_weights,
         self.all_mlm_labels, self.nsp_labels) = _pad_bert_inputs(
            examples, max_len, self.vocab)
    def __getitem__(self, idx):
        return (self.all_token_ids[idx], self.all_segments[idx],
                self.valid_lens[idx], self.all_pred_positions[idx],
                self.all_mlm_weights[idx], self.all_mlm_labels[idx],
                self.nsp_labels[idx])
    def __len__(self):
        return len(self.all_token_ids)
```
通过使用`_read_wiki`函数和`_WikiTextDataset`类，我们定义了下面的`load_data_wiki`来下载并生成WikiText-2数据集，并从中生成预训练样本。
```{.python .input}
#@tab pytorch
#@save
def load_data_wiki(batch_size, max_len):
    """加载WikiText-2数据集"""
    num_workers = d2l.get_dataloader_workers()
    data_dir = d2l.download_extract('wikitext-2', 'wikitext-2')
    paragraphs = _read_wiki(data_dir)
    train_set = _WikiTextDataset(paragraphs, max_len)
    train_iter = torch.utils.data.DataLoader(train_set, batch_size,
                                        shuffle=True, num_workers=num_workers)
    return train_iter, train_set.vocab
```
将批量大小设置为512，将BERT输入序列的最大长度设置为64，我们打印出小批量的BERT预训练样本的形状。注意，在每个BERT输入序列中，为遮蔽语言模型任务预测$10$（$64 \times 0.15$）个位置。
最后，我们来看一下词量。即使在过滤掉不频繁的词元之后，它仍然比PTB数据集的大两倍以上。
## 小结
* 与PTB数据集相比，WikiText-2数据集保留了原来的标点符号、大小写和数字，并且比PTB数据集大了两倍多。
* 我们可以任意访问从WikiText-2语料库中的一对句子生成的预训练（遮蔽语言模型和下一句预测）样本。
## 练习
1. 为简单起见，句号用作拆分句子的唯一分隔符。尝试其他的句子拆分技术，比如Spacy和NLTK。以NLTK为例，需要先安装NLTK：`pip install nltk`。在代码中先`import nltk`。然后下载Punkt语句词元分析器：`nltk.download('punkt')`。要拆分句子，比如`sentences = 'This is great ! Why not ?'`，调用`nltk.tokenize.sent_tokenize(sentences)`将返回两个句子字符串的列表：`['This is great !', 'Why not ?']`。
1. 如果我们不过滤出一些不常见的词元，词量会有多大？
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/5737)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/5738)
:end_tab:
:begin_tab:`paddle`
[Discussions](https://discuss.d2l.ai/t/11822)
:end_tab: