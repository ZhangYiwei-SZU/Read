# [在线笔记](https://mp.weixin.qq.com/s/Bf7uVhGiu47uOELjmC5uXQ)

# [官网(github)](https://git-scm.com/)

# [官网(gitee)](https://gitee.com/all-about-git)

# [帮助文档](https://docs.github.com/zh)

# [Git-it](https://jlord.us/git-it/)

# 遇到的问题

**为什么我push后，一级目录的文件夹名是linux/notes，里面是readme.md，而不是linux是一级目录，notes是二级目录，里面是readme.md?**

> 从你提供的信息来看，你的GitHub仓库`Read`中确实存在一个`linux/notes`的路径，其实这就表示`notes`是`linux`的子目录。在这个子目录下，应该存在你提交的`readme.md`文件。
>
> 但如果你觉得显示为`linux/notes`有些困扰，那可能是因为GitHub在显示文件和文件夹时，会将路径中的所有层级一起显示出来，而不是像我们在本地文件系统中看到的那样，一层一层地展开。
>
> 如果你想看到`linux`和`notes`分开展示的样子，你可以点击`linux/notes`，这样就会进入`linux`目录，然后你会看到`notes`目录，再点击`notes`，你就能看到`readme.md`文件了。
>
> 总的来说，这个显示方式是GitHub的设计，目的是为了在主页上给出文件的完整路径，方便用户快速找到文件。并不表示你的目录结构有问题，你的目录结构是正确的。
>
> <img src="https://raw.githubusercontent.com/113737038537/Pic/main/image-20240429154454132.png" alt="image-20240429154454132" style="zoom:67%;" />
>
> <img src="https://raw.githubusercontent.com/113737038537/Pic/main/image-20240429154422892.png" alt="image-20240429154422892" style="zoom:50%;" />
>
> 显示的是全部内容，但目录结构正确。
>
> 

**PS D:\Read> git push https://github.com/ZhangYiwei-SZU/Read**
**To https://github.com/ZhangYiwei-SZU/Read**
 **! [rejected]        main -> main (fetch first)**
**error: failed to push some refs to 'https://github.com/ZhangYiwei-SZU/Read'**
**hint: Updates were rejected because the remote contains work that you do not**
**hint: have locally. This is usually caused by another repository pushing to**
**hint: the same ref. If you want to integrate the remote changes, use**
**hint: 'git pull' before pushing again.**
**hint: See the 'Note about fast-forwards' in 'git push --help' for details.**
**这个报错是怎么产生的？**

>这个错误是由于你正在尝试将你本地的更改推送(push)到GitHub仓库，但是该仓库在你上次拉取(pull)或克隆(clone)后有新的更改。换句话说，你本地的版本落后于GitHub上的版本。
这通常发生在其他人或者包括你自己在其他设备上对同一个仓库进行了更改并推送到GitHub，再从别的设备试图推送不同的更改时。
要解决这个问题，你需要首先拉取（pull）远程仓库的最新更改到你的本地仓库：
plaintext
git pull https://github.com/ZhangYiwei-SZU/Read main
在执行这个命令后，Git将会拉取并合并远程仓库的最新更改。当然，如果在这个过程中存在你本地更改和远程更改冲突的情况，你需要手动解决这个冲突。解决完冲突后，再做一次推送（push）操作就可以成功了。
另外，强调一下，为了避免这类问题的发生，在进行推送之前，最好先进行一次拉取操作，确保本地版本是最新的。
>
>我在github这边修改后，本地需要先pull拉取更新本地库，才能push

**命令行的规则**

