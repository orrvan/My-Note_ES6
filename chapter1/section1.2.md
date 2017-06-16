# git的日常操作流workflow

##先看git的三个’阶段’
**working tree/working directory**：可简单理解为本地副本。
> The **working directory** is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

**index/staging area**：可简单理解为缓存区。
> The **staging area is** a file, generally contained in your Git directory, that stores information about what will Go into your next commit. It’s sometimes referred to as the “index”, but it’s also common to refer to it as the staging area.

**repository**：分为local repository（本地的版本库）和remote repository（远程仓库）由于第一章节所描述的分布式设计,每个人的电脑都是一个完整的版本库,所以俩者内容实质是一样的。
> The **Git directory** is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.

##三个阶段的简易联系
working tree ->git add->index ，   index->git commit->repository 
##再看git的四种文件状态
官方文档给出了git版本管理系统下的文件的各种状态，包括untracked（无迹可寻的）、unmodified（未修改的）、modified（修改的）、staged（进阶阶段之后的’）
![workflow](http://img.blog.csdn.net/20160730183243795)
下面的这张图更清晰的描述了git各种操作指令对版本控制各状态的影响
<img src="http://img.blog.csdn.net/20160730183343452" width=800  />
注意：

git fetch是从远程拉取代码到本地，只是拉取。

git rebase用于把一个分支的修改合并到当前分支。

git pull不仅拉取到本地还merge到本地分支中。所以git pull是git fetch与git merge的集合体。

git pull = git fetch + git merge

git pull --rebase = git fetch + git rebase

git checkout 所做的事情就是将命令行对应的版本库中或者index中的文件拷贝出来，粘贴到working directory（如果参数是版本库也会拷贝到index区域）区域中
##备注
注意，不要将git所管理的文件的状态（untracked、unmodified、modified、staged）与git自身的阶段（working tree、index、local repository、remote repository）相混淆。
> working directory中的文件可以包含多种状态，例如从版本库上一次提交snapshot检出的文件处于tracked和unmodified状态、本地对tracked文件的任何修改会使文件处于modified和staged（git add操作即可）状态，**本地新增文件或其他操作会使得文件处于untracked状态**；

> index中的文件只能处于modified和staged状态（同时处于）；

> repository(local or remote)中文件的状态只能处于unmodified的跟踪状态。
> *——当然这句话还有待考究，这里严格意义来说是从repository中检出的文件只能处于unmodified的tracked状态，因为你只能从别的仓库中将unmodified的tracked状态的文件拉倒本地。但原始的仓库中其实有可能存在着其他状态的文件，但是对外来讲是隐藏的、透明的。*

##本章完
<img src="http://i4.piimg.com/569521/844410bcd0ec3647.jpg" height=600 >





