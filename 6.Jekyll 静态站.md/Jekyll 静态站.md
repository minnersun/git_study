### 快速上手

#### 1.环境准备

连接到linux虚拟机

安装git和vim

> `sudo yum install -y git vim`
>
> 安装成功后
>
> > `git --version`

配置git和vim的参数

> `git config --global --replace-all user.name "你的 git 的名称"`
>
> `git config --global --replace-all uesr.email "你的 git 的邮箱"`



#### 2.创建项目

在github上创建空仓库 jekyll-demo

在该仓库上启用github pages设置

在自己电脑上克隆该仓库



#### 3.创建配置文件

在项目的根目录下，建立一个名为`\_config.yml`的文本文件

> 目录结构为
>
> > `/jekyll_demo`
> >
> > > ` |-- _config.yml`

> `touch _config.yml`	-创建文件



#### 4.创建模板文件

在项目根目录下创建一个 `\_layouts`目录，用于存放模板文件

> 在该目录下，创建一个``default.html`文件，作为Blog的默认模板

> 目录结构变为
>
> > `/jekyll_demo`
> >
> > > ` |-- _config.yml`
> > >
> > > `|-- _layouts`
> > >
> > > > `|-- default.html`

> `mkdir _layouts`	创建目录
>
> `cd _layouts/`	进入目录
>
> `vim default.html`	创建模板文件
>
> > ```
> > <!DOCTYPE html>
> > <html lang="en">
> > <head>
> >     <meta charset="UTF-8">
> >     <title> {{ page.title }}</title>
> > </head>
> > 
> > <body>
> > 	{{ content }}
> > </body>
> > 
> > </html>
> > ```
> >
> > 



#### 5.创建文章

在项目根目录，创建一个`\_posts`目录，用于存放blog文章

> 目录结构变为
>
> > `/jekyll_demo`
> >
> > > ` |-- _config.yml`
> > >
> > > `|-- _layouts`
> > >
> > > > `|-- default.html`
> > >
> > > `|-- _posts`
> > >
> > > > `|-- 2021-01-23-hello-world.html`	博客文章命名规范：	年-月-日-文章名.html

> `mkdir _posts`	创建`_posts`文件夹
>
> `vim 2021-02-23-hello-world.md `	创建文章
>
> > ```
> > ---
> > layout: default							模板
> > title: hello,jeklly						标题
> > ---
> > <h2> {{ page.title }} </h2>
> > <p>my first blob</p>
> > ```



#### 6.创建首页

在项目根目录里创建一个index.html文件

> 目录结构变为
>
> > `/jekyll_demo`
> >
> > > ` |-- _config.yml`
> > >
> > > `|-- _layouts`
> > >
> > > > `|-- default.html`
> > >
> > > `|-- _posts`
> > >
> > > > `|-- 2021-01-23-hello-world.html`
> > >
> > > `index.html`

> `vim index.html `	创建首页
>
> > ```
> > ---
> > layout: default
> > title: wangxinhui's Blog
> > ---
> > <h2> {{ page.title }} </h2>
> > <p> new article list </p>
> > <ul>
> >     {% for post in site.posts %}
> > 	<li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }} </a></li>
> >    {% endfor %}
> > </ul>
> > ```



#### 7.发布内容

把所有内容加入本地git库

把本地git仓库的内容推送到远程仓库

通过浏览器访问这个博客



#### 8.指定域名

在GitHub网站上配置域名，使用新的域名访问博客系统

> 在settings中找到GitHub Pages进行配置
>
> > 配置成功后可根据指定的url访问





### 安装Jekyll环境

#### 1.安装必要工具

安装wget	从网上下载按装包

安装bzip2	解压缩的工具

> `yum install -y wget bzip2`



#### 2.安装ruby-install

> `wget -O ruby-install-0.8.1.tar.gz https://github.com/postmodern/ruby-install/archive/v0.8.1.tar.gz`	获取ruby-install按装包
>
> `tar -xzvf ruby-install-0.8.1.tar.gz`	解压
>
> `rm ruby-install-0.8.1.tar.gz`	删除压缩包

