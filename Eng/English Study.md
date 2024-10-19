```html
format 
- [ ] <div title=""></div>
```

## April

### week1

revolutionize v.彻底改变

generation n.产生

**sentiment n.情绪**

fine-tuning 微调

interpretability n.可解释性 

computational adj.计算的

capabilities n.功能

prompt 提示词

comma n.逗号

analysis n.分析

backbone n.骨干

implement v.实现

**appositive** adj.同位的 n.同位语

trivial adj.琐碎的，不重要的

noteworthy adj.值得注意的，显著的

setup  n.安装，体制

make sense of 弄懂

**sensory adj.感觉的**

**Perceptron 感知机**

reliability n.可靠性，可信度

spatial adj.空间的

notation n.标记系统

tutorial n.教程 adj.教程的

toggle v. 转换

revert  v.回复，恢复

checkpoint n.检查点，权重保存点

cursor n.游标

palette n.选项板

docstring n.文档字符串（''' string ''')

handout n.讲义

therapeutics n.疗法，治疗药物

utilize v.利用

unprecedented adj.史无前例的

elucidate v.阐明，解释

Adversarial adj.对抗的，对手的

Generative adj.有生产力的

characteristic n.特色 adj.独特的

tweak v.微调

feed-forward adj.前馈的

**stack up 堆积**

**grunt work 苦力工作**

**get the hang of 掌握...的窍门**

### week2

acclaimed adj.收到表扬的,广受欢迎的

**groundbreaking adj.开创性的**

**narrative adj.叙述的**

recording button 记录按钮

**mind-bending adj.离奇古怪的**

**meticulous adj.一丝不苟的**

**synonyms n.同义词**

**Grabbing coffee 喝咖啡**

**versatile adj.用途广泛的**

**integer n.整数**

**Scalar n.标量**

### week4

**Deprecate vt.反对**

Vulnerability n.弱点

**Alias n.别名**

Truncate v.截断

**Descriptive 描述性的**

**Immersion 专心；沉浸**

Assign v.分派

Respective adj.相应的

**seamless adj.无缝的**

## May

### week2

**consent n./v.允许；同意**

snippets n.片段

verbose adj.冗长的

console n.控制台

### week3

parameter n.参数

> In this case, our model receives a snippet of audio as *input*, and the model generates a selection among {yes,no} as *output*. If all goes according to plan the model’s guesses will typically be correct as to whether the snippet contains the wake word.

snippet n.片段

> If we choose the right family of models, there should exist one setting of the knobs such that the model fires “yes” every time it hears the word “Alexa”

knob n.旋钮

> Because the exact choice of the wake word is arbitrary, we will probably need a model family sufficiently rich that, via another setting of the knobs, it could fire “yes” only upon hearing the word “Apricot”. 

arbitrary adj. 任意的

rich that 多元化

> if we want to deal with fundamentally different inputs or outputs, say if we wanted to map from images to captions, or from English sentences to Chinese sentences.

**caption n.字幕**

> In machine learning, the *learning* is the process by which we discover the right setting of the knobs for coercing the desired behavior from our model. 

**coerce v. 强制，迫使**

> Start off with a randomly initialized model that cannot do anything useful.

start off 以某种特定的方式开始

> Often refers to the process of taking a pre-trained model and making precise adjustments to tailor it for a specific task or dataset.

refer to 指代

**tailor 使...适应**

Key Components 关键组件

> we gave a hand-wavy sense of how we might train a model to approximate a mapping from snippets to classifications.

hand-wavy adj.含糊其辞的，不明确的

> This sort of problem, where we try to predict a designated unknown label based on known inputs given a dataset consisting of examples for which the labels are known, is called *supervised learning*. 

designated adj.指定的，标出的

> This is just one among many kinds of machine learning problems. Before we explore other varieties, we would like to shed more light on some core components that will follow us around, no matter what kind of machine learning problem we tackle.

shed some more light 透露更多的情况

> An *objective function* that quantifies how well (or badly) the model is doing

objective function 目标函数

> Each *example* (or *data point*, *data instance*, *sample*) typically consists of a set of attributes called *features* (sometimes called *covariates* or *inputs*), based on which the model must make its predictions. 

covariate n.协变量

>  a 200×200 pixel color photograph would consist of 200×200×3=120000 numerical values.

```
* = times
```

> "Dimension" typically refers to the minimum number of coordinates needed to specify any point within a space. For instance, a line has one dimension (length), a square has two dimensions (length and width), and a cube has three dimensions (length, width, and height).

**coodinates n.坐标**

> In such cases, when every example is characterized by the same number of numerical features, we say that the inputs are fixed-length vectors and we call the (constant) length of the vectors the *dimensionality* of the data.

be characterized by 以……为特征

fixed-length 固定长度

>we cannot expect images mined from the Internet all to have the same resolution or shape

mine v.挖掘

> We risk losing information in the cropped-out portions. 

cropped-out portions 裁出部分

> Consider the customer reviews left on e-commerce sites such as Amazon, IMDb, and TripAdvisor. Some are short: “it stinks!”. Others ramble for pages. One major advantage of deep learning over traditional methods is the comparative grace with which modern models can handle *varying-length* data.

left 后置定语 留下的

**ramble n.长篇大论**

> Finally, it is not enough to have lots of data and to process it cleverly. We need the *right* data. If the data is full of mistakes, or if the chosen features are not predictive of the target quantity of interest, learning is going to fail.

"Be predictive of" 和 "predict" 都有预见或预测的意思，但使用场合和语境稍有不同。 “Be predictive of” 是形容某种特征、指标或者现象能够表明或者预示另一种状态或者结果的可能性或者趋势。这个短语更注重的是描述一种关联性或者趋势，并不强调必然发生。例如，“他的学习成绩是他未来成功的预示”我们可以说"His grades are predictive of his future success"。 而 "predict" 更多的是用在可以根据某些观察或者数据去预测或者预告一个确切事件或者结果，它更侧重于确定性。例如，“我可以预测明天会下雨”我们可以说"I can predict it will rain tomorrow"。 在这里"the chosen features are not predictive of the target quantity of interest"，作者是想表示选定的特征并不能有效的表明或者预示目标变量的趋势或者变化，所以用了"be predictive of"。

> In sensitive applications of machine learning, like predictive policing, resume screening, and risk models used for lending, we must be especially alert to the consequences of garbage data. 

sensitive adj.敏感的

> For example, if past hiring decisions are used to train a predictive model that will be used to screen resumes then machine learning models could inadvertently capture and automate historical injustices. Note that this can all happen without the data scientist actively conspiring, or even being aware.