> 在命令行语法中，中括号（[]）和尖括号（<>）的含义是不同的。它们分别表示如下： - 中括号（[]）：中括号包围的参数表示该参数是可选的。也就是说，你可以在命令中包含该参数，也可以不包含。如果不包含该参数，命令通常会使用一些默认的设置或者行为。 - 尖括号（<>）：尖括号包围的部分表示该部分需要被用户替换。你需要将尖括号及其内部的内容替换为实际的值或者内容。 例如，对于`git remote add [-t <branch>] [-m <master>] [-f] [--tags | --no-tags] [--mirror=<fetch|push>] <name> <url>`这个命令： - `[-t <branch>]`表示 `-t` 是一个可选的参数，如果你选择使用这个参数，那么你需要将`<branch>`替换为实际的分支名。 - `<name>`和`<url>`是需要被替换的部分，你需要将它们替换为实际的远程仓库别名和URL。

**为什么有些仓库中的文件夹中有.github文件夹却没有.git文件夹？**

> 在一个Git仓库中，`.git`文件夹是非常重要的，它存储了所有关于版本控制的信息，包括提交历史、分支、标签等。然而，你通常在本地仓库中可以看到`.git`文件夹，而在GitHub上在线仓库中却看不到。这是因为，GitHub在展示仓库时默认隐藏了这个文件夹。实际上，`.git`文件夹是存在的，只不过被GitHub隐藏了。
>
> 而`.github`文件夹是用来存放GitHub特性相关的配置文件的，如GitHub Actions的工作流程配置，Issue和Pull Request的模板等。这个文件夹和`.git`文件夹的用途是完全不同的。`.github`文件夹通常需要开发者手动创建，并在其中添加相应的配置文件。GitHub在展示仓库时，并不会隐藏`.github`文件夹，因此你可以在在线仓库中直接看到这个文件夹。
>
> 所以，你在GitHub的在线仓库中可以看到`.github`文件夹却看不到`.git`文件夹，这是正常的，不需要担心。

# 版本控制

> 版本控制 = 版本迭代

版本控制（Revision control）是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。

没有进行版本控制或者版本控制本身缺乏正确的流程管理，在软件开发过程中将会引入很多问题，如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性，以及软件的整合等问题。

无论是工作还是学习，或者是自己做笔记，都经历过这样一个阶段！我们就迫切需要一个版本控制工具！

多人开发必须使用版本控制