> `cd ruby-install-0.8.1/`	进入解压后的文件夹
>
> `make install` 
>
> > make：是编译的意思。就是把源码包编译成二进制可执行文件
> >
> > make install：是用来安装的，它也从Makefile中读取指令，安装到指定的位置
>
> `ruby-install --system ruby`	需要升级到**2.4以上版本**
>
> `gem install jekyll`	安装jekyll
>
> `gem install bundler`	下载bundler依赖

> `jekyll new blob`	使用jeklly创建博客
>
> > 此时该目录下多了一个blob的文件夹
>
> `cd blob/`	进入新建的blob目录



### Jekyll基本用法

#### 目录讲解

> 生成的目录讲解
>
> > `404.html`
> >
> > `about.md`
> >
> > `Gemfile`	
> >
> > `Gemfile.loc`
> >
> > `index.md`	网站首页
> >
> > `_config.yml`	配置文件
> >
> > `_drafts`	草稿
> >
> > > `|--test1.html`
> > >
> > > `|--test2.md`
> >
> > `_includes`	存放样式
> >
> > > `footer.html`
> > >
> > > `header.html`
> >
> > `_layouts`	网站模板，静态页面套到模板里成为网页
> >
> > > `default.html`
> > >
> > > `post.html`
> >
> > `_posts`	存放静态文件
> >
> > > `_posts`文件夹下的文章只能按照**年-月-日-文章名.后缀**命名
> >
> > `_site`	存放生成的网页
> >
> > > 运行**jekyll build**时会出现文件
> > >
> > > 静态文件**`_posts`**文件夹中的内容套用**`_layouts`**中的模板生成的网页存放在**`_site`**中

#### 运行jekyll

> `sudo firewall-cmd --permanent --add-port=4000/tcp`	打开防火墙4000端口
>
> > 如果出现`FirewallD is not running`则表示防火墙没有打开
> >
> > > `systemctl start firewalld`	打开防火墙
> > >
> > > `systemctl status firewalld`	查看防火墙状态
> > >
> > > `sudo firewall-cmd --reload`	重启防火墙
>
> `jekyll serve`	运行jekyll
>
> > 如果报有关webrick的错 - 执行 `bundle add webrick`指令即可
>
> `jekyll serve --host 172.24.63.255`	
>
> > 将其修改为与`ifconfig`中的ip一致即可
>
> 成功启动后在浏览器访问即可



### 编辑博客内容

具体可参照

> `https://jekyll.zcopy.site/docs/`

博客文章一般存放于`_posts`文件夹

> `cd post/`	进入post页面
>
> > `2021-02-24-welcome-to-jekyll.markdown`
> >
> > 自动生成文件的头部变量
> >
> > > **需要在其他创建的文件中添加**
> >
> > ```markdown
> > ---
> > layout: post										表示网站使用的模板样式
> > title:  "Welcome to Jekyll!"						 文章的标题
> > date:   2021-02-24 16:38:02 +0800					  文章创建的时间
> > categories: jekyll update							 url中的显示路径
> > ---
> > ```

 

### 编辑样式

具体可参照

> `https://jekyll.zcopy.site/docs/`

需要手动上传主题到GitHub上

> `bundle show minima`	查看主题所在位置
>
> `cp -r /usr/local/lib/ruby/gems/3.0.0/gems/minima-2.5.1/* .`	将主题拷贝到jekyll创建的blob目录下
>
> > 成功拷贝后在blob目录下会出现`_layouts`文件夹等内容

#### 下载主题

> `http://jekyllthemes.org/`

#### 配置主题

> `Gemfile`
>
> > 添加
> >
> > > `gem 主题名`
>
> `_config.yml`
>
> > 修改
> >
> > > `theme: 主题名`
>
> 安装主题
>
> > 执行
> >
> > > `bundle install`
> > >
> > > > 自动找到并下载相关主题
>
> 将新主题重新拷贝到目录下



