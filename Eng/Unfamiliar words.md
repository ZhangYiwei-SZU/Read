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
