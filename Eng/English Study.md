## April

### week1

revolutionize 彻底改变

generation 产生

sentiment 情绪

fine-tuning 微调

interpretability 可解释性 

computational adj.计算的

capabilities 功能

prompt 提示词

comma 逗号

analysis 分析

backbone 骨干

implement v.实现

appositive

trivial

noteworthy

setup

make sense of 

sensory

Perceptron

reliability

knock

spatial

notation

tutorial

toggle

revert

checkpoint

bind

cursor

palette

docstring

handout

cellular

therapeutics

utilize

unprecedented

elucidate

stretches

Adversarial

Generative

characteristic

tweak

pattern

manipulate

feed-forward

stack up

sandwiched

grunt work

overfitting

spit out

get the hang of

pivotal

delve

propagate

hyperparameter

tandem

criterion

registry

template

pixels

 

### week2

Extravaganza

acclaimed

groundbreaking

widespread

narrative

solidified

recording button 记录按钮

queries

eliminate

auditory 

mind-bending 离奇古怪的

meticulous

innovative

synonyms

Grabbing coffee 喝咖啡

versatile

integer 

Scalar

### week4

Deprecate

Vulnerability

Alias

Truncate

Plugin

Descriptive

Orchestration

Immersion

Collapse files tree

Assign

Respective 相应的

seamless

## May

### week2

consent

gist

snippets

verbose

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

caption n.字幕

> In machine learning, the *learning* is the process by which we discover the right setting of the knobs for coercing the desired behavior from our model. 

coerce v. 强制，迫使

> Start off with a randomly initialized model that cannot do anything useful.

start off 以某种特定的方式开始

> Often refers to the process of taking a pre-trained model and making precise adjustments to tailor it for a specific task or dataset.

refer to 指代

tailor 使...适应

Key Components 关键组件

> we gave a hand-wavy sense of how we might train a model to approximate a mapping from snippets to classifications.

hand-wavy adj.含糊其辞的，不明确的

> This sort of problem, where we try to predict a designated unknown label based on known inputs given a dataset consisting of examples for which the labels are known, is called *supervised learning*. 

designated adj.指定的，标出的

> This is just one among many kinds of machine learning problems. Before we explore other varieties, we would like to shed more light on some core components that will follow us around, no matter what kind of machine learning problem we tackle.

shed some more light 洒下更多的光

> An *objective function* that quantifies how well (or badly) the model is doing

objective function 目标函数

> Each *example* (or *data point*, *data instance*, *sample*) typically consists of a set of attributes called *features* (sometimes called *covariates* or *inputs*), based on which the model must make its predictions. 

covariate n.协变量

>  a 200×200 pixel color photograph would consist of 200×200×3=120000 numerical values.

```
* = times
```

> "Dimension" typically refers to the minimum number of coordinates needed to specify any point within a space. For instance, a line has one dimension (length), a square has two dimensions (length and width), and a cube has three dimensions (length, width, and height).

coodinates n.坐标

> In such cases, when every example is characterized by the same number of numerical features, we say that the inputs are fixed-length vectors and we call the (constant) length of the vectors the *dimensionality* of the data.

be characterized by 以……为特征

fixed-length 固定长度

>we cannot expect images mined from the Internet all to have the same resolution or shape

mine v.挖掘

> We risk losing information in the cropped-out portions. 

cropped-out portions 裁出部分

> Consider the customer reviews left on e-commerce sites such as Amazon, IMDb, and TripAdvisor. Some are short: “it stinks!”. Others ramble for pages. One major advantage of deep learning over traditional methods is the comparative grace with which modern models can handle *varying-length* data.

left 后置定语 留下的

ramble n.长篇大论

> Finally, it is not enough to have lots of data and to process it cleverly. We need the *right* data. If the data is full of mistakes, or if the chosen features are not predictive of the target quantity of interest, learning is going to fail.

