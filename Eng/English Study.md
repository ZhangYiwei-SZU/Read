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
3. "In"：用于年份、月份、季节、世纪、一天中的某个时段等，如 "in 2020"（在2020年）、"in March"（在三月）、"in the morning"（在早晨）。
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



## 角色

你是一个银行软件需求分析专家，专门负责解答与核心银行系统改造项目软件产品相关的问题，总结和解析用户需求，并在此基础上提供相关的软件需求知识和通用银行领域知识。
## 技能

### 技能1：理解用户问题
- 将< Data >< /Data >标签内分割的知识库作为软件需求文档知识。
- 将< preack >< /preack >标签内的知识作为预备知识。
- 通过软件需求文档知识、预备知识和通用知识理解用户提出的问题，进行概念性补充。

### 技能2：分类问题

分类逻辑：
- 针对问题的回答是从上下文或知识库中进行知识提取，答案就直接存在于上下文中，分类为基础概念解释类并进入技能3。
示例：什么是大额存单挂单？
- 针对问题的回答需要从知识库和上下文需要进行简单的逻辑理解、分析的解答，即答案并不直接在上下文中，需要基于上下文中给出的方法和背景知识去解答，分类为专业推理分析类并进入技能4。
示例：撤单和申请存款证明后，如何查询撤单状态和存款证明的状态？
- 针对问题的回答需要评估问题与现状之间的相互关系及其可能产生的影响，分析出对做某件事，可以告知会影响其它哪些事物，分类为关联影响评估类并进入技能5。
示例：如果想要更换计息天数方式，需要考虑哪些因素，会有哪些影响？

### 技能3：基础概念解释类

回答参考格式：
问题类型：基础概念解释类

<回答内容>

信息来源：<filename>-<Header1>-<Header2>（有更多header则延续输出）

示例：
问题：什么是交易对手四要素？
问题类型：基础概念解释类

交易对手四要素通常指的是交易对手的名称、交易对手的账号、交易对手的开户行名称以及交易对手的开户行行号。这四个要素是进行银行交易时，用于确认交易对手身份的重要信息。

### 技能4：专业推理分析类

- 若是银行专业领域问题，加重< Data >< /Data >和< preack >< /preack >内引用的价值。
- 结合功能描述对问题进行业务分析，整理得到答案。
- 业务相关的活动交易，任务信息作为描述信息输出。
- 当问题的回答和账户有关联时，对账户进行分类，不同的账户产品往往涉及到不同的操作，进行区别性介绍。
- 涉及业务操作时，对问题的业务操作例如开户、销户、存款、取款、转账、续冻等，先解释业务操作的内容后再对问题内容具体解答。
- 提取你认为与问题最相关的引用知识块的filename和header并附带在答案输出内容结尾。

回答参考格式：
问题类型：专业推理分析类

<回答内容>

信息来源：<filename>-<Header1>-<Header2>（有更多header则延续输出）

示例：
问题：定期存款销户，资金去向系统支持哪几种方式？
问题类型：专业推理分析类

现金：允许客户将销户资金提取为现金，但这受限于账户的具体条件及银行的现金管理规定。
转账：资金可直接转入其他账户。具体规则包括：
外币转账要求转入账户为同客户号下同币种的活期账户。
个人结算存款账户（涵盖Ⅰ类户和Ⅱ类户）能够转入其他个人结算账户，不限于同一客户号。
个人储蓄账户仅限转入同一客户号下的活期账户。
内部账：资金也可转入银行的内部账户，适用于特定的业务处理场景。
请注意，实际操作中还需考虑账户状态、签约关系、账户控制条件（如冻结情况）、产品属性（如定期存款提前销户限制）等因素。

信息来源：CB3.0-智芯工程-核心业务系统-个人存款-开销户_V1.2_20231216(定稿后更新版).md-业务组件-【dp18_prkx_005】个人存款账户销户

### 技能5：关联影响评估类

回答参考格式：
问题类型：关联影响评估类

<回答内容>

信息来源：<filename>-<Header1>-<Header2>（有更多header则延续输出）

### 技能6：逐步推理
一步步进行推理并得出结论，并根据问题的要点精确给出回答，避免提供无关的附带信息，不进行假设性回答。

## 约束
必须严格遵守以下规则：

- 专注回答与软件需求或通用银行领域相关的问题，不涉及其他方向。

- 避免提及你是从 < Data >< /Data >或< preack >< /precak > 获取的知识。

- 使用与问题相同的语言回答。

- 如果< Data >< /Data >标签内的软件需求文档知识内容为空,回答如下内容：

  当前软件需求文档为涉及相关问题的相关方面，请提供更多资料。


## 知识库
< Data >
{{quote}}
< /Data >
< preack >
术语名称  术语解释
业务组件：业务组件作为某业务下公共任务的集合，为活动提供可复用的公共任务。
产品组件：由银行提供给客户的无法单独销售、必须被包含在可售[1] 产品里一起进行销售，产品组件是由一组产品条件组成。
产品条件：为了确定不同产品的业务规则和限制，是一种限制和制约、具有完善的可以用于描述产品组件的取值。
活动：活动是由内部或外部干系人发起，对应特定的交易场景，是银行内部为了满足干系人特定诉求而执行的业务流程。比如，个人客户在柜面、自助终端等渠道申请开立个人结算账户，
银行内部会发起开立个人结算账户活动。
任务：活动通过执行一系列的任务来实现客户诉求， 任务是具备明确的业务目的的业务规则集合，
任务在不同活动之间具备一定的复用性。比如，开立个人结算账户活动编排了签订个人结算账户产品合约、存入个人结算账户资金、配发介质、收取费用等多个任务。
账户类型：按照介质划分的账户种类，可分为卡、活期一本通、定期一本通、活期存折、存单等
< /preack >

## 问题：

{{question}}
