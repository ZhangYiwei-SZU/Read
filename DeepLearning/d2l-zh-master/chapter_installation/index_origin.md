# Installation
:label:`chap_installation`
In order to get you up and running for hands-on learning experience,
we need to set you up with an environment for running Python,
Jupyter notebooks, the relevant libraries,
and the code needed to run the book itself.
## Installing Miniconda
The simplest way to get going will be to install
[Miniconda](https://conda.io/en/latest/miniconda.html). The Python 3.x version
is required. You can skip the following steps if conda has already been installed.
Download the corresponding Miniconda sh file from the website
and then execute the installation from the command line
using `sh <FILENAME> -b`. For macOS users:
For Linux users:
Next, initialize the shell so we can run `conda` directly.
Now close and re-open your current shell. You should be able to create a new
environment as following:
## Downloading the D2L Notebooks
Next, we need to download the code of this book. You can click the "All
Notebooks" tab on the top of any HTML page to download and unzip the code.
Alternatively, if you have `unzip` (otherwise run `sudo apt install unzip`) available:
Now we will want to activate the `d2l` environment and install `pip`.
Enter `y` for the queries that follow this command.
## Installing the Framework and the `d2l` Package
:begin_tab:`mxnet,pytorch`
Before installing the deep learning framework, please first check
whether or not you have proper GPUs on your machine
(the GPUs that power the display on a standard laptop
do not count for our purposes).
If you are installing on a GPU server,
proceed to :ref:`subsec_gpu` for instructions
to install a GPU-supported version.
Otherwise, you can install the CPU version.
That will be more than enough horsepower to get you
through the first few chapters but you will want
to access GPUs before running larger models.
:end_tab:
:begin_tab:`mxnet`
:end_tab:
:begin_tab:`pytorch`
:end_tab:
:begin_tab:`tensorflow`
You can install TensorFlow with both CPU and GPU support via the following:
:end_tab:
We also install the `d2l` package that encapsulates frequently used
functions and classes in this book.
Once they are installed, we now open the Jupyter notebook by running:
At this point, you can open http://localhost:8888 (it usually opens automatically) in your Web browser. Then we can run the code for each section of the book.
Please always execute `conda activate d2l` to activate the runtime environment
before running the code of the book or updating the deep learning framework or the `d2l` package.
To exit the environment, run `conda deactivate`.
## GPU Support
:label:`subsec_gpu`
:begin_tab:`mxnet,pytorch`
By default, the deep learning framework is installed without GPU support
to ensure that it will run on any computer (including most laptops).
Part of this book requires or recommends running with GPU.
If your computer has NVIDIA graphics cards and has installed [CUDA](https://developer.nvidia.com/cuda-downloads),
then you should install a GPU-enabled version.
If you have installed the CPU-only version,
you may need to remove it first by running:
:end_tab:
:begin_tab:`tensorflow`
By default, TensorFlow is installed with GPU support.
If your computer has NVIDIA graphics cards and has installed [CUDA](https://developer.nvidia.com/cuda-downloads),
then you are all set.
:end_tab:
:begin_tab:`mxnet`
:end_tab:
:begin_tab:`pytorch`
:end_tab:
:begin_tab:`mxnet,pytorch`
Then we need to find the CUDA version you installed.
You may check it through `nvcc --version` or `cat /usr/local/cuda/version.txt`.
Assume that you have installed CUDA 10.1,
then you can install with the following command:
:end_tab:
:begin_tab:`mxnet`
:end_tab:
:begin_tab:`pytorch`
:end_tab:
:begin_tab:`mxnet,pytorch`
You may change the last digits according to your CUDA version, e.g., `cu100` for
CUDA 10.0 and `cu90` for CUDA 9.0.
:end_tab:
## Exercises
1. Download the code for the book and install the runtime environment.
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/23)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/24)
:end_tab:
:begin_tab:`tensorflow`
[Discussions](https://discuss.d2l.ai/t/436)
:end_tab: