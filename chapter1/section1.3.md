# git代码'检出'
git采用分布式无中心化设计，因此检出代码的同时需要将完整的仓库下载到本地。所以不像SVN一样可以直接用checkout来直接检出服务端的版本库（即开发代码）到本地工作目录，在git中应该使用git clone将远程仓库检出到本地。

##git clone 流程
**git clone** 是一个**复合高级指令**，内部会执行git init（在本地初始化git repository，即创建.git隐藏目录）、git pull（将远程仓库的几乎所有拷贝到本地）、git remote add（将远程仓库的URL连接添加到记录），以及git checkout（将默认的仓库的master分支代码拷贝到本地工作目录working directory和缓冲区index）。 
![git clone](http://i2.muimg.com/569521/17b0563254872a85.png)
## 拓展内容-git pull
要注意git pull与git fetch的区别，由下图可以看出git pull是git fetch和git merge的复合指令，由此可以得出git fetch只负责将文件检出到本地，并不会与当前工作区的代码合并。
![git pull](http://i2.muimg.com/569521/272e46eb6608fb98.png)
##拓展内容-git checkout系列之*checkout的底层机制*
通过“**git的日常操作流workflow**”和“**git的代码‘检出**’”我们大致了解了如何从仓库中将git所管理的各种文件拉取到本地。

这里着重说下checkout，尤其是当需要同时管理多个分支，在多个分支之间切换时；甚至是当需要与同一个源的其他仓库进行合并时（即我们通常所说的多人协同开发）。

checkout所做的事情就是**将命令行对应的版本库中或者index中的文件拷贝出来，粘贴到working directory（如果参数是版本库也会拷贝到index区域）区域中**
![git checkout 简单示意图](http://img.blog.csdn.net/20160730183413406)
当git checkout后面跟的是一个本地（或远程）分支、或者HEAD（即默认的当前分支）时，实际的操作如上图所示：

 * 会将本地的**working directory**和 **index** 的内容设置成**与制定的分支**（你checkout选择的分支）的**最近一次提交内容相一致**，即**目标分支中存在的任何文件都会被拷贝到index和working directory中**。
 
* 同时也意味着**属于现有分支，但目标分支不存在的文件**，将会自动从index和working directory中**暂时移除**
> 例如：我创建了一个test.txt文件，我从默认分支（master）切换到新建分支
> BranchB，然后一系列add，commit之后，再切回分支master，test.txt文件会
> 自己消失（已经在working directory移除）

* 两个分支提交都存在的文件保持不变。

##拓展内容-git checkout系列之*checkout多分支维护*
* 新建的文件在working directory的中属于状态untracked，不会影响分支的切换（不论你怎么切换分支，新建的文件都不会‘暂时移除’）。

* 新建的文件在某一分支上 git add之后，但并未commit，也不会影响分支切换。

* 新建的文件在当前分支commit之后，如果有修改，但没有再一次commit，那么此时切换另一分支会报错

>（因为新建的文件在当前分支commit的时候就算属于当前分支了，在你修改之后但没commit，却要切换分支，那么git本来是准备遵循‘移除，属于现有分支，但目标分支不存在的文件’，但发现你的文件修改之后未提交，还处于临时状态，如果移除了，会导致本地修改丢失，故报错）

##拓展内容-git checkout系列之*‘错误的dirty状态’*
至此我们清楚了checkout是如何完成分支切换的，以及什么情况下才能切换。这也就是官方所说的只有在非“dirty”状态下才能自由执行checkout指令。

因此当你遇到这样的状况，你不想/不能，提交你正在进行中的工作，但又不得不切换到其他分支，去完成那个分支上的任务或者工作，那么你就可以这样做：

1. 储藏你的当前修改 **stash**

2. 乘搭‘时光机’回到最近的版本 reset -hrad HEAD

3. 切换分支 checkout 


这里就不得不提前拓展以下几个个命令：

git stash 和git stash apply：将当前工作储藏and重新应用你储藏好的修改

git stash list：查看现有的所有储藏

git stash drop 移除某个储藏的工作
## 本章完
<img src="http://i4.piimg.com/569521/b021492809d6b2e4.jpg" width=800>