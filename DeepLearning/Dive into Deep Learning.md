# Online Class

[课程主页](https://courses.d2l.ai/zh-v2/ )

[网课（Bilibili)](https://space.bilibili.com/1567748478/channel/seriesdetail?sid=358497)

[教材](https://zh.d2l.ai/)

[教材(eng)](https://d2l.ai/)



# 环境配置

## 基础依赖包安装

```shell
# 配置conda环境

(base) C:\Users\YW>conda create --name d2l python=3.9 -y
Collecting package metadata (current_repodata.json): done
Solving environment: done

## Package Plan ##

...
#
# To activate this environment, use
#
#     $ conda activate d2l
#
# To deactivate an active environment, use
#
#     $ conda deactivate

(d2l) C:\Users\YW>conda list
# packages in environment at D:\Anaconda\envs\d2l:
#
# Name                    Version                   Build  Channel
ca-certificates           2024.3.11            haa95532_0
openssl                   3.0.13               h2bbff1b_1
pip                       24.0             py39haa95532_0
python                    3.9.19               h1aa4202_1
setuptools                69.5.1           py39haa95532_0
sqlite                    3.45.3               h2bbff1b_0
tzdata                    2024a                h04d1e81_0
vc                        14.2                 h21ff451_1
vs2015_runtime            14.27.29016          h5e58377_2
wheel                     0.43.0           py39haa95532_0

#安装成功
```

```shell
# conda配置镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch

conda info

# pip配置镜像
python -m pip install --upgrade pip
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

(d2l) C:\Users\YW>pip config list
global.index-url='https://pypi.tuna.tsinghua.edu.cn/simple'
```

```shell
# 安装深度学习框架
# torch
(d2l) C:\Users\YW>pip install torch==1.12.0
Looking in indexes: https://pypi.tuna.tsinghua.edu.cn/simple
Collecting torch==1.12.0
  Downloading https://pypi.tuna.tsinghua.edu.cn/packages/a4/4f/d8245c749b90e643fa06547c0aa36698507597b24d501c22e5bba4fb31a8/torch-1.12.0-cp39-cp39-win_amd64.whl (161.8 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 161.8/161.8 MB 865.7 kB/s eta 0:00:00
Collecting typing-extensions (from torch==1.12.0)
  Downloading https://pypi.tuna.tsinghua.edu.cn/packages/01/f3/936e209267d6ef7510322191003885de524fc48d1b43269810cd589ceaf5/typing_extensions-4.11.0-py3-none-any.whl (34 kB)
Installing collected packages: typing-extensions, torch
# torchvision
(d2l) C:\Users\YW>pip install torchvision==0.13.0
Looking in indexes: https://pypi.tuna.tsinghua.edu.cn/simple
Collecting torchvision==0.13.0
  Downloading https://pypi.tuna.tsinghua.edu.cn/packages/5e/d0/a1265a21c742225e19123389b8665439b7a22d734ff97ecdbbfaff33a3c5/torchvision-0.13.0-cp39-cp39-win_amd64.whl (1.1 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.1/1.1 MB 1.2 MB/s eta 0:00:00
 requests, torchvision
Successfully installed certifi-2024.2.2 charset-normalizer-3.3.2 idna-3.7 numpy-1.26.4 pillow-10.3.0 requests-2.31.0 torchvision-0.13.0 urllib3-2.2.1

# d2l(numpy,pandas,matplotlib...)
(d2l) C:\Users\YW>pip install d2l==0.17.6
Looking in indexes: https://pypi.tuna.tsinghua.edu.cn/simple
Collecting d2l==0.17.6
....

```

## IDE

**Jupyter nootbook的使用**

> 指定文件夹作为目录

<img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/image-20240514164118528.png" alt="image-20240514164118528" style="zoom:50%;" />

![image-20240514164434549](https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/image-20240514164434549.png)

> shortcut key

```
Esc:返回到命令模式
Enter：编辑模式
In开头表示是代码块
数字表示执行的次数
command mode:
M转换为markdown语法块
Y转换为markdown语法块
B在下方创建代码块
A在上方创建代码块
D删除当前块
shift + enter:执行命令，跳到下一行
ctrl + enter:执行命令，跳到当前行
P:选项板，选择需要执行的操作
H：帮助面板

```

