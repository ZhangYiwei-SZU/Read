# 安装
:label:`chap_installation`
我们需要配置一个环境来运行 Python、Jupyter Notebook、相关库以及运行本书所需的代码，以快速入门并获得动手学习经验。
## 安装 Miniconda
最简单的方法就是安装依赖Python 3.x的[Miniconda](https://conda.io/en/latest/miniconda.html)。
如果已安装conda，则可以跳过以下步骤。访问Miniconda网站，根据Python3.x版本确定适合的版本。
如果我们使用macOS，假设Python版本是3.9（我们的测试版本），将下载名称包含字符串“MacOSX”的bash脚本，并执行以下操作：
如果我们使用Linux，假设Python版本是3.9（我们的测试版本），将下载名称包含字符串“Linux”的bash脚本，并执行以下操作：
接下来，初始化终端Shell，以便我们可以直接运行`conda`。
现在关闭并重新打开当前的shell。并使用下面的命令创建一个新的环境：
现在激活 `d2l` 环境：
## 安装深度学习框架和`d2l`软件包
在安装深度学习框架之前，请先检查计算机上是否有可用的GPU。
例如可以查看计算机是否装有NVIDIA GPU并已安装[CUDA](https://developer.nvidia.com/cuda-downloads)。
如果机器没有任何GPU，没有必要担心，因为CPU在前几章完全够用。
但是，如果想流畅地学习全部章节，请提早获取GPU并且安装深度学习框架的GPU版本。
:begin_tab:`mxnet`
安装MXNet的GPU版本，首先需要知道已安装的CUDA版本。
（可以通过运行`nvcc --version`或`cat /usr/local/cuda/version.txt`来检验。）
假设已安装CUDA 10.1版本，请执行以下命令：
可以根据CUDA版本更改如上`mxnet-cu101`的最后一位数字，
例如：CUDA 10.0是`cu100`， CUDA 9.0是`cu90`。
如果机器没有NVIDIA GPU或CUDA，可以按如下方式MXNet的CPU版本：
:end_tab:
:begin_tab:`pytorch`
我们可以按如下方式安装PyTorch的CPU或GPU版本：
:end_tab:
:begin_tab:`tensorflow`
我们可以按如下方式安装TensorFlow的CPU或GPU版本：
:end_tab:
:begin_tab:`paddle`
安装PaddlePaddle的GPU版本，首先需要知道已安装的CUDA版本。
（可以通过运行`nvcc --version`或`cat /usr/local/cuda/version.txt`来检验。）
假设已安装CUDA 11.2版本，请执行以下命令：
如果机器没有NVIDIA GPU或CUDA，可以按如下方式PaddlePaddle的CPU版本：
:end_tab:
我们的下一步是安装`d2l`包，以方便调取本书中经常使用的函数和类：
## 下载 D2L Notebook
接下来，需要下载这本书的代码。
可以点击本书HTML页面顶部的“Jupyter 记事本”选项下载后解压代码，或者可以按照如下方式进行下载：
:begin_tab:`mxnet`
注意：如果没有安装`unzip`，则可以通过运行`sudo apt install unzip`进行安装。
:end_tab:
:begin_tab:`pytorch`
注意：如果没有安装`unzip`，则可以通过运行`sudo apt install unzip`进行安装。
:end_tab:
:begin_tab:`tensorflow`
注意：如果没有安装`unzip`，则可以通过运行`sudo apt install unzip`进行安装。
:end_tab:
:begin_tab:`paddle`
注意：如果没有安装`unzip`，则可以通过运行`sudo apt install unzip`进行安装。
:end_tab:
安装完成后我们可以通过运行以下命令打开Jupyter笔记本（在Window系统的命令行窗口中运行以下命令前，需先将当前路径定位到刚下载的本书代码解压后的目录）：
现在可以在Web浏览器中打开<http://localhost:8888>（通常会自动打开）。
由此，我们可以运行这本书中每个部分的代码。
在运行书籍代码、更新深度学习框架或`d2l`软件包之前，请始终执行`conda activate d2l`以激活运行时环境。
要退出环境，请运行`conda deactivate`。
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/2082)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/2083)
:end_tab:
:begin_tab:`tensorflow`
[Discussions](https://discuss.d2l.ai/t/2084)
:end_tab:
:begin_tab:`paddle`
[Discussions](https://discuss.d2l.ai/t/11679)
:end_tab: