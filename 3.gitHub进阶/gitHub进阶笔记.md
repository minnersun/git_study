## gitHub进阶笔记

---

### 图形界面工具

> Git GUI
>
> Source Tree
>
> EGit
>
> > 这三个图形界面，自己拓展



### .gitignore

#### 使用场合

> 1.忽略操作系统自动生成的文件
>
> > 比如：缩略图等
>
> 2.忽略编译生成的中间文件、可执行文件等
>
> > 比如：c语言编译产生的.obj文件和.exe文件；
>
> 3.忽略自己带有敏感信息的配置文件
>
> > 比如：存放口令的配置文件
>
> 4.tmp/	临时文件
>
> 5.log/	日志文件
>
> 等等

#### 如何使用

##### 创建.gitignore文件

> 在Git Bash命令模式中，使用**vim**创建一个名为**`.gitignore`**的文件
>
> **每一行**即表明要忽略版本控制的一个/类文件
>
> > 支持**通配符**的使用

##### 查看是哪条规则忽略了某一文件

> `git check-ignore -v project.txt`

##### 将.gitignore忽略的文件加入控制

> `git add -f 文件名`
>
> > `git add -f project.txt`

> 注
>
> > `.gitignore`中每一行的文件会被自动忽略
> >
> > `.gitignore`文件本身默认不跟踪
> >
> > > `git status` `.gitignore`文件显示为红色

###### 案例

.gitignore

```
# 忽略ignoretest文件/目录
ignoretest
# 忽略project.txt文件
project.txt
```



##### github提供的模板

> 新建仓库 --> Add .gitignore:None --> 选择对应的模板

> GitHub官方托管的gitignore仓库
>
> > `https://github.com/github/gitignore`



### 换行处理

> CR：carriage return回车，光标移到首行
>
> > '\r' = return
>
> LF：line feed换行，光标下移一行
>
> > ‘\n’ = newline

##### linux换行

> `\n`

##### windows换行

> `\r\n`

##### MAC OS换行

> `\r`

##### 配置

> `git config --global core.autocrlf true`
>
> > 提交时转换为LF，检出时转为`CRLF`
> >
> > **默认设置不用修改**
>
> `git config --global core.safecrlf false`
>
> > 允许提交时包含混合换行符的文件
> >
> > > 添加之后关于**换行的警告消失**
> >
> > > 输入 `git config -l`
> > >
> > > > 发现配置中多了`core.safecrlf=false`



### 别名

#### 以图形的方式打印Git提交的日志

> > `git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short`
> >
> > > %h：hash值
> > >
> > > %ad：提交commat信息
> > >
> > > %s%d：提交日期
> > >
> > > [%an]：提交人
> > >
> > > --graph：以图形化的方式显示
> > >
> > > --data=short：以短日期的方式显示

#### 设置别名

##### git别名配置文件

> `cd`
>
> > 进入到git的主目录
>
> `ls -l -a`
>
> > 查看文件，`.gitconfig`文件存储
>
> 所有别名可以在`.gitconfig`文件中查看

###### .gitconfig

```
[user]
        name = wangxinhui
        email = 1076710856@qq.com
[core]
        safecrlf = false
[alias]
        mylog = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
```



### 凭证

##### https协议凭证

> 存储凭证
>
> > `git config --global credential.helper wincred`
> >
> > > wincred：会将第一次输入的用户名密码存起来，之后提交就不会再提示我们输入用户名和密码
> >
> > > 可在`~/.gitconfig`文件中查看配置



### Git协议

#### 本地协议（一般不使用）

##### 克隆本地仓库

> `git clone /c/wd/test.git`
>
> > 克隆本地仓库
>
> `git clone file:///c/wd/test.git`
>
> > 克隆本地仓库，不建议使用file://
> >
> > > 添加了file之后，所有的操作都是通过**协议栈**的方式来做协议的传输，相对而言比较慢
>
> 添加远程仓库的链接
>
> > `git remote add origin /c/wd/test.git`

###### 缺点

> 没有网络，无法在互联网中访问



#### Git协议（速度最快）

> `git clone git://setver_ip/test.git`
>
> > 克隆远程仓库
>
> `git remote add origin git://server_ip/test.git`
>
> > 添加远程仓库的链接 

###### 缺点

> 权限要么对所有人开放，要么对所有人不开放



#### HTTP协议（主流）

> `git clone https://github.com/minnersun/git_study`
>
> > 克隆远程仓库
>
> `git remote add origin https://github.com/minnersun/git_study`
>
> > 添加远程仓库链接

###### 缺点

> HTTP协议传输效率比较低
>
> > HTTP为超文本传输协议，需要对数据进行压缩，解压

> 从安全性角度来讲，和SSH协议差不多
>
> > 不适用存储凭证，需要输入用户名和密码



#### SSH协议(重点)

##### 生成密钥对

> `ssh-Keygen -t rsa -C "your email"`
>
> > rsa：加密算法
> >
> > your email：github注册使用的email地址
>
> 案例
>
> > `ssh-Keygen -t rsa -C "1076710856@qq.com"`
> >
> > > 将密钥对存储到默认位置即可，全部默认下一步
>
> 位置
>
> > `cd ~`
> >
> > `cd .ssh`
> >
> > > `id_rsa`
> > >
> > > > 私钥
> > >
> > > `id_rsa.pub`
> > >
> > > > 公钥
> >
> > > `cat id_rsa.pub`
> > >
> > > > 将公钥打印出来，复制

##### github配置公钥

> 点击右侧头像 --> Settings --> SSH and GPG keys --> New SSH key
>
> > Title
> >
> > > 给公钥起一个名字
> >
> > Key
> >
> > > 粘贴复制的公钥

> 配置完成之后即可用SSH协议对远程仓库进行操作



##### SSH方式克隆远程仓库

> `git clone ssh://@github.com/minnersun/git_study`
>
> `git clone git@github.com:minnersun/git_study`
>
> > 克隆远程仓库，一般写成简短的命令
> >
> > > 如果存在删除原有数据源
> > >
> > > > `git remote rm origin`

##### SSH方式添加远程仓库

> `git remote add origin git@github.com:wangding/test.git`
>
> > 添加远程仓库的链接



> 