**advertent adj.留意的；注意的**

inadvertently 无意地c

> Note that this can all happen without the data scientist actively conspiring, or even being aware.

conspiring 参与

Note that 请注意

> Most machine learning involves transforming the data in some sense. We might want to build a system that ingests photos and predicts smiley-ness. Alternatively, we might want to ingest a set of sensor readings and predict how normal vs. anomalous the readings are. 

ingest v.吸收

sensor n.传感器

> While simple models are perfectly capable of addressing appropriately simple problems, the problems that we focus on in this book stretch the limits of classical methods.

stretch v.拓展

> By convention, we usually define objective functions so that lower is better.

By convention 按照惯例

> You can take any function for which higher is better, and turn it into a new function that is qualitatively identical but for which lower is better by flipping the sign. 

flip v.翻转

> When trying to predict numerical values, the most common loss function is *squared error*, i.e., the square of the difference between the prediction and the ground truth target.

ground truth target 真实值（预测目标）

> the most common objective is to minimize error rate, i.e., the fraction of examples on which our predictions disagree with the ground truth. 

fraction 比例

> Some objectives (e.g., squared error) are easy to optimize, while others (e.g., error rate) are difficult to optimize directly, owing to non-differentiability or other complications. 

**differentiate 求...微分**

non-differentiability 不可微

**derivative 导数**

> In these cases, it is common instead to optimize a *surrogate objective*.

**surrogate adj.替代的**

> We learn the best values of our model’s parameters by minimizing the loss incurred on a set consisting of some number of examples collected for training. However, doing well on the training data does not guarantee that we will do well on unseen data. So we will typically want to split the available data into two partitions

incur 遭受，产生

the loss incurred on a set 这组数据产生的损失

pratition 部分

>  You could think of training performance as analogous to the scores that a student achieves on the practice exams used to prepare for some real final exam. 

**analogous adj.类似的**

practice exam 模拟考试

> Over the course of studying, the student might begin to memorize the practice questions, appearing to master the topic but faltering when faced with previously unseen questions on the actual final exam.

**falter v.衰弱，退步**

> In brief, at each step, this method checks to see, for each parameter, how that training set loss would change if you perturbed that parameter by just a small amount.

**perturb 小幅度的调整或改变**

> supervised learning itself can take diverse forms and require tons of modeling decisions

modeling decision 建模决策

> If you live in New York or San Francisco, and you are not the CEO of Amazon, Google, Microsoft, or Facebook, the (sq. footage, no. of bedrooms, no. of bathrooms, walking distance) feature vector for your home might look something like: [600,1,1,60]. However, if you live in Pittsburgh, it might look more like [3000,4,3,10]. Fixed-length feature vectors like this are essential for most classic machine learning algorithms.

sq. square 房屋总面积

no. number

> Lots of practical problems are easily described as regression problems. Predicting the rating that a user will assign to a movie can be thought of as a regression problem 

assign 分配

> A good rule of thumb is that any *how much?* or *how many?* problem is likely to be regression. For example:
>
> - How many hours will this surgery take?
> - How much rainfall will this town have in the next six hours?

**A good rule of thumb 一个经验法则**

> Whereas in regression we sought a regressor to output a numerical value, in classification we seek a classifier, whose output is the predicted class assignment.

whereas 用于对比或者对照

seek 的过去式 sought

> For reasons that we will get into as the book gets more technical, it can be difficult to optimize a model that can only output a *firm* categorical assignment, e.g., either “cat” or “dog”. 

categorical assignment 分类任务

firm categorical assignment指一个确切的分类任务，比如100%是cat或者0%是dog

> The magnitude of the probability for the predicted class conveys a notion of uncertainty.

magnitude 大小

> When we have more than two possible classes, we call the problem *multiclass classification*. Common examples include handwritten character recognition {0, 1, 2, ... 9, a, b, c, ...}. While we attacked regression problems by trying to minimize the squared error loss function, the common loss function for classification problems is called *cross-entropy*, whose name will be demystified when we introduce information theory in later chapters.

multiclass classification 多分类任务

cross-entropy 交叉熵

> The problem of learning to predict classes that are not mutually exclusive is called *multi-label classification*. 

not mutually exclusive 不互斥

> Sometimes such tagging problems draw on enormous label sets.

**draw on 利用**

> The goal is less to determine *whether* a particular page is relevant for a query, but rather which, among a set of relevant results, should be shown most prominently to a particular user.

prominently 显著地

> The problems are similar insofar as the goal is to display a set of items relevant to the user. 

- [ ] <div title="在某种程度上，就某种程度而言">insofar as</div>

> For example, on a five-point scale, you might notice that items receive many one- and five-star ratings but that there are conspicuously few three-star ratings. 

**conspicuously 显著地**

> And our guess of what is going on in each frame might be much stronger if we take into account the previous or succeeding frames.

succeeding frame 下一帧

