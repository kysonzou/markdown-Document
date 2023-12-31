### 主流的Git托管平台

Github：目前的主流，有出Github desktop客户端，被软收购

Bitbucket：国外平台，有出SourceTree客户端， 属于Atlassian公司

GitLab：不太了解

Coding：国内平台

### 版本控制系统的发展

#### 本地版本控制系统

属于第一代版本控制系统，主流的有RCS，工作原理：在硬盘上保存补丁集（补丁是指文件修订前后的变化），通过应用所有的补丁，可以重新计算出各个版本的文件内容。

缺陷：不能很好的协同工作，因为文件只保留在本地，容易出现数据丢失的风险

#### 集中化版本控制系统

属于第二代版本控制系统，主流有的SVN，工作原理：用一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。

缺陷：和本地控制系统一样，如果中央服务器的出现故障，也会出现数据丢失的风险，只剩下人们在各自机器上保留的单独快照。

#### 分布式版本控制系统

属于第三代版本控制系统，主流的有Git，工作原理：和集中式不同的是客户端并不只提取最新版本的文件快照，而是把代码仓库完整地镜像下来。 这么一来，任何一处协同工作用的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复。 **因为每一次的克隆操作，实际上都是一次对代码仓库的完整备份**。

缺陷：暂时不知道，但是它解决了集中化版本控制系统的缺陷

### Git工作区、暂存区、版本库

我们先来理解下 Git 工作区、暂存区和版本库概念：

- **工作区：**就是你在电脑里能看到的目录。
- **暂存区：**英文叫 stage 或 index。一般存放在 **.git** 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- **版本库：**工作区有一个隐藏目录 **.git**，这个不算工作区，而是 Git 的版本库。

下面这个图展示了工作区、版本库中的暂存区和版本库之间的关系：![git版本库](../assets/CLI程序-Git-git版本库.jpeg)

- 图中左侧为工作区，右侧为版本库。在版本库中标记为 "index" 的区域是暂存区（stage/index），标记为 "master" 的是 master 分支所代表的目录树。
- 图中我们可以看出此时 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。
- 图中的 objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。
- 当对工作区修改（或新增）的文件执行 **git add** 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。
- 当执行提交操作 **git commit** 时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。



### 参考

[Git教程](https://www.runoob.com/git/git-basic-operations.html)