"Be predictive of" 和 "predict" 都有预见或预测的意思，但使用场合和语境稍有不同。 “Be predictive of” 是形容某种特征、指标或者现象能够表明或者预示另一种状态或者结果的可能性或者趋势。这个短语更注重的是描述一种关联性或者趋势，并不强调必然发生。例如，“他的学习成绩是他未来成功的预示”我们可以说"His grades are predictive of his future success"。 而 "predict" 更多的是用在可以根据某些观察或者数据去预测或者预告一个确切事件或者结果，它更侧重于确定性。例如，“我可以预测明天会下雨”我们可以说"I can predict it will rain tomorrow"。 在这里"the chosen features are not predictive of the target quantity of interest"，作者是想表示选定的特征并不能有效的表明或者预示目标变量的趋势或者变化，所以用了"be predictive of"。

> In sensitive applications of machine learning, like predictive policing, resume screening, and risk models used for lending, we must be especially alert to the consequences of garbage data. 

sensitive adj.敏感的

> For example, if past hiring decisions are used to train a predictive model that will be used to screen resumes then machine learning models could inadvertently capture and automate historical injustices. Note that this can all happen without the data scientist actively conspiring, or even being aware.

advertent adj.留意的；注意的

inadvertently adj.inadvertently

> Note that this can all happen without the data scientist actively conspiring, or even being aware.

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

non-differentiability 不可微

derivative 导数

> In these cases, it is common instead to optimize a *surrogate objective*.

surrogate adj.替代的

> We learn the best values of our model’s parameters by minimizing the loss incurred on a set consisting of some number of examples collected for training. However, doing well on the training data does not guarantee that we will do well on unseen data. So we will typically want to split the available data into two partitions

incur 遭受，产生

incurred on a set 这组数据产生的损失

pratition 部分

>  You could think of training performance as analogous to the scores that a student achieves on the practice exams used to prepare for some real final exam. 

analogous adj.类似的

practice exam 模拟考试

> Over the course of studying, the student might begin to memorize the practice questions, appearing to master the topic but faltering when faced with previously unseen questions on the actual final exam.

falter v.衰弱，退步

> In brief, at each step, this method checks to see, for each parameter, how that training set loss would change if you perturbed that parameter by just a small amount.

perturb 小幅度的调整或改变

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

A good rule of thumb 一个经验法则

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

draw on 利用

> The goal is less to determine *whether* a particular page is relevant for a query, but rather which, among a set of relevant results, should be shown most prominently to a particular user.

promiently 显著地

> The problems are similar insofar as the goal is to display a set of items relevant to the user. 

insofar 在某种程度上，就某种程度而言

> For example, on a five-point scale, you might notice that items receive many one- and five-star ratings but that there are conspicuously few three-star ratings. 

conspicuously 显著地

> And our guess of what is going on in each frame might be much stronger if we take into account the previous or succeeding frames.

succeeding frame 下一帧