![图片](https://raw.githubusercontent.com/113737038537/Pic/main/640)

> 常见的版本控制工具

- **Git**
- **SVN**（Subversion）
- **CVS**（Concurrent Versions System）
- **VSS**（Microsoft Visual SourceSafe）
- **TFS**（Team Foundation Server）
- Visual Studio Online

版本控制产品非常的多（Perforce、Rational ClearCase、RCS（GNU Revision Control System）、Serena Dimention、SVK、BitKeeper、Monotone、Bazaar、Mercurial、SourceGear Vault），现在影响力最大且使用最广泛的是Git与SVN

学当下最流行的软件：**Git**

## 版本控制分类

**1、本地版本控制**

记录文件每次的更新，可以对每个版本做一个快照，或是记录补丁文件，适合个人用，如RCS。

![图片](https://raw.githubusercontent.com/113737038537/Pic/main/640.png)

**2、集中版本控制  SVN**

所有的版本数据都保存在服务器上，协同开发者从服务器上同步更新或上传自己的修改

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p00V4uLaibxtZI9RLpq7tkSdlWiaF92AVeZ0ib9DicqBkS2poo5u8sEU2mCQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

所有的版本数据都存在服务器上，用户的本地只有自己以前所同步的版本，如果不连网的话，用户就看不到历史版本，也无法切换版本验证问题，或在不同分支工作。而且，所有数据都保存在单一的服务器上，有很大的风险这个服务器会损坏，这样就会丢失所有的数据，当然可以定期备份。代表产品：SVN、CVS、VSS

**3、分布式版本控制 	Git**

每个人都拥有全部的代码！安全隐患！

所有版本信息仓库全部同步到本地的每个用户，这样就可以在本地查看所有版本历史，可以离线在本地提交，只需在连网时push到相应的服务器或其他用户那里。由于每个用户那里保存的都是所有的版本数据，只要有一个用户的设备没有问题就可以恢复所有的数据，但这增加了本地存储空间的占用。

不会因为服务器损坏或者网络问题，造成不能工作的情况！

![图片](https://raw.githubusercontent.com/113737038537/Pic/main/11.webp)

# 环境配置

安装：无脑下一步

## 启动Git

安装成功后在开始菜单中会有Git项，菜单下有3个程序：任意文件夹下右键也可以看到对应的程序！

![图片](https://raw.githubusercontent.com/113737038537/Pic/main/12.webp)

**Git Bash：**Unix与Linux风格的命令行，使用最多，推荐最多

**Git CMD：**Windows风格的命令行

**Git GUI**：图形界面的Git，不建议初学者使用，尽量先熟悉常用命令

> 基本Linux命令

1. cd : 改变目录。

2. cd . . 回退到上一个目录，直接cd进入默认目录

3. pwd : 显示当前所在的目录路径。

4. ls(ll):  都是列出当前目录中的所有文件，只不过ll(两个ll)列出的内容更为详细。

5. touch : 新建一个文件 如 touch index.js 就会在当前目录下新建一个index.js文件。

6. rm:  删除一个文件, rm index.js 就会把index.js文件删除。

7. mkdir:  新建一个目录,就是新建一个文件夹。

8. rm -r :  删除一个文件夹, rm -r src 删除src目录

9. ```
   rm -rf / 切勿在Linux中尝试！删除电脑中全部文件！
   ```

10. mv 移动文件, mv index.html src index.html 是我们要移动的文件, src 是目标文件夹,当然, 这样写,必须保证文件和目标文件夹在同一目录下。

11. reset 重新初始化终端/清屏。

12. clear 清屏。

13. history 查看命令历史。

14. help 帮助。

15. exit 退出。

16. #表示注释

## Git配置

配置好环境变量后直接在cmd中就可以使用git配置仓库



查看配置：git config -l

```shell
$ git config --global -h #-h是简单的帮助
                         #--help是帮助文档
usage: git config [<options>]

Config file location
    --[no-]global         use global config file
    --[no-]system         use system config file
    --[no-]local          use repository config file
    ....
#在命令行参数中，--[no-]这个符号的意义是提供一个选项的反向操作。也就是说，如果一个选项是开关类型的，那么在这个选项前面加上no-就表示关闭这个选项
```

查看不同级别的配置文件：

```shell
#查看系统config
git config --system --list
　　
#查看当前用户（global）配置
git config --global  --list
```

**Git相关的配置文件：**

1. Git\etc\gitconfig  ：Git 安装目录下的 gitconfig   --system 系统级
2. C:\Users\Administrator\ .gitconfig   只适用于当前登录用户的配置  --global 全局

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0hcJS0rxj3qoCVvfDKh3WxwQJlSV3P15EIZuejraOwXLdic6NCB8X8oQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这里可以直接编辑配置文件，通过命令设置后会响应到这里。

> ==设置用户名与邮箱（用户标识，必要==

设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：

```shell
$ git config --global user.name "YW"
$ git config --global user.email 1137038537@qq.com
```

# ==基本理论==

 ## 本地的三个区域

Git本地有三个工作区域：工作目录（Working Directory）、暂存区(Stage/Index)、资源库(Repository或Git Directory)。如果在加上远程的git仓库(Remote Directory)就可以分为四个工作区域。文件在这四个区域之间的转换关系如下：

<img src="https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0NJ4L9OPI9ia1MmibpvDd6cSddBdvrlbdEtyEOrh4CKnWVibyfCHa3lzXw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom:80%;" />

- Workspace：工作区，就是你平时存放项目代码的地方
- Index / Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息
- Repository：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本
- Remote：远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换

本地的三个区域确切的说应该是git仓库中HEAD指向的版本：

<img src="https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0icz6X2aibIgUWzHxtwX8kicPCKpDrsiaPzZk04OlI2bzlydzicBuXTJvLEQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom:67%;" />

- Directory：使用Git管理的一个目录，也就是一个仓库，包含我们的工作空间和Git的管理空间。
- WorkSpace：需要通过Git进行版本控制的目录和文件，这些目录和文件组成了工作空间。
- .git：存放Git管理信息的目录，初始化仓库的时候自动创建。
- Index/Stage：暂存区，或者叫待提交更新区，在提交进入repo之前，我们可以把所有的更新放在暂存区。
- Local Repo：本地仓库，一个存放在本地的版本库；HEAD会只是当前的开发分支（branch）。
- Stash：隐藏，是一个工作状态保存栈，用于保存/恢复WorkSpace中的临时状态。

## 工作流程

git的工作流程一般是这样的：

１、在工作目录中添加、修改文件；

２、将需要进行版本管理的文件放入暂存区域；

３、将暂存区域的文件提交到git仓库。

因此，git管理的文件有三种状态：已修改（modified）,已暂存（staged）,已提交(committed)

<img src="https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p09iaOhl0dACfLrMwNbDzucGQ30s3HnsiaczfcR6dC9OehicuwibKuHjRlzg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom:67%;" />

# 项目搭建

## 创建工作目录与常用指令

工作目录（WorkSpace)一般就是希望Git帮助管理的文件夹，可以是你项目的目录，也可以是一个空目录，建议不要有中文。

日常使用只要记住下图6个命令：

<img src="https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0AII6YVooUzibpibzJnoOHHXUsL3f9DqA4horUibfcpEZ88Oyf2gQQNR6w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1" alt="图片" style="zoom:67%;" />

## 仓库搭建

* 本地仓库搭建

1、创建全新的仓库，需要用GIT管理的项目的根目录执行：

```shell
YW@▒▒▒▒ΰ MINGW64 /d/Gitcode
$ git init
Initialized empty Git repository in D:/Gitcode/.git/
```

2、执行后可以看到，仅仅在项目目录多出了一个.git目录，关于版本等的所有信息都在这个目录里面。

* 克隆远程仓库

```shell
# 克隆一个项目和它的整个代码历史(版本信息)
D:\> git clone https://github.com/113737038537/Read.git
Cloning into 'Read'...
remote: Enumerating objects: 39, done.
remote: Counting objects: 100% (39/39), done.
remote: Compressing objects: 100% (27/27), done.
remote: Total 39 (delta 1), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (39/39), 18.07 KiB | 162.00 KiB/s, done.
Resolving deltas: 100% (1/1), done.
PS D:\>
```

<img src="https://raw.githubusercontent.com/113737038537/Pic/main/image-20240427144032500.png" alt="image-20240427144032500" style="zoom: 80%;" />

# 文件操作

## 文件的四种状态

版本控制就是对文件的版本控制，要对文件进行修改、提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的文件，或者要提交的文件没提交上。

- Untracked: 未跟踪, 此文件新添加到文件夹中, 但并没有加入到git库, 不参与版本控制. 通过**git add**状态变为**Staged**.
- Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件
- Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态, 使用git checkout则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改 !
- Staged: 暂存状态. 执行**git commit**则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态. 执行git reset HEAD filename取消暂存, 文件状态为Modified

## 查看文件状态

```shell
#查看指定文件状态
git status [filename]

#查看所有文件状态
git status

# git add .                  添加所有文件到暂存区
# git commit -m "消息内容"    提交暂存区中的内容到本地仓库 -m 提交信息
```

## 忽略文件

有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等

在主目录下建立".gitignore"文件，此文件有如下规则：

1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。（注释）
2. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。
3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

```shell
*.txt        #忽略所有 .txt结尾的文件,这样的话上传就不会被选中！
!lib.txt     #但lib.txt除外
/temp        #仅忽略项目根目录下的TODO文件,不包括其它目录temp
build/       #忽略build/目录下的所有文件
doc/*.txt    #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

<img src="https://raw.githubusercontent.com/113737038537/Pic/main/image-20240427151205606.png" alt="image-20240427151205606" style="zoom:67%;" align = "center"/>

## ==Push到远程仓库==

### 实例

#### 修改Git工作区内容(add)

```shell
PS D:\Read> git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Deep Learning/

nothing added to commit but untracked files present (use "git add" to track)
```

> 这段命令是在Git的命令行界面中运行的，用于查看Git仓库的当前状态。
>
> 这是对每一行的解释：
>
> - `PS D:\Read> git status`：`git status`是一个Git命令，用于显示工作目录和暂存区的状态。它会告诉你哪些文件已修改，哪些文件已暂存但尚未提交，哪些文件尚未暂存，以及哪些文件是未跟踪的。在这个例子中，命令在`D:\Read`目录下运行。
> - `On branch main`：这表示你当前在名为`main`的分支上。
> - `Your branch is ahead of 'origin/main' by 1 commit.`：这表示你的本地`main`分支比远程`origin/main`分支领先1个提交。这通常意味着你在本地做了一些更改并提交了，但还没有将这些更改推送到远程仓库。
> - `(use "git push" to publish your local commits)`：这是一个建议，告诉你可以使用`git push`命令将你的本地提交推送到远程仓库。
> - `Untracked files:`：这表示有一些文件在Git中是未跟踪的。这些文件是新添加到目录中，或者在.gitignore文件中被忽略的。
> - `(use "git add <file>..." to include in what will be committed)`：这是一个建议，告诉你可以使用`git add <file>`命令将未跟踪的文件添加到Git，这样它们就会被包括在下一次提交中。
> - `Deep Learning/`：这是一个未跟踪的文件或文件夹。在这个例子中，它是一个名为`Deep Learning`的文件夹。
> - `nothing added to commit but untracked files present (use "git add" to track)`：这表示没有文件被添加到暂存区，准备提交，但有未跟踪的文件存在。你可以使用`git add`命令将它们添加到暂存区，准备下一次提交。

#### 添加到暂存区(commit)

```shell
PS D:\Read> git add .
PS D:\Read> git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   Deep Learning/Note/Dive into Deep Learning.md
```

> 这段命令是在Git的命令行界面中运行的，用于查看Git仓库的当前状态和添加新的更改到暂存区。
>
> 这是对每一行的解释：
>
> - `PS D:\Read> git add .`：`git add .` 是一个Git命令，用于将当前目录下的所有更改添加到暂存区。在这个例子中，命令在`D:\Read`目录下运行。`.`代表当前目录，所以这条命令会将当前目录及其子目录下的所有文件和文件夹的更改添加到暂存区。
> - `PS D:\Read> git status`：`git status`是一个Git命令，用于显示工作目录和暂存区的状态。它会告诉你哪些文件已修改，哪些文件已暂存但尚未提交，哪些文件尚未暂存，以及哪些文件是未跟踪的。
> - `On branch main`：这表示你当前在名为`main`的分支上。
> - `Your branch is ahead of 'origin/main' by 1 commit.`：这表示你的本地`main`分支比远程`origin/main`分支领先1个提交。这通常意味着你在本地做了一些更改并提交了，但还没有将这些更改推送到远程仓库。
> - `(use "git push" to publish your local commits)`：这是一个建议，告诉你可以使用`git push`命令将你的本地提交推送到远程仓库。
> - `Changes to be committed:`：这表示有一些文件已经被添加到暂存区，准备提交。这些文件是你对它们做出更改后，使用`git add`命令添加到暂存区的。
> - `(use "git restore --staged <file>..." to unstage)`：这是一个建议，告诉你如果你想取消暂存某些文件，可以使用`git restore --staged <file>`命令。
> - `new file: Deep Learning/Note/Dive into Deep Learning.md`：这是一个将要被提交的新文件。在这个例子中，它是一个名为`Dive into Deep Learning.md`的文件，位于`Deep Learning/Note/`目录下。

#### 提交到仓库(push)

1. 通过`URL`PUSH

```shell
PS D:\Read> git push https://github.com/113737038537/Read
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 553 bytes | 553.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/113737038537/Read
   a553799..d671878  main -> main
```

>这是一段在Git命令行界面中运行的命令，用于将本地的更改推送（push）到远程仓库。
>
>这是对每一行的解释：
>
>- `PS D:\Read> git push https://github.com/113737038537/Read`：`git push`是一个Git命令，用于将本地仓库的更改推送到远程仓库。在这个例子中，命令在`D:\Read`目录下运行，并将更改推送到`https://github.com/113737038537/Read`这个远程仓库。
>- `Enumerating objects: 5, done.`：Git正在计算需要推送的对象数量。在这个例子中，有5个对象需要被推送。
>- `Counting objects: 100% (5/5), done.`：Git已经完成了对象的计数。在这个例子中，5个对象都已计数完毕。
>- `Delta compression using up to 16 threads`：Git正在使用最多16个线程进行delta压缩。Delta压缩是一种Git用来减少存储空间和提高传输速度的方法。
>- `Compressing objects: 100% (4/4), done.`：Git已经完成了对象的压缩。在这个例子中，4个对象都已压缩完毕。
>- `Writing objects: 100% (4/4), 553 bytes | 553.00 KiB/s, done.`：Git已经完成了对象的写入。在这个例子中，4个对象都已写入完毕，总共占用了553字节的空间，写入速度为553.00 KiB/s。
>- `Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)`：这行给出了一些关于推送操作的统计信息。在这个例子中，总共有4个对象被推送，没有对象被重复使用，没有对象被重复打包。
>- `To https://github.com/113737038537/Read`：这是推送操作的目标地址，即你的远程仓库的URL。
>- `a553799..d671878 main -> main`：这表示你的`main`分支已经被成功推送到远程仓库。`a553799..d671878`是这次推送操作的提交范围。

2. 通过`<name>`PUSH

具体看

```shell
git remote -h
```

> 当你把一个仓库克隆（git clone）到本地时，这个远程仓库会自动被命名为"origin"。这是一个约定俗成的命名规则，通常情况下我们都会这么做。所以，无论你的远程仓库URL是什么，你都可以通过`origin`这个名字来引用它。
>
> 当你执行`git clone https://github.com/ZhangYiwei-SZU/Read.git`时，Git 会自动创建一个名为 "origin" 的远程别名，指向你的 GitHub 仓库 "https://github.com/ZhangYiwei-SZU/Read.git"。
>
> 如果你想看你所有的远程仓库及其别名，你可以使用`git remote -v`这条命令，它会显示所有远程仓库的别名以及它们的URL。
>
> 当然，如果你想使用别的名字作为远程仓库的别名也是可以的，你可以使用`git remote add [别名] [远程仓库URL]`命令来为远程仓库起别名。比如，`git remote add read https://github.com/ZhangYiwei-SZU/Read.git`，这时你就可以用 `read` 这个别名引用你的远程仓库了。

![image-20240427155314026](https://raw.githubusercontent.com/113737038537/Pic/main/image-20240427155314026.png)

## Clone/Pull

> `git clone`和`git pull`都是Git中的命令，用于从远程仓库获取代码，但它们的用途是不同的。
>
> **git clone**
>
> `git clone`命令用于创建远程仓库的一个本地副本。也就是说，如果你想在本地机器上工作，但所有的代码都在远程Git仓库中，你可以使用`git clone`命令将整个仓库拷贝到本地。此命令将会在本地创建一个目录，拷贝仓库所有的文件到这个新目录中，并初始化一个`.git`目录，其中含有全部的版本管理信息。简单来说，`git clone`命令重建了远程仓库的所有内容和版本历史。
>
> **git pull**
>
> 相较于`git clone`，`git pull`命令则是在已经存在本地仓库的情况下使用的，用来更新本地仓库到最新版。当其他人在你`git clone`之后改变了远程仓库（例如提交了新的改动），你的本地仓库将不再是最新版本。在这种情况下，你可以使用`git pull`命令将这些新的提交拉取到本地，让你的本地仓库保持与远程仓库的一致性。
>
> 所以，两者的主要区别在于：
>
> - `git clone`是用来从远程获取Git仓库，并在本地创建一个相同的版本库；
> - `git pull`则是用于已经被克隆的本地版本库，用来获取远程版本库中的最新提交和改动。

### Clone

```shell
PS D:\Study> git clone https://github.com/113737038537/d2l-zh
Cloning into 'd2l-zh'...
remote: Enumerating objects: 23948, done.
remote: Counting objects: 100% (197/197), done.
remote: Compressing objects: 100% (104/104), done.
remote: Total 23948 (delta 94), reused 176 (delta 91), pack-reused 23751
Receiving objects: 100% (23948/23948), 309.44 MiB | 726.00 KiB/s, done.
Resolving deltas: 100% (16756/16756), done.
Updating files: 100% (834/834), done.
warning: the following paths have collided (e.g. case-sensitive paths
on a case-insensitive filesystem) and only one from the same
colliding group is in the working tree:

  'img/Marginal.svg'
  'img/marginal.svg'
  'img/Neuron.svg'
  'img/neuron.svg'
```

>这段命令是执行在命令行中执行的一段`git clone`操作。
>
>让我们分步骤来解析这段命令：
>
>1. **`PS D:\Study> git clone https://github.com/113737038537/d2l-zh`**: 这是从远程仓库克隆项目到本地的命令。"PS D:\Study>"是表示你当前的工作路径是"D:\Study"，而"git clone https://github.com/113737038537/d2l-zh"命令是从该"https://github.com/113737038537/d2l-zh"地址的远程Git仓库中克隆项目到本地。
>2. **`Cloning into 'd2l-zh'...`**: 表明正在克隆远程仓库到本地的"d2l-zh"目录。
>3. **`remote: Enumerating objects: 23948, done.`**: 这表示远程仓库中总共有23948个对象。Git对象可以是blob（数据）、tree（目录）、commit（提交）或tag（标签）。
>4. **`remote: Counting objects: 100% (197/197), done.`**: Git已经计算了需要拉取的对象总数。
>5. **`remote: Compressing objects: 100% (104/104), done.`**: Git正在压缩传输对象以加速下载过程。
>6. **`remote: Total 23948 (delta 94), reused 176 (delta 91), pack-reused 23751`**: 这里是Git接受对象阶段的统计信息。
>7. **`Receiving objects: 100% (23948/23948), 309.44 MiB | 726.00 KiB/s, done.`**: 这表示已完成所有对象接收过程，数据量为309.44 MiB，速度为726.00 KiB/s。
>8. **`Resolving deltas: 100% (16756/16756), done.`**: "delta"在Git中指的是文件的改动，这条消息表示所有的文件改动都已经解析完成。
>9. **`Updating files: 100% (834/834), done.`**: 这表示所有的文件都已经更新完成。
>10. **`warning: the following paths have collided (e.g. case-sensitive paths on a case-insensitive filesystem) and only one from the same colliding group is in the working tree:`**: 这是一个警告信息，表示在大小写不敏感的文件系统中，有些文件路径因为大小写的不同而发生了冲突。这种情况在Linux和Windows上经常发生，因为Linux的文件系统是大小写敏感的，而Windows的文件系统是大小写不敏感的。例如，`img/Marginal.svg`和`img/marginal.svg`在Linux中被视为两个不同的文件，但在Windows中被视为相同的文件。
>11. **`'img/Marginal.svg' 'img/marginal.svg' 'img/Neuron.svg' 'img/neuron.svg'`**: 这些是因大小写不同而在大小写不敏感的文件系统产生冲突的文件路径。

### Push

```shell
PS D:\Read> git pull
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (2/2), 880 bytes | 293.00 KiB/s, done.
From https://github.com/113737038537/Read
   e67324d..9dc0905  main       -> origin/main
Updating d4bbc39..9dc0905
Fast-forward
 linux/notes/readme.md | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 linux/notes/readme.md
```

>你刚才执行的是一个`git pull`命令，这是从你的远程仓库拉取更新到本地的一个操作。现在我们来依次解释这段命令的输出：
>
>1. **`remote: Enumerating objects: 3, done.`**: 这是从远程仓库中获取对象信息，总共发现了3个对象。
>2. **`remote: Counting objects: 100% (3/3), done.`**: 这一步是在计算需要获取的对象的数量，完成了全部的3个。
>3. **`remote: Compressing objects: 100% (2/2), done.`**: 这一步是在压缩对象以便于传输，所有对象都已经被成功压缩。
>4. **`remote: Total 2 (delta 1), reused 0 (delta 0), pack-reused 0`**: 这些是关于对象包的统计信息。总共有2个对象，其中1个是差异对象，没有重复利用。
>5. **`Unpacking objects: 100% (2/2), 880 bytes | 293.00 KiB/s, done.`**: 这是在解压缩对象，在本地文件系统中写入这些更新。完成了全部的2个对象，包总大小880字节，下载速度为293.00 KiB/s。
>6. **`From https://github.com/113737038537/Read`**: 这是显示你正在拉取更新的远程仓库地址。
>7. **`e67324d..9dc0905 main -> origin/main`**: 这说明在远程仓库上的`main`分支已经由`e67324d`更新到了`9dc0905`。你的本地仓库需要做相应地更新。
>8. **`Updating d4bbc39..9dc0905`**: 这表明你的本地`main`分支即将由`d4bbc39`更新到`9dc0905`。
>9. **`Fast-forward`**: 这意味着，你的`main`分支是落后于`origin/main`的，没有发生冲突，可以直接“快进”更新到最新的状态。
>10. **`linux/notes/readme.md | 0` `1 file changed, 0 insertions(+), 0 deletions(-)` `delete mode 100644 linux/notes/readme.md`**: 这些信息总结了具体的文件更新，`linux/notes/readme.md`这个文件被删除，没有插入的行，也没有删除的行。标记为`delete mode 100644`表明这个文件的模式由100644变为了删除。

# 码云

# IDEA中集成Git

# Git分支

分支在GIT中相对较难，分支就是科幻电影里面的平行宇宙，如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，我们就需要处理一些问题了！

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0BOGzaG4QTc4JXO0hSlwcNtujNzAvxeibSrajLYLCT6otNnHDV9xYWwA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Ksu8UlITwMlbX3kMGtZ9p0Ayn87woxfepOhSlUj4FQTFUsia4ic0j6aQy4Tz32PRuJ0HSVeGeUzURA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

git分支中常用指令：

```shell
# 列出所有本地分支
git branch

# 列出所有远程分支
git branch -r

# 新建一个分支，但依然停留在当前分支
git branch [branch-name]

# 新建一个分支，并切换到该分支
git checkout -b [branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```

如果同一个文件在合并分支时都被修改了则会引起冲突：解决的办法是我们可以修改冲突文件后重新提交！选择要保留他的代码还是你的代码！

master主分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作，工作一般情况下在新建的dev分支上工作，工作完后，比如上要发布，或者说dev分支代码稳定后可以合并到主分支master上来。

![](https://raw.githubusercontent.com/113737038537/Pic/main/image-20240429154454132.png)

1111
