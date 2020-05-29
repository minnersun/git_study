## git团队协作

----

### 邀请参加开源项目

##### 步骤

> 邀请人
>
> > 登录Github --> 进入仓库 --> Settings --> Manage access
>
> 被邀请人
>
> > 登录Github
> >
> > > 查看消息，接收邀请
> >
> > > 打开邀请网址，接收邀请



### 集中式工作流（最简单）

> 与`Subversion`的`trunk`相似
>
> `Git`叫做`master`，所有修改提交到`master`
>
> 该工作流只用到`master`这一个分支

##### 可能会出现的问题

###### 同一分支出现分叉

> 多人协作过程中，本地提交远程仓库（commit）之后，推到远程仓库（pull）之前，可能会出现分叉
>
> > 都有commit，出现不同的版本
>
> > 解决`git pull --rebase`
> >
> > > 使用rebase会将分叉合并为一条，这样就不会报错了

###### 多人修改同一文件

> 需要手动修改，确认版本



### 功能分支工作流

> 所有的功能开发应该在一个专门的分支，而不是在master分支上
>
> > 可以方便多个开发者在各自功能上开发而不会弄乱主干代码
> >
> > > 保证了master分支的代码一定不会是有问题的

##### pull request

> `pull request`
>
> > 能为每个分支发起一个讨论
> >
> > > 在功能分支并入主干之前，给其他开发者审核代码的机会
> >
> > > 如果你在功能开发中遇到问题卡住了，也可以开一个`pull request`来向其他小伙伴征求建议

##### 工作方式

> 功能分支工作流仍然用中央仓库，并且`master`分支还代表了正式项目的历史
>
> > 不直接提交本地变更到master分支
> >
> > > 开发者每次在开始新功能前线创建一个新分支
> > >
> > > > 功能分支应该有个描述性的名字
> > > >
> > > > > 如
> > > > >
> > > > > > `animated-menu-items`
> > > > > >
> > > > > > `issue-#1061`
>
> 分支内容可以push到中央仓库

##### 案例分析

> `minnersun`
>
> > `(master)git checkout -b feat-dialog`
> >
> > `touch c`
> >
> > > `echo 1111 >> c`
> > >
> > > `echo 2222 >> c`
> >
> > `git commit -am "edit c"`
> >
> > `git push origin feat-dialog`
> >
> > > `echo 3333 >> c`
> >
> > `git commit -am "finish the feature dialog"`
> >
> >  `git push -u origin feat-dialog`
>
> `mytest-2`
>
> > `minnersun`提交后，`mytest-2`登录系统
> >
> > > 打开到对应的仓库，可以看到`Comparable`和`Pull request`按钮
> >
> > 点击`Pull request`
> >
> > > 可以输入信息进行讨论
>
> `minnersun`
>
> > 登录仓库	-->  `Pull request` --> Files changed
> >
> > > 查看代码的变化，可以点击`+`，提bug
> >
> > 点击`Comversation`
> >
> > > 确认是否提交或者合并代码