> With speech recognition, the input sequence is an audio recording of a speaker ([Fig. 1.3.5](https://d2l.ai/chapter_introduction/index.html#fig-speech)), and the output is a transcript of what the speaker said.

transcript 转录的结果

> The challenge is that there are many more audio frames (sound is typically sampled at 8kHz or 16kHz) than text, i.e., there is no 1:1 correspondence between audio and text, since thousands of samples may correspond to a single spoken word. 

i.e. means that is

> Unlike the case of speech recognition, where corresponding inputs and outputs occur in the same order, in machine translation, unaligned data poses a new challenge.

unaligned 不对齐的

> Consider the following illustrative example of the peculiar tendency of Germans to place the verbs at the end of sentences:

peculiar tendency 特殊倾向

>  For instance, determining the order in which a user reads a webpage is a two-dimensional layout analysis problem. 

determining 确定

> Dialogue problems exhibit all kinds of additional complications, where determining what to say next requires taking into account real-world knowledge and the prior state of the conversation across long temporal distances. Such topics are active areas of research.

dialogue 对话

exhibit 表现出

take into account 考虑到

prior state 之前的状态

> To whet your appetite for now, we describe a few of the following questions you might ask.

whet sb appetite 激起食欲，提起兴趣

> For images, we may train models to tell the relative position between two cropped regions of the same image ([Doersch *et al.*, 2015](https://d2l.ai/chapter_references/zreferences.html#id58)), to predict an occluded part of an image based on the remaining portions of the image, 

occluded adj.隔离的，封闭的

> In each case, we grab a big pile of data upfront, then set our pattern recognition machines in motion without ever interacting with the environment again. 

in motion 在运行中

> we must account for the way its actions might impact the future observations of the agent, and so offline learning is inappropriate.

account for 考虑到

> *Deep reinforcement learning*, which applies deep learning to reinforcement learning problems, has surged in popularity.

surge in popularity 人气飙升

> At each time step, the agent receives some *observation* from the environment and must choose an *action* that is subsequently transmitted back to the environment via some mechanism (sometimes called an *actuator*), 

is subsequently transmitted back to 随后传输回去

### week4

> If you are interested in using machine learning to develop an agent that interacts with an environment and takes actions, then you are probably going to wind up focusing on reinforcement learning. 

wind up 最终处于，结束于

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

linea ralgebraic operation 线性代数运算

preliminaries 预备知识

> Zotero is, at the most basic level, a reference manager. It is designed to store, manage, and cite bibliographic references, such as books and articles

bibliographic adj. 书目的；书籍解题的

Attachments 附件

> It has been a longstanding research challenge to achieve this goal, to enable machines to read, write, and communicate like humans

longstanding adj.长期存在的

> LM aims to model the generative likelihood of word sequences, so as to predict the probabilities of future (or missing) tokens.

so as to 目的是，意图是

> Since the researchers have found that model scaling can lead to an improved model capacity, they further investigate the scaling effect by increasing the parameter scale to an even larger size.

scaling 增加、扩展或提升语言模型的规模或能力

> these large-sized PLMs display different behaviors from smaller PLMs (e.g., 330M-parameter BERT and 1.5Bparameter GPT-2) and show surprising abilities (called emergent abilities [31]) in solving a series of complex tasks.

涌现能力 

> BERT [23] was proposed by pre-training bidirectional language models with specially designed pre-training tasks on large-scale unlabeled corpora.

corpora 语料库

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

comb 梳理

> Extensive research has shown that scaling can largely improve the model capacity of LLMs [26, 55, 56]. Thus, it is useful to establish a quantitative approach to characterizing the scaling effect. Next, we introduce two representative scaling laws for Transformer language models [30, 34].

"Scaling law"（规模化法则 or 尺度定律）在这里指的是一种定量方法，用于描述和预测大型语言模型（如Transformer模型）性能随模型规模（如参数数量、训练数据的大小、计算资源等）增加而改变的规律

文章解释：[阿里云](https://developer.aliyun.com/article/1446631)

> Firstly, for large models, it is infeasible to rigorously examine various training tricks or variants, and it would be very helpful if experiences gained from small models could also apply to large models.

infeasible 不可行的

tricks 技巧

variant 变体

> Secondly, the training of large-scale models takes a long time, often suffering from issues such as training loss spike, and scaling law can be employed to monitor the training status of LLMs, e.g., identifying abnormal performance at an early time. Despite that scaling law characterizes a smooth trend of performance increase (or loss decrease), it also indicates that diminishing returns might occur as model scaling.

training loss spike 训练损失突增

characrerizes 描述

"Diminishing returns"是一个经济学术语，原意指的是在生产过程中，当一个生产要素（如资本、劳动力或原材料）的投入量增加时，其他条件保持不变，新增加的产出（回报）会逐渐减少。换句话说，每增加一单位的投入，所获得的额外产出会越来越少，直到最终可能为零或负值。 在这段话中，"diminishing returns"被用来形容在大型语言模型规模增加时可能遇到的情况。初始阶段，模型规模的增加可以带来显著的性能提升，但随着模型规模继续扩大，每一次增加所带来的性能提升会变得越来越小。这表明在达到一定规模后，继续增加模型大小的成本效益逐渐降低。

> An empirical study [58] from the OpenAI team has shown that representation quality or semantic content can still effectively improve even if approaching the point of diminishing returns (i.e., approaching the irreducible loss) [58]. This finding suggests that training large models are promising for improving the performance of downstream tasks. To further explore scaling effect, a potential issue is that the amount of available data for training LLMs is actually limited. With the ever-increasing model scale, the public text data would be soon “exhausted” for LLMs [60]. Thus, it will be meaningful to study how scaling laws apply to a data-constrained regime [61], where data repetition or augmentation might be useful to alleviate data scarcity.

representation quality 表示质量

semantic content 语义内容

be promising for ...有希望的

data-constrained regime 数据受限的情况

regime 特定的情况、状态

data augmentation 数据增强

alleviate data scarity 减轻数据稀缺

## June

### week1

> 随机梯度下降（SGD）的全称是 Stochastic Gradient Descent。这是一种优化算法，用于调整深度学习和其他机器学习模型的参数，以最小化损失函数。"Stochastic" 一词指的是算法在每一步更新中使用随机抽样的子集来计算梯度。

Stochastic 随机的

### Week2

> Our fastest and most affordable flagship model

affordable 便宜的

flagship 旗舰产品

> Enter an instruction or select a preset, and watch the API respond with a message that attempts to match or answer the query.

preset 预设

> Controls diversity via nucleus sampling: 0.5 means half of all likelihood-weighted options are considered.

nucleus sampling 核采样

top_p 

> 在ChatGPT和其他基于GPT的语言模型中，`top_p`是一种称为nucleus sampling或top-p sampling的文本生成策略的参数。这种策略在生成文本时考虑可能性最高的下一个词的累积概率分布。
>
> 具体来说，`top_p`参数设置了一个概率阈值`p`，模型在每一步生成词汇时，会从概率最高的一组词汇中进行选择，这组词汇的累积概率至少为`p`。通过这种方式，模型只考虑那些累积概率达到阈值`p`的词汇，而忽略那些累积概率较低的不太可能的词汇。
>
> 假设我们让一个基于GPT的模型完成这个句子：“太阳落山后，天空呈现出一片……”，并且我们考虑使用不同的`top_p`值来控制生成的多样性。
>
> **`top_p`值较低的情况（例如，`top_p=0.3`）**
>
> 当`top_p`值较低时，模型在选择下一个词时更加保守，主要考虑那些概率最高的词汇。在这种情况下，模型可能会生成比较常见或预期的词汇来完成句子，如：“太阳落山后，天空呈现出一片**红色**。”这里，“红色”是一个相对常见的描述天空颜色的词汇，因为它的概率较高，容易被模型选中。
>
> **`top_p`值较高的情况（例如，`top_p=0.9`）**
>
> 当`top_p`值较高时，模型在生成文本时更加开放和多样，会考虑更广泛的词汇选择。这时，模型可能会生成一些更具创造性或不那么常见的词汇来完成句子，如：“太阳落山后，天空呈现出一片**橘紫交错的光辉**。”在这个例子中，由于`top_p`值较高，模型考虑了一组累积概率达到90%的词汇，这允许模型探索更多样化和具有创造性的表达方式。
>
> 通过调整`top_p`值，我们可以控制模型在生成文本时的保守程度和多样性。较低的`top_p`值让模型倾向于选择更加确定和常见的词汇，而较高的`top_p`值鼓励模型探索更广泛的可能性，生成更有创造性和多样性的文本。

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
