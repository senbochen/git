# rebase 合并分支

## demo

### 一、 rebase 分支步骤

> 一条 v1 分支，一条 v2 分支

> 1、新建一条分支：test-serve

> 2、先切到 v1 分支，rebase test-serve 分支

> 3、再切到 v2 分支，rebase test-serve 分支

> 4、再切到 test-serve 分支， rebase v2 分支

> 5、完成 最后的结果是：v1=>v2=>test-serve
