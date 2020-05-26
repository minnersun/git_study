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



### gitignore和换行符

#### .gitignore

##### 使用场合

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

##### 如何使用

###### 创建.gitignore文件

> 在Git Bash命令模式中，使用**vim**创建一个名为**`.gitignore`**的文件
>
> **每一行**即表明要忽略版本控制的一个/类文件
>
> > 支持**通配符**的使用



###### 查看是哪条规则忽略了某一文件

> `git check-ignore -v project.txt`



###### 将.gitignore忽略的文件加入控制

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



#### 换行

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

