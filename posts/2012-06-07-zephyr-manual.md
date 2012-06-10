---
layout: post
title: Zephyr 简要安装说明
date: 2012-06-07 14:02:11
category: zephyr
tags: 
---


==zephyr项目地址

目前项目托管在:

    https://github.com/youngtrips/zephyr


==安装Zephyr

Zephyr代码现在托管在github.com上, 你只需要在shell中执行:

    git clone https://github.com/youngtrips/zephyr.git


zephyr依赖python-mako, python-yaml, python-markdown等开发库, 在ubuntu中直接使用apt-get安装即可:

    apt-get install python-mako
    apt-get install python-markdown
    apt-get install python-yaml

别的linux发行版使用相应的包管理工具(如fedora的yum, archlinux的pacman, gentoo的emerge)安装这些依赖库,或者也可以从以下
网站下载源码安装(或者直接用pip安装)

1. [Mako](http://www.makotemplates.org)

2. [Markdown](http://pypi.python.org/pypi/Markdown)

3. [python-yaml](http://pyyaml.org/)

==创建博客

在shell执行命令, 例如:

    zephyr init /home/youngtrips/blog

zephyr会在blog_path中创建工作目录:

1. .zephyr: 存放配置文件config.py及html生成文件

2. posts: 存放你写的markdown格式博客文件的目录

3. pages: 存放自定义页面

==配置博客

打开博客目录下.zephyr/config.py编辑配置型项, 配置文件格式如下:

    # configuration
    # site configuration
    SITE = {
        'name': 'MindEden', # 博客名称
        'description': 'Somewhere to keep my iears', # 博客描述,目前尚未使用到
        'url': 'http://mindeden.com', # 博客地址
        'pagelimit': 10, # 分页限制
        'theme': 'default', # 当前主题
        'disqus_shortname': 'mindeden', # disqus评论功能配置
    }

    AUTHOR = {
        'name': 'Tuz', # 作者名称
        'email': 'youngtrips@gmail.com', # 邮件地址
    }

    # remote git repo list
    REPO = {
        #name: url
        'github': 'git@github.com:youngtrips/mindeden.git', # 博客git版本库url, 目前尚未支持
    }

    # remote rsync server list
    RSYNC = {
        #name: url
        'myvps': 'root@codedelight:/var/www/'  # 远程服务器rsync同步url
    }

    # 友情链接列表
    LINKS = {
        #title: url
        'python': 'http://www.python.org',
        'Fedoraproject': 'http://fedoraproject.org',
        'Tuz@github': 'https://github.com/youngtrips',
        'Kevinlynx' : 'http://codemacro.com',
    }

配置文件是python脚本,编辑时请注意python语法.


==新建日志

执行shell命令, 例如:

    zephyr newpost hello-world -t "Hello World" -p ~/blog

该命令执行后, zephyr会在~/blog/posts下新建一个 YYYY-MM-DD-hello-world.md的文件,你只需用熟悉的文本编辑器打开编辑即可.

日志文件内容格式与Jeklly/Octopress的类似, 目前可以用的文件头标签有:

1. layout 模板布局

2. title 页面显示的标题

3. date 创建日期时间

4. category 分类


==发布站点

在配置文件config.py中设置好rsync同步地址, 在博客工作目录根目录下执行以下命令:

    zephyr publish

==模板自定义

zephyr是支持模板自定义的, 目前只有一个default模板, 详细的模板制作文档稍候补上.


