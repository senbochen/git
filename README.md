## Git 是如何解决我们版本控制的问题的？
> Git 的核心功能是在文件中创建保存点。我喜欢把这些保存点想象成电子游戏中的那些——你到达的检查点，即使你在那之后把所有事情都搞砸了，你也可以随时回来再试一次，而不必从头开始。

> Git 还有很多其他很棒的方面，但它的核心就是它的全部内容：在代码中创建保存点，如果需要，以后可以返回，即可以进行版本回退。

## Git 是如何工作的？
> 1、暂存操作：git add .

> 2、实际提交：git commit

## Git rebase 操作的黄金法则
> 不能在共同分享的分支上面进行rebase操作

> 所谓共享的分支，即是指那些存在于远端并且允许团队中的其他人进行Pull操作的分支。

## Git rebase 原理
> 本人的理解如下：git rebase 哪个分支，就是以哪个分支为基准分支，表示需要被操作的分支修改的point点是从rebase 这个分支最后一次提交记录开始改动的。

>  如果两条进行rebase 操作的分支中，经过对比存在相同的commit ID，会进行fast-forward快进操作，不会产生一个新的提交，而不同的commit ID 会更新到另外rebase分支上去

![](https://test-file.kfangcdn.com/test/0b74b6f8f9f643b3a56323a5567be672.png)

> 如上图有两个分支，一条master分支,一条iss53 分支，很明显我们看到两条分支有共同的提交记录C0、C1、C2,3条记录，所以在rebase 过程中这3条记录会进行fast-forward快进操作，但是我们发现iss53分支比master 分支落后一条记录C4,如果我们想把iss53分支合并到master分支上，怎么操作呢？

> 1、我们可以把iss53 分支同步到最新的master提交记录，git rebase master ,那么发现iss53分支记录变成了最新的C0=>C1=>C2=>C4=>C3=>C5,master分支记录为：C0=>C1=>C2=>C4

>2、切到master分支，git rebase iss53 分支，对比发现，C0=>C1=>C2=>C4,这4条提交记录的commit ID是一样的，直接进行fast-forward快进操作,最后只有C3=>C5 这2条记录commit ID ，更新到 master 分支上去



## Git rebase 操作命令
> git rebase --continue，rebase操作中解决完冲突，git add . => git rebase --continue

> git rebase --abort ，取消当前的rebase操作

## demo rebase 分支步骤

> 一条 v1 分支，一条 v2 分支

> 1、新建一条分支：test-serve

> 2、先切到 test-serve 分支，rebase v1 分支

> 3、再切到 v2 分支，rebase test-serve 分支

> 4、再切到 test-serve 分支， rebase v2 分支

> 5、完成 最后的结果是：v1=>v2=>test-serve