> With speech recognition, the input sequence is an audio recording of a speaker ([Fig. 1.3.5](https://d2l.ai/chapter_introduction/index.html#fig-speech)), and the output is a transcript of what the speaker said.

transcript 转录的结果

> The challenge is that there are many more audio frames (sound is typically sampled at 8kHz or 16kHz) than text, i.e., there is no 1:1 correspondence between audio and text, since thousands of samples may correspond to a single spoken word. 

**i.e. means that is**

> Unlike the case of speech recognition, where corresponding inputs and outputs occur in the same order, in machine translation, unaligned data poses a new challenge.

unaligned 不对齐的

> Consider the following illustrative example of the peculiar tendency of Germans to place the verbs at the end of sentences:

peculiar tendency 特殊倾向

>  For instance, determining the order in which a user reads a webpage is a two-dimensional layout analysis problem. 

**determining 确定**

> Dialogue problems exhibit all kinds of additional complications, where determining what to say next requires taking into account real-world knowledge and the prior state of the conversation across long temporal distances. Such topics are active areas of research.

dialogue 对话

exhibit 表现出

take into account 考虑到

prior state 之前的状态

> To whet your appetite for now, we describe a few of the following questions you might ask.

**whet sb appetite 激起食欲，提起兴趣**

> For images, we may train models to tell the relative position between two cropped regions of the same image ([Doersch *et al.*, 2015](https://d2l.ai/chapter_references/zreferences.html#id58)), to predict an occluded part of an image based on the remaining portions of the image, 

**occluded adj.隔离的，封闭的**

> In each case, we grab a big pile of data upfront, then set our pattern recognition machines in motion without ever interacting with the environment again. 

in motion 在运行中

> we must account for the way its actions might impact the future observations of the agent, and so offline learning is inappropriate.

account for 考虑到

> *Deep reinforcement learning*, which applies deep learning to reinforcement learning problems, has surged in popularity.

surge in popularity 人气飙升

> At each time step, the agent receives some *observation* from the environment and must choose an *action* that is subsequently transmitted back to the environment via some mechanism (sometimes called an *actuator*), 

is subsequently transmitted back to 随后传输回去

**subsequently  随后**

### week4

> If you are interested in using machine learning to develop an agent that interacts with an environment and takes actions, then you are probably going to wind up focusing on reinforcement learning. 

**wind up 最终处于，结束于**

> Reinforcement learning gives a very general statement of a problem in which an agent interacts with an environment over a series of time steps. 

在英语中，有许多介词可以用于表示时间关系。以下是一些常见的例子：

1. "At"：用于具体的时间点，如 "at 3 o'clock"（在三点钟）。
2. "On"：用于具体的日期或星期几，如 "on Monday"（在星期一）或 "on March 8th"（在三月八日）。
3. "In"：用于年份、月份、季节、世纪、一天中的某个时段等，如 "in 2020"（在2020年）、"in March"（在三月）、"in the morning"（在早晨)。
4. "By"：表示在某时间之前，如 "by 5 o'clock"（在五点之前）。
5. "Before"：表示在……之前，如 "before the meeting"（在会议之前）。
6. "After"：表示在……之后，如 "after lunch"（午餐后）。
7. "During"：表示在某个时间段内，如 "during the holiday"（在假期期间）。
8. "Until" / "Till"：表示直到某个时间，如 "until tomorrow"（直到明天）。
9. "Since"：表示从某个时间点开始直到现在，如 "since 1990"（自1990年以来）。
10. "For"：表示一段时间，如 "for three hours"（三小时）。



"Over"和"for"都可以用来表示一段时间，但它们的用法和含义有一些细微的差别。

1. "Over"：通常用来表示在一段时间内的动作或事件的完成或发生。例如，"I read the book over the weekend"（我在周末读完了这本书）。
2. "For"：用来表示动作或状态的持续时间。例如，"I have been reading for two hours"（我已经读了两个小时了）。

> The reinforcement learner must constantly choose whether to *exploit* the best (currently) known strategy as a policy, or to *explore* the space of strategies, potentially giving up some short-term reward in exchange for knowledge.

short-term 短期的

> Accounting for all this complexity at once may be asking too much.

account for 解释

> knowledge of the basic linear algebraic operations that we apply to high-dimensional data elements;

linear algebraic operation 线性代数运算

- [ ] <div title=" 预备知识">preliminaries</div>

> Zotero is, at the most basic level, a reference manager. It is designed to store, manage, and cite bibliographic references, such as books and articles

bibliographic adj. 书目的；书籍解题的

Attachments 附件

> It has been a longstanding research challenge to achieve this goal, to enable machines to read, write, and communicate like humans

longstanding adj.长期存在的

> LM aims to model the generative likelihood of word sequences, so as to predict the probabilities of future (or missing) tokens.

- [ ] <div title="目的是，意图是">
      so as to
  </div>

> Since the researchers have found that model scaling can lead to an improved model capacity, they further investigate the scaling effect by increasing the parameter scale to an even larger size.

scaling 增加、扩展或提升语言模型的规模或能力

> these large-sized PLMs display different behaviors from smaller PLMs (e.g., 330M-parameter BERT and 1.5Bparameter GPT-2) and show surprising abilities (called emergent abilities [31]) in solving a series of complex tasks.

涌现能力 

> BERT [23] was proposed by pre-training bidirectional language models with specially designed pre-training tasks on large-scale unlabeled corpora.

- [ ] <div title = "语料库">
      corpora
  </div>

> A remarkable application of LLMs is ChatGPT2 that adapts the LLMs from the GPT series for dialogue

adapt ... for 使...适应于

> Furthermore, pre-trained language models learned context-aware representations that can be optimized according to downstream tasks. For the latest generation of language model, LLMs are enhanced by exploring the scaling effect on model capacity, which can be considered as general-purpose task solvers. To summarize, in the evolution process, the task scope that can be solved by language models have been greatly extended, and the task performance attained by language models have been significantly enhanced.

"Context-aware"在这里指的是预训练的语言模型具有学习上下文关系的能力。这些模型可以理解和解释输入信息的上下文，再根据上下文来预测下一个词或者完成特定的任务。简单来说，它们能够理解词语之间的关系并使用这种理解来改善预测和任务完成的性能。

而"downstream tasks"则指的是在预训练模型基础上需要进一步完成的任务，也就是说，预训练的模型会提供一种学习到的通用性表达，然后这种表达可以被进一步优化，以便应对下游的特定任务，如文本分类、命名实体识别、情感分析等任务。通常来说，优化会涉及对模型参数的一些微调，以适应下游任务的特定需求。因此，预训练的模型只是完成下游任务的第一步。

> In the existing literature, PLMs have been widely discussed and surveyed [36–39], while LLMs are seldom reviewed in a systematic way. To motivate our survey, we first highlight three major differences between LLMs and PLMs.

motivate 提供理由,建立基础  通过强调这两者之间的区别，可以说明为什么需要对LLMs进行更系统的审查和研究。

>The training of LLMs requires extensive practical experiences in large-scale data processing and distributed parallel training. To develop capable LLMs, researchers have to solve complicated engineering issues, working with engineers or being engineers.

distributed parallel training 分布式并行训练

> Nowadays, LLMs are posing a significant impact on the AI community, and the advent of ChatGPT and GPT-4 leads to the rethinking of the possibilities of artificial general intelligence (AGI).

AGI 强AI，与人类匹配的认知能力

> Due to the huge demand of computation resources, it is very costly to carry out repetitive, ablating studies for investigating the effect of various strategies for training LLMs.

carry out 执行

repetitive 重复的

"ablating studies" 是一种研究方法，通常用于在科学和工程领域中，通过逐步移除或修改某些变量或组件，以研究它们对整体系统性能的影响。这种方法被称为"ablation study" 或 "ablative analysis"。

> We thoroughly comb the literature and summarize the key findings, techniques, and methods of LLMs.

- [ ] <div title = "梳理">
      comb
  </div>

> Extensive research has shown that scaling can largely improve the model capacity of LLMs [26, 55, 56]. Thus, it is useful to establish a quantitative approach to characterizing the scaling effect. Next, we introduce two representative scaling laws for Transformer language models [30, 34].

"Scaling law"（规模化法则 or 尺度定律）在这里指的是一种定量方法，用于描述和预测大型语言模型（如Transformer模型）性能随模型规模（如参数数量、训练数据的大小、计算资源等）增加而改变的规律

文章解释：[阿里云](https://developer.aliyun.com/article/1446631)

> Firstly, for large models, it is infeasible to rigorously examine various training tricks or variants, and it would be very helpful if experiences gained from small models could also apply to large models.

infeasible 不可行的

tricks 技巧

variant 变体

> Secondly, the training of large-scale models takes a long time, often suffering from issues such as training loss spike, and scaling law can be employed to monitor the training status of LLMs, e.g., identifying abnormal performance at an early time. Despite that scaling law characterizes a smooth trend of performance increase (or loss decrease), it also indicates that diminishing returns might occur as model scaling.

- [ ] <div title="训练损失突增">training loss spike</div>

characrerizes 描述

"Diminishing returns"是一个经济学术语，原意指的是在生产过程中，当一个生产要素（如资本、劳动力或原材料）的投入量增加时，其他条件保持不变，新增加的产出（回报）会逐渐减少。换句话说，每增加一单位的投入，所获得的额外产出会越来越少，直到最终可能为零或负值。 在这段话中，"diminishing returns"被用来形容在大型语言模型规模增加时可能遇到的情况。初始阶段，模型规模的增加可以带来显著的性能提升，但随着模型规模继续扩大，每一次增加所带来的性能提升会变得越来越小。这表明在达到一定规模后，继续增加模型大小的成本效益逐渐降低。

> An empirical study [58] from the OpenAI team has shown that representation quality or semantic content can still effectively improve even if approaching the point of diminishing returns (i.e., approaching the irreducible loss) [58]. This finding suggests that training large models are promising for improving the performance of downstream tasks. To further explore scaling effect, a potential issue is that the amount of available data for training LLMs is actually limited. With the ever-increasing model scale, the public text data would be soon “exhausted” for LLMs [60]. Thus, it will be meaningful to study how scaling laws apply to a data-constrained regime [61], where data repetition or augmentation might be useful to alleviate data scarcity.

representation quality 表示质量

- [ ] <div title = "语义内容">
      semantic content
  </div>

be promising for ...有希望的

data-constrained regime 数据受限的情况

regime 特定的情况、状态

data augmentation 数据增强

alleviate data scarity 减轻数据稀缺

## June

### week1

> 随机梯度下降（SGD）的全称是 Stochastic Gradient Descent。这是一种优化算法，用于调整深度学习和其他机器学习模型的参数，以最小化损失函数。"Stochastic" 一词指的是算法在每一步更新中使用随机抽样的子集来计算梯度。

Stochastic 随机的

### week2

> Our fastest and most affordable flagship model

affordable 便宜的

flagship 旗舰产品

> Enter an instruction or select a preset, and watch the API respond with a message that attempts to match or answer the query.

preset 预设

> Controls diversity via nucleus sampling: 0.5 means half of all likelihood-weighted options are considered.

nucleus sampling 核采样

top_p  

> 在大模型中，尤其是用于自然语言处理的生成模型中，如GPT-3，"top_p"（也称为核采样，nucleus sampling）是用于生成文本时的一种采样策略。
>
> ### Top-p (Nucleus Sampling) 详解
>
> 在文本生成过程中，模型会根据词汇表中每个可能的下一个词的概率分布生成下一个词。这些概率是通过软最大化函数计算得出的。传统的贪心搜索或top-k采样可能会导致生成的文本质量不高，因为它们要么太确定，要么太随机。Top-p 采样则是一种折衷方法，能够平衡生成质量和多样性。
>
> ### 如何工作
>
> 1. **排序**：
>    首先，根据模型预测的概率对所有可能的词进行排序，从高到低。
>
> 2. **累计概率**：
>    然后，依次累加这些排序后的概率，直到累计概率达到或超过阈值 \( p \)。
>
> 3. **选择词汇**：
>    最后，从这些累计概率满足条件的词中进行采样。
>
> 这样做的好处是，它能动态地选择最可能的一些词，而不是限制在固定数量的词（如top-k采样），这使得生成的文本既有质量又有多样性。
>
> ### 数学描述
>
> 设词汇表中的所有词的概率分布为 \( P(w) \)，我们按从高到低对这些概率进行排序，得到一个排序后的词汇表 \( \{w_1, w_2, \ldots, w_V\} \)，其中 \( P(w_1) \geq P(w_2) \geq \ldots \geq P(w_V) \)。我们选择前 \( k \) 个词，使得：
>
> $$
> \sum_{i=1}^{k} P(w_i) \geq p
> $$
>
> 然后在这些词中进行采样。
>
> ### 例子
>
> 假设有一个非常小的词汇表包含五个词：A、B、C、D、E。模型对下一个词的预测概率如下：
>
> - P(A) = 0.4
> - P(B) = 0.3
> - P(C) = 0.2
> - P(D) = 0.07
> - P(E) = 0.03
>
> 如果我们设定 \( p = 0.7 \)：
>
> 1. 排序后的概率：A (0.4), B (0.3), C (0.2), D (0.07), E (0.03)。
> 2. 从高到低累积概率：0.4 (A), 0.4 + 0.3 = 0.7 (A + B)。
>
> 此时累计概率已经达到 0.7，因此我们从 A 和 B 中采样下一个词。
>
> ### 优点
>
> - **灵活性**：相比于top-k采样，top-p采样更为灵活，因为它根据概率分布的实际情况来动态调整候选词的数量。
> - **多样性**：它能生成更有创意和多样性的文本，因为它不局限于固定数量的高概率词。
>
> 在已经选取的A和B中，具体选择哪一个词汇是通过概率采样来决定的。这个过程可以理解为在这两个词之间进行一次概率性选择，而不是均匀随机选择。
>
> 假设已经选取了A和B两个词，它们的概率分别是：
>
> - P(A) = 0.4
> - P(B) = 0.3
>
> 总概率和为0.7（因为我们之前设定的top-p阈值为0.7）。为了在这两个词中进行采样，我们需要对这两个词的概率进行重新归一化，使得它们的概率总和为1。
>
> ### 重新归一化概率
>
> 归一化后的概率分别是：
>
> $$
> P'(A) = \frac{P(A)}{P(A) + P(B)} = \frac{0.4}{0.4 + 0.3} = \frac{0.4}{0.7} = \frac{4}{7}
> $$
>
> $$
> P'(B) = \frac{P(B)}{P(A) + P(B)} = \frac{0.3}{0.4 + 0.3} = \frac{0.3}{0.7} = \frac{3}{7}
> $$
>
> ### 采样过程
>
> 在重新归一化后，A和B的概率变成了4/7和3/7。我们可以将这个过程看作是在[0, 1]区间上进行一次随机选择，具体步骤如下：
>
> 1. 生成一个在[0, 1]区间上的随机数 \( r \)。
> 2. 如果 \( r \) 落在[0, 4/7]区间，则选择词A。
> 3. 如果 \( r \) 落在(4/7, 1]区间，则选择词B。
>
> ### 例子
>
> 假设生成的随机数 \( r = 0.5 \)：
>
> - 因为 \( 0.5 \) 落在[0, 4/7]区间内，所以选择词A。
>
> 如果生成的随机数 \( r = 0.6 \)：
>
> - 因为 \( 0.6 \) 落在(4/7, 1]区间内，所以选择词B。
>
> ### 总结
>
> 在已经选取的候选词（如A和B）中，具体选择哪一个词汇是通过重新归一化概率后进行的随机采样决定的。这样既保持了生成文本的多样性，又确保了较高概率的词汇更有可能被选中，从而保证生成的文本质量。

> The OpenAI API uses API keys for authentication. You can create API keys at a user or service account level. Service accounts are tied to a "bot" individual and should be used to provision access for production systems. Each API key can be scoped to one of the following,

be scoped to 被限定在...范围内

> Transcribes audio into the input language.

"Transcript" 和 "Transcribe" 是两个相关但不同的术语，通常用于与文本和音频处理相关的领域。

- Transcript

"Transcript" 是一个名词，指的是已经完成的文字记录或文本副本。它通常是对某段对话、演讲、视频或音频内容的逐字记录。换句话说，"transcript" 是最终的产物，是一份完整的文本文件或记录。

**例子**：

- 会议记录：会议结束后，秘书会提供一份会议记录（transcript），详细记录会议中的每一句话。
- 采访记录：记者采访完某人后，可能会将采访内容转录成文本记录（transcript）。
- 学术讲座记录：学生可以参考讲座的文字记录（transcript）来复习内容。

- Transcribe

"Transcribe" 是一个动词，指的是将语音、视频或其他音频内容转录成文本的过程。这个过程可以是手动完成的（由人类逐字记录），也可以是自动完成的（由语音识别软件进行转录）。

**例子**：

- 手动转录：一个人听录音并将其内容逐字记录下来，这个过程就是"transcribe"。
- 自动转录：使用语音识别软件将音频文件转录成文本，这个过程也是"transcribe"。

**例句**：

- "I need to transcribe the interview by tomorrow."（我需要在明天之前把采访内容转录出来。）
- "The software can automatically transcribe audio files into text."（这个软件可以自动将音频文件转录成文本。）

总结

- **Transcript**：指的是已经完成的文字记录或文本文件，是名词。
- **Transcribe**：指的是将音频或视频内容转录成文本的过程，是动词。

简单来说，**"transcribe"** 是一个动作，表示转录的过程；而 **"transcript"** 是这个动作的结果，即转录后的文本记录。

> gpt assistnat training pipeline

pipeline 流水线；步骤

![image-20240611164858159](https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/image-20240611164858159.png)

ensemble 融合；集成

self-consistency 自洽性

> Ask GPT:Did you meet the assignment?

meet the assig完成任务

> **PromptSource is a toolkit for creating, sharing and using natural language prompts.**

toolkit 工具包

> A common denominator in these works is the use of prompts which has gained interest among NLP researchers and engineers. This emphasizes the need for new tools to create, share and use natural language prompts.

common denominator 共同点

### week3

> What readers fear the most while reading a scientific paper is to get stuck or left behind. They are stuck when the experienced writer zigzags around the familiar obstacles in the knowledge field, whilst readers crash into them; and they are left behind when the knowledgeable writer runs where they can only walk.
>
> 读者在阅读科学论文时最害怕的是陷入困境或被抛在后面。当经验丰富的作者在知识领域中绕过熟悉的障碍时，读者却撞上了它们；当知识渊博的作者在他们只能步行的地方奔跑时，读者就被抛在了后面。

ziazag 绕过

> Good writing should therefore take into account the reader’s ignorance, fatigue, short-term memory, and impatience in order to minimise their impact.

ignorance 无知，未知

fatigue 疲劳

> Unique writing techniques rarely presented in books on technical writing will bring the writer closer to the six qualities that are the hallmark of great scientific writing: fluid, organised, clear, concise, convincing, and interesting (FOCI).

hallmark 特点

fluid 流畅的

>  This book comes with a metaphorical box of chocolates: 48 stories designed to liven up reading and reinforce the learning process. It also comes with a core of 100 examples inspired or quoted from scientific articles.

metaphorical 比喻的

> In their assessment of the course, the participants highlighted benefits; some expected, some unexpected.

assessment 评估

highlighted 强调

> Junior scientists without any publishing experience were relieved that they no longer had to blindly imitate the work of others, not knowing whether what they were imitating was good or bad. Unexpectedly, even senior scientists with great publishing experience found that the seminar had improved their analytical reading skills and had equipped them with a method to conduct better peer reviews.

在职称和级别上，**senior scientist**（高级科学家）的级别比**junior scientist**（初级科学家）更高。

解释：

- **Junior Scientist**（初级科学家）：通常指刚开始其科研职业生涯的科学家，可能是刚获得博士学位或在科研领域工作经验较少的人。
- **Senior Scientist**（高级科学家）：通常指在科研领域有丰富经验和成就的科学家，通常拥有较长的工作经历，可能负责领导科研项目或团队。

> Before turning the page, words of appreciation are due.

在翻页之前，应该表达感谢之情。

> The Tense of Verbs in an Abstract

tense of verbs 动词的时态

> Sustain Attention to Ensure Continuous Reading

sustain attention 保持注意力

> This title probably conjures up the image of a schoolboy’s pencilcase containing a few chosen articles designed to help reading: a pair of glasses, a bookmark, instant coffee, etc. However, this toolkit is quite special. It contains resources invisible to the naked eye, like time, memory, energy, attention, and motivation. A skillful writer minimises the time, memory, and energy needed for reading, while keeping reader attention and motivation high.

- [ ] <div title="使人联想到，想象出">
      conjure up
  </div>

pencilcase 铅笔盒

- [ ] <div title = "速溶咖啡">instant coffee</div>

naked eye 肉眼

> require less from memory

减少对记忆的需求

> The Forgotten Acronym

- [ ] <div title = " 首字母缩略词">acronym</div>

> The Diverting Synonym

synonym 同义词

diverting 转移注意力的

> Make Important Things Stand Out

stand out 突出，显眼

> Illustrate to Clarify

illustrate 插图

> Notice the just-in-time definition of the acronym in the following example.

just in time 即时的

> Scientific readers favour visuals — fast food for the brain, “information burgers” that reduce reading time and increase the informative value of an article.

visuals 图形

> To set an expectation is like creating a void that other sentences will fill. Not filling that void is tantamount to frustrating readers by not bringing closure.

- [ ] <div title = "等同于">be tantamount to</div>

- [ ] <div title="结论">closure</div>

> Readers expect the author to bring evidence to justify scientific claims.

elaborate 详细说明，阐述

> from hypothesis to observations, and from results to analysis and interpretation.

从假设到观察，从结果到分析和解释

> The art of construction is acquired through a long apprenticeship

apprenticeship 学徒期

apprentice 学徒

> Each stage of the construction of a house contributes to its overall quality. Similarly, each part of an article contributes to the quality of the whole, from the abstract (the architectural blueprint) and the structure (the foundations) to the introduction (the flight of steps and the landing in front of your main door), the visuals (the light-providing windows), and finally the conclusion (the handing out of the key to knowledge). The art of construction is acquired through a long apprenticeship. You may be attracted by the time-saving expedient prefab (even its name indicates that it is a shortcut), or by the imitation of other constructions of uncertain architectural quality. Beware of shortcuts. A thorough analysis of the different parts of a hastily assembled paper often reveals major cracks and faults: the shapeless structure is like a pair of baggy jeans that fit just about any frame, while the graphics and other visuals have a mouse- and mass-produced look and feel.
>
> 建造房子的每个阶段都会对其整体质量产生影响。同样，文章的每个部分也会影响整体质量，从摘要（建筑蓝图）和结构（地基）到引言（通向主门的台阶和门前的着陆区）、视觉效果（提供光线的窗户）以及最后的结论（知识的钥匙）。建造的艺术是通过长期的学徒期获得的。你可能会被节省时间的预制件所吸引（甚至它的名字都表明它是一条捷径），或者被其他不确定建筑质量的仿制品所吸引。要小心捷径。对匆忙拼凑的论文的不同部分进行深入分析，往往会揭示出重大缺陷和错误：无形的结构就像一条适合任何体型的宽松牛仔裤，而图形和其他视觉效果则有一种鼠标点击和批量生产的感觉。要构建一套令人满意的部分，必须理解每个部分对读者和作者的作用；要评估它们的质量，必须建立评估标准。接下来的章节将实现这些目标，并提供大量示例进行分析，帮助区分好文章和坏文章。

Handing out - 发放

time saving expedient prefab 节省时间的预制件

expedient 方便的

prefab 预制件

Hastily - 匆忙地

Imitation - 仿制品

> Today, as the city’s bowels demonstrate their usual constipation, the pouring rain adds a somewhat slimy aspect to the slow procession of traffic. Professor Leontief does not like arriving late at the lab. He hangs his dripping umbrella over the edge of his desk, at its designated spot above the trashcan, and he gently awakens his sleepy computer with some soothing words: “Come on, you hunk of metal and silicon oxide, wake up.”

bowel 肠道

Constipation - 便秘（这里比喻交通拥堵）

> being a resourceful man, he makes a couple of telephone calls and reorganises his work schedule so as to free up an immediately available 2-hour slot.

- [ ] <div title = "足智多谋的">resourceful</div>

so as to 为了

free up 腾出（时间）

> The difference between making ripples or making waves will then be a matter of scientific excellence — a topic I leave in your good and capable hands

- [ ] <div title = "取决于">be a mattle of</div> 

制造涟漪和掀起波浪之间的区别将取决于科学卓越性

> What makes your face unique is the way its features are assembled harmoniously.

assemble 组合，装配

harmoniously  和谐地

> Scientist: By all means, go ahead!

by all means 当然

> You are perfectly entitled to logically infer that from the title.

logically infer 逻辑推断

> Silicon-on-insulator

insulator 绝缘体

> Besides and and or, other prepositions can also be quite ambiguous in titles. For example, the preposition with could mean together with as in “coffee with milk”, or it could mean using as in “to move the ground with a shovel”.

preposition 介词

> 读文献是有技巧和优先级的，不要一脑袋就扎进去瞎读。具体优先级如下：1）近一到两年你大致研究方向的[文献综述](https://www.zhihu.com/search?q=文献综述&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A1945330900})。这种综述一般会帮你把各种流派以及最先进的方法整理出来，读完后你会有一个大概的big picture 2）近五年内该方向的经典著作（高引用，具有启发性的）。这类文章一般也有很多博客讲解，原文读不懂可以看别人的博客。3）带开源代码，近两年的顶会sota. 4)无开源代码，近两年的顶会sota.

sota:state of the art 

当前最优水平或最先进的模型、算法或技术

> The time has come for our last title. It is somewhat tricky.

tricky 棘手

> The heart plays an essential role in the human body. Similarly, the essence of an article is its abstract. It goes to the core.

essence 精华

> The skeleton gives a frame to the body. With it, the reinforced body takes shape;

reinforced 强化的，增强的

> The most detailed part of a structure contains the largest amount of contributive details.

the largest amount of 最多的

contributive 有用的

> Three Principles for a Good Structure A structure that plays its role follows these principles: 1. The contribution guides its shape. 2. Title words are repeated in its headings and subheadings. 3. It tells a story clearly and completely in its broad lines.

Broad lines - 大纲

> Studying the structure of your paper will allow you to identify important problems. Your paper may be too complex, too detailed, too premature, or too shallow.

premature 草率的，不成熟的

> Nonlinear finite element simulation to elucidate the efficacy

elucidate 阐述，解释

> A structure should be the most detailed where the author has the most to write about, namely the scientific contribution of the paper.

the most 定量词组，表示数量最多的东西（最多内容要写的部分）

namely 也就是说

> The structure expands to accommodate the level ofdetails required to fullydevelop the contribution

accommodate 适应

> The contribution is often found under the heading that has the deepest level of indentation and the largest number of subheadings.

indentation 缩进

> This first principle has a corollary: when excessively detailed parts do not contain much contribution, the structure has a problem.

corollary 推论，结论

> Syntactic Rules for Headings

syntactic 句法的，语法的

> It contains data and grad, which storage the value of node and gradient w.r.t loss respectively.
>
> 它包含数据和梯度，分别存储节点的值和相对于损失（loss）的梯度

w.r.t **with respect to（w.r.t）**：表示某个量或变量相对于另一个量或变量的关系。例如，在微积分中，当我们说“导数 w.r.t x”时，我们指的是函数相对于变量 x 的导数。

> Applies a linear transformation to the incoming data:
>
> *y*=*x**A**T*+*b*
>
> - **bias** ([*bool*](https://docs.python.org/3/library/functions.html#bool)) – If set to `False`, the layer will not learn an additive bias. Default: `True`

bias 就是线性回归中的b

> The torch package contains data structures for multi-dimensional tensors and defines mathematical operations over these tensors. Additionally, it provides many utilities for efficient serialization of Tensors and arbitrary types, and other useful utilities.

张量（Tensors）的序列化（serialization）是指将张量的数据结构转换为一种可以保存到文件或传输到其他系统的格式。序列化的目的是将张量的状态（包括数据和元数据）保存下来，以便在以后可以恢复或在不同的环境中重新使用。

### week4

> Define the computation performed at every call.
>
> Should be overridden by all subclasses.

被子类重写

overridden 重写

> Although the recipe for forward pass needs to be defined within this function, one should call the Module instance afterwards instead of this since the former takes care of running the registered hooks while the latter silently ignores them.

recipe 步骤

> Terminology: Epoch,Batch-Size,Iteration

terminology 术语,专业用语

> PyTorch Recipes Recipes are bite-sized, actionable examples of how to use specific PyTorch features, different from our full-length tutorials.

bite-sized 小巧的，简单易懂的

## July

### week1

> PyTorch allows a maketensor to be a View of an existing tensor. View tensor shares the same underlying data with its base tensor. Supporting View avoids explicit data copy, thus allows us to do fast and memory efficient reshaping, slicing and element-wise operations.

underlying data 底层数据

explicit data copy 显示的数据复制

element-wise operation 元素级操作

### week2

> hallucination

（大模型）幻觉

> The exact value and typeof symbols are mostlyimmaterial to the modelperformance.Replacingsymbols with abstractplaceholders can do justas well at eliciting elieffective thoughts.

immaterial 不重要的

placeholder 占位符

eliciting 刺激

> symbiotic relationship between text and patterns

- [ ] <div title = '共生的'>
      symbiotic
  </div>

### Week3

> Decks that have been nested under another deck (that is, that have at least one “::” in their names) are often called 'subdecks', and top-level decks are sometimes called 'superdecks' or 'parent decks'.

- [ ] <div title = '被嵌入'>have been nested</div> 

> We propose a new simple network architecture, the Transformer, based solely on attention mechanisms, dispensing with recurrence and convolutions entirely.

- [ ] <div title = '放弃，不再使用'> dispensing with </div>

- [ ] <div title = '已出版的文献'>literature</div>

- [ ] <div title = '英语成分句法分析'>English constituency parsing</div>

> Recurrent neural networks, long short-term memory [13] and gated recurrent [7] neural networks in particular, have been firmly established as state of the art approaches in sequence modeling and transduction problems such as language modeling and machine translation [35, 2, 5]. Numerous efforts have since continued to push the boundaries of recurrent language models and encoder-decoder architectures
> since的用法？

在这个句子中，"since" 用作从属连词，引导一个时间状语从句，表示“自从……以来”。它用来指明从过去某个时间点或事件之后一直持续到现在的时间跨度。这里的用法强调从某个特定的时间点开始，相关的行为或状态一直持续不断。

句子中的 "since" 用法如下：
> "Numerous efforts have since continued to push the boundaries of recurrent language models and encoder-decoder architectures."

这句话的意思是自从循环神经网络（RNNs），特别是长短期记忆网络（LSTM）和门控循环神经网络（GRUs）被确立为序列建模和转换问题（如语言建模和机器翻译）的最先进方法以来，许多努力一直在不断地推动循环语言模型和编码器-解码器架构的边界。

这里的 "since" 指的可能是这些网络结构被广泛认可和使用的那个时间点，从那时起，研究者们就一直在进行各种尝试和研究，以进一步提升这些模型的性能和应用范围。

### Week4

> The choice of candidate is influenced by the reader’s knowledge: the more superficial the knowledge, the more error-prone the choice will be. Authors who wish nonexperts to read their paper should be aware that pronouns present dangers.

- [ ] <div title = '易出错的'>error-prone</div>

> The usual culprits were absent: the grammar was correct and the sentence length was average for a scientific article.

- [ ] <div title = '起因'>culprit</div>

> Local variables are known only within the subroutine where they are declared.

- [ ] <div title = '子程序'>subroutine</div>

> Additional information is readily available from “context” other words found in the vicinity of the word considered.

- [ ] <div title = '周边区域'>vicinity</div>

> The nesting of subordinates has the same effect as plunging the reader below the comprehension level.

- [ ] <div title = '嵌套'>nest</div>

- [ ] <div title = '嵌套'>subordinate</div>

> In summary, acronyms, pronouns, abusive detailing, background “ghettos”, cryptic captions, and separated phrases all take their toll on the reader’s memory.

- [ ] <div title="滥用的">abusive</div>

- [ ] <div title = '模糊的'>cryptic</div>

> Drama and suspense naturally seem out of reach for the scientific writer.

- [ ] <div title = '悬念，兴奋'>suspense</div>

> To reduce excessive paragraph length, follow these three steps: keep the main supportive details that contribute the most to your argument, and trim the rest; join and consolidate related details that are scattered; and restructure the paragraph to remove repetition and inconsistent keywords.

- [ ] <div title="调整">trim</div>

- [ ] <div title="展开">scatter</div>

> Sometimes, additional length is caused by lack of focus. The paragraph accumulates points and issues that are interwoven and difficult to disentangle without a complete restructure of the long paragraph

有时候，额外的长度是由于缺乏焦点造成的。段落累积了许多点和问题，它们相互交织，难以在不对长段落进行完全重构的情况下解开。

> Used in moderation, a numbered list, a box around text, bold,underlined,or italic text, a change in font, etc. are equivalent to raising the volume of your voice, or changing its pitch or inflexion.

- [ ] <div title = '适度'>moderation</div>

> They break the monotony of paragraphs and make things stand out (note that the publisher may limit your choices by imposing a standard format).

- [ ] <div title = '单调乏味'>monotony</div>

> This inherently sequential nature precludes parallelization within training examples, which becomes critical at longer sequence lengths, as memory constraints limit batching across examples.

- [ ] <div title = '排除'>preclude</div>

> In all but a few cases [27], however, such attention mechanisms are used in conjunction with a recurrent network.

- [ ] <div title = '被用来与...一起使用'>be usesd in conjuction with</div>

> The goal of reducing sequential computation also forms the foundation of the Extended Neural GPU [16], ByteNet [18] and ConvS2S [9], all of which use convolutional neural networks as basic building block, computing hidden representations in parallel for all input and output positions. In these models, the number of operations required to relate signals from two arbitrary input or output positions grows in the distance between positions, linearly for ConvS2S and logarithmically for ByteNet. This makes it more difficult to learn dependencies between distant positions [12]. In the Transformer this is reduced to a constant number of operations, albeit at the cost of reduced effective	 resolution due to averaging attention-weighted positions, an effect we counteract with Multi-Head Attention as described in section 3.2.

- [ ] <div title = '线性'>linearly</div>

- [ ] <div title="指数">logarithmically</div>

- [ ] <div title="尽管">albeit</div>

- [ ] <div title="抵消">counteract</div>

> We plan to extend the Transformer to problems involving input and output modalities other than text and to investigate local, restricted attention mechanisms to efficiently handle large inputs and outputs such as images, audio and video.

- [ ] <div title="形态">modality</div>

## August

### Week2

> In this work we propose the Transformer, a model architecture eschewing recurrence and instead relying entirely on an attention mechanism to draw global dependencies between input and output.

- [ ] <div title="避开">eschew</div>

> At each step the model is auto-regressive [10], consuming the previously generated symbols as additional input when generating the next.

- [ ] <div title="自回归">auto-regressive</div>

$ y_t $ 的输出与之前时刻$y_1 ... y_{t-1} $相关 

> The summary, another repetition, clarifies what is important by rephrasing the section’s main points succinctly and differently.

- [ ] <div title = 'succintly'>简洁地</div>

> Words such as to summarise, in summary, in other words, see Fig. X, in conclusion, in short, and briefly put all perk up the attention of readers.

- [ ] <div title="引起注意力">perk up attention</div>

> Words conveying importance guide attention. They act like pointing fingers and are quite effective, if used sparingly.

- [ ] <div title="简朴的">sparingly</div>

> Without visuals, a paper soon becomes unclear; without clear understanding, readers’ attention soon wanes.

- [ ] <div title="减弱，衰退">wane</div>

> One might think that all questions come with a question mark.

- [ ] <div title="问号">question mark</div>

> A noteworthy contradiction, difference, exception, limitation: however, but, contrary to, although, in contrast, on the other hand, while, whereas, whilst, only.

- [ ] <div title="矛盾">contradiction</div>

> In conclusion, you can control how the reader perceives time by (1) managing the length of the sections of your paper

- [ ] <div title="感知">perceive</div>

> You order the paper through your library. A day later, it lands on your desk with a yellow post-it note attached to the first page that says, “A French girlfriend, maybe?”

- [ ] <div title="便利贴">post-it</div>

> If you ask the librarian, she will ask you about your French girlfriend, so you scrap that idea.

- [ ] <div title="放弃想法">scrap the idea</div>

> Deviating from the norm is often frowned upon (like ending sentences with a preposition).

- [ ] <div title="偏离，违背">deviate from</div>

> You can now see that your writing has much to do with sustaining the motivation of the reader through a combination of writing style, honest title, judicious detail and background, clear contribution, and good English.

- [ ] <div title="明智的">judicious</div>

> The following scenarios will help you understand their goals.

- [ ] <div title="情节">scenarios</div>

> The serendipitous reader

- [ ] <div title="偶然发现的">serendipitous</div>

> Now that we have ascertained what you know for sure about your readers’ initial knowledge, what then do you not know for sure?

- [ ] <div title="查明">ascertain</div>

> Even though it is tempting to believe that readers have the same level of knowledge as the one you had at the start of your project, nothing could be further from the truth. Readers are not younger versions of you. Let us now consider your contribution.

- [ ] <div title="诱人的">tempting</div>

> I hope you now see that, by and large, the gap between your knowledge and readers’ knowledge is wide

- [ ] <div title="大体上">by and large</div>

> therefore, you must clearly demark your contribution from that of others.

- [ ] <div title="区别">demark</div>

> We suspect that for large values of dk, the dot products grow large in magnitude, pushing the softmax function into regions where it has extremely small gradients 4. To counteract this effect, we scale the dot products by 1 √dk .

- [ ] <div title="（按比例）缩小">scale</div>

> The Transformer follows this overall architecture using stacked self-attention and point-wise, fully connected layers for both the encoder and decoder, shown in the left and right halves of Figure 1, respectively.

- [ ] <div title="两等分">halves</div>

### Week3

> In this work, we investigate white-box KD of LLMs where the output distribution of the teacher model is available. We argue that the standard KD objectives (Kim & Rush, 2016; Song et al., 2020; Chiang et al., 2023; Taori et al., 2023) are sub-optimal for LLMs that perform tasks in a generative manner.

- [ ] <div title="次优的">subtimal</div>

> How do you keep them? Are some of their contents highlighted to mark a significant problem or discovery? Every discovery is a conceptual leap.

- [ ] <div title="概念飞跃">conceptual leap</div>

> You have to throw a figurative ladder to readers, so that they can come on board your hot air balloon gondola.

- [ ] <div title="比喻的">figuratibe</div>

> Not filling that void is tantamount to frustrating readers by not bringing closure.

- [ ] <div title="等同">be tantamount to</div>

- [ ] <div title="结论">closure</div>

> Controlling these expectations, limiting their range, or channelling them is not optional: it is key to the success of your paper. Therefore, manage the expectations you set.

- [ ] <div title="引导">channelling</div>

> It is time to revive grammatical concepts acquired in secondary school. One recognises a main clause because it stands alone. A subordinate clause does not stand alone: to be understood, it needs the main clause. The following sentence has two clauses (each with subject and verb).

- [ ] <div title="中学">secondary school</div>

- [ ] <div title="主句">main clause</div>

- [ ] <div title="从句">subordiante clause</div>

> In (4), the two influential factors are on opposite sides of the sentence (main clause at the head of the sentence and subordinate at the end of the sentence), so they neutralise one another.

- [ ] <div title="中和">neutralise</div>

## September

### Week 4

> - being highly customizable for bespoke document production due to its intrinsic programmability and extensibility through thousands of [free add-on packages](https://www.ctan.org/pkg).

* [ ]  <div title = 'adj.定做的，定制的v.显示，展现；表明……的存在，证明；预订（bespeak 的过去式） '>bespoke</div>

   
