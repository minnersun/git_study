## git笔记

----

### 设置git参数

> 显示当前的git配置
>
> > `git config --list`
>
> 设置提交仓库时的用户名信息
>
> > `git config --global user.name "wangxinhui"`
>
> 设置提交仓库时的邮箱信息
>
> > `git config --global user.email "1076710856@qq.com"`

注： 

> 如果设置了多个用户名则会报错
>
> > 报错信息
> >
> > > `error: cannot overwrite multiple values with a single value
> > > Use a regexp, --add or --replace-all to change user.name.`
>
> 解决方案
>
> > `git config --global --replace-all user.name "你的 git 的名称"`
> >
> > `git config --global --replace-all uesr.email "你的 git 的邮箱"`
>
> > 或者编辑
> >
> > > `vim .gitconfig`

### git概念

> `WorkSpace`: 工作区
>
> > 相当于工作的文件夹
>
> `index/stage`：暂存库
>
> `Repository`：仓库区(本地仓库)
>
> remote：远程仓库

### Git Bash命令

#### 本地仓库相关

##### 新建代码仓库

> `git init`
>
> > 再当前目录下新建一个git代码库

##### 下载一个项目和他的整个代码历史

> `git clone [url]`
>
> > 克隆的时候已经将关联关系建立好了
>
> > `url格式：`
> >
> > > `http://github.com/[username]/reposName`

##### 添加删除文件

> `git add [file1] [file2]`
>
> > 添加指定文件到暂存区
>
> `git rm [file1] [file2]`
>
> > 删除工作区文件，并且将这次删除放入暂存区

##### 改名文件，并将这个改名放入暂存区

> `git mv [file-origin] [file-renamed]`

##### 代码提交

> `git commit -m [message]`
>
> > 提交暂存区到仓库
>
> `git commit -a -m [message]`
>
> > 直接从工作区提交到仓库
> >
> > > 前提该文件已经有仓库中的历史版本

##### 查看信息

> `git status`
>
> > 显示变更信息
>
> `git log`
>
> `git log --oneline`
>
> > 显示当前分支的历史版本信息

##### 查看提交版本的详细信息

> `git show [版本号]`
>
> > 可查看变动文本的内容

##### 查看文件与上次提交时的差异

> `git diff`
>
> > 查看文件与上次提交时的差异



#### 远程仓库相关

##### 将github用户名添加到git配置中

> `git config --global user.username <USerNamE>`　
>
> > 　严格区分大小写

##### 同步远程仓库

> `git remote add [shortname] [url]`
>
> > 关联远程仓库，并命名
> >
> > > 例如
> > >
> > > > `git remote add origin https://github.com/minnersun/gitdemo`
> > > >
> > > > > 将`https://github.com/minnersun/gitdemo`起别名为origin，并将本地仓库关联到远程仓库
> >
> > > `git remote rm origin`
> > >
> > > > 删除原有数据源
> >
> > > `git remote -v`
> > >
> > > > 查看是否与远程仓库建立连接
>

##### 将本地文件推送到github上

> `git push [remote] [branch]`
>
> > 将本地的提交推送到远程仓库
> >
> > > 例如
> > >
> > > > `git push origin master`
> >
> > > 远程仓库的commit信息与本地仓库的`git log`查询结果一致
>

##### 将github项目下拉到本地

> `git pull [remote] [branch]`
>
> > 将远程仓库的提交下拉到本地
>
> > 例如
> >
> > > `git pull origin master`
> > >
> > > > 将远程master分支中的内容推拽到本地

##### 叉拼存储库（clone）

> 找你到需要的项目，点击右上方的fork按钮
>
> > 此时github账户中会出现一个副本
>
> 复制fork项目中的HTTP URL

> 在本地Clone Fork
>
> > `git clone <URLFROMGITHUB>`



#### 分支操作

##### 创建分支

> `git branch <BRANCHNAME>`
>
> > 分支名区分大小写

##### 进入分支处理

> `git checkout <BRANCHNAME>`









### 资料相关

##### 资料地址

> `https://github.com/wangding/courses/tree/master/github`

##### 官方学习地址

> `https://try.github.io/`

##### git-it学习

> 需要安装nodejs
>
> > 验证安装成功
> >
> > > 打开cmd ---> node -v
>
> 在cmd窗口输入
>
> > `npm install git-it -g`
> >
> > > `-g`：全局安装git-it包
>
> 在cmd中输入git-it即可开始练习