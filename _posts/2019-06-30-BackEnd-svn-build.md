---
layout: post
title: SVN在服务器的搭建与使用
tags: [Back-End]
---

**摘要：**之前的公司进行代码管理多是用svn与git进行管理,但是我作为开发者,只是会使用,这次公司需求在服务器上部署一个办公室内部的SVN服务器,也刚好练习了VI命令.
{:.message}


6888
### 1.项目使用
#### 1.1 启动项目
进入rails服务所在文件夹(/liucc/liujiawen/omm3.2下服务器)

>==注意! 若缓存已经存在 则== `rm /.../**.log` ==文件==

>```rails s -b172.16.1.113 -p2121```(b=>服务器地址,p=>端口号地址)


>更新controller时不需要重启,更新config文件下需要更新 

### 2. 项目后台学习

#### 2.1 关于ruby及ruby on rails
>*Ruby 是一种开源的面向对象程序设计的服务器端脚本语言,Ruby 可运行于多种平台，如 Windows、MAC OS 和 UNIX 的各种版本。Rails 是一个基于 MVC 模式的高效的开发框架。*
 
#### 2.2 ruby的安装与rails的搭建

在之前的文章(github pages的搭建)中已经使用过`jekyll`,而使用`jekyll`需要搭建过ruby环境及rails,本文就不再详细概述这样的问题.

>`rails new 'demo' rails s`启动项目
如果看到3000端口启动这样的页面,则启动成功

![rails](/blog/assets/img/docs/How-Browsers-Work/rails.png)

但是这里可以提出 我们通过命令更改`gem`包地址提高开发效率

```
$ gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
$ gem sources -l
```

```
常见问题

Q: gem install xxx 的时候遇到错误信息包含：“Error fetching data: Errno::ETIMEDOUT: Operation timed out - connect(2)”

A: 网络问题导致请求淘宝服务器被连接重置了，在遇到此类情况的时候，你可以尝试换一台机器或网络尝试安装，看是否还有同样的问题，以确定是淘宝镜像服务器的问题还是你的环境问题。
```

#### 2.3 Rails 中的视图
上面说到了*Rails 是一个基于 MVC 模式的高效的开发框架*,所以为了快速开发和高效学习,我们将基于MVC三大部分来学习rails框架.

视图（View）即 MVC 中的 V，也是Rails使用者最先见到的部分。在我们的项目中,我们可以进入到`app/views`这个文件夹.

`layouts` 里放的是布局文件。如果我们网站只有一种布局，那么一个 `application.html.erb` 就足够了。我们也可以为每个资源创建一个 `layout`，比如 `app/views/layouts/products.html.erb`

>`<%= yield(:page_stylesheet) if content_for?(:page_stylesheet) %>`

这行代码中的`content_for`可以在这个layout 的这个位置，显示额外的内容,这样给我们的代码里增加了一些灵活，也不必把所有内容都写到一起。

**待学习整理**

#### 2.4  Rails 中的模型

>模型（Model）是 MVC 架构中的 M，代表数据库，通过对模型的学习，可以了解 Rails 是如何实现数据库操作的.

##### 2.4.1  Active Record 简介
`Active Record `是默认与数据库进行交互的代码库,它提供了一系列对象,来对数据对象进行增删改查(*CRUD*)操作.本地项目使用`Mysql`数据库.
 >命名约定
 - 数据表名：复数，下划线分隔单词（例如 book_clubs）
- 模型类名：单数，每个单词的首字母大写（例如 BookClub）

---
###### 生成用户模型

```
rails generate model User name:string email:string
```
app/models/user.rb 结果如下 
```
class User < ActiveRecord::Base
end
```
我们创建一个 model 的时候，会自动创建它的 migration 文件，我们还可以使用 `rails g migration XXX`的方法，添加自定义的迁移文件。比如我为 variant 添加一个color 字段.

```
rails g migration AddColorToVariants color:string
```
---
这里我们先忽略迁移文件,专注到model上来,首先我们探索数据模型,我们的工具是Rails控制台.
1. 首先`rails c`进入控制台
2. 直接创建用户对象
```
user.new
=> #<User id: nil, name: nil, email: nil, created_at: nil, updated_at: nil>
```
3. 为`User.new`指定参数
```
user = User.new(name: "Michael Hartl", email: "mhartl@example.com")
=> #<User id: nil, name: "Michael Hartl", email: "mhartl@example.com", created_at: nil, updated_at: nil>
```
这里`new`方法只是创建对象,并没有在数据库改变数据,这里我们需要save方法
4. 保存数据库
```
user.save
=>true
```
---
通过save方法,我们打出`user`可以看到
>`#<User id: 1, name: "Michael Hartl", email: "mhartl@example.com", created_at: "2018-04-12 08:11:31", updated_at: "2018-04-12 08:11:31">`

同时我们也可以通过.方法获取属性`uesr.name=>"Michael Hartl"`

但是我们要了解的是,我们一般通过`User.create`方法使两步合一步
```
User.create(name: "A Nother", email: "another@example.org")
=>#<User id: 2, name: "A Nother", email: "another@example.org", created_at:
"2013-03-11 01:05:24", updated_at: "2013-03-11 01:05:24">
// 我们可以通过赋值给变量来直接操作
foo = User.create(name: "Foo", email: "foo@bar.com")
```

销毁对象使用`User.destroy`可以直接使用`foo.destroy`

---
###### **查找用户对象**
Active Record为我们提供了很多查找对象方法,我们先来看看,

1. `User.find(1)`这个命令很明显;我们查找一个不存在的的id呢?

```
>> User.find(3)
=> #ActiveRecord::RecordNotFound: Couldn't find User with ID=3
```
2. `find_by_name`可以通过属性查找记录,通过Hash形式传入
```
>> User.find_by(email: "mhartl@example.com")
=> #<User id: 1, name: "Michael Hartl", email: "mhartl@example.com",
created_at: "2013-03-11 00:57:46", updated_at: "2013-03-11 00:57:46">
```
3. `User.first`返回第一个
4. `User.all` 返回所有

---
##### 更新用户对象
我们这里列出一个常用方法,即`update_attributes`
```
user.update_attributes(name: "The Dude", email: "dude@abides.org")
=>true
```
---
---
##### 2.4.1  用户数据验证
>**验证数据格式,并用来显示一些有用的提示信息**


但是这边的项目中,我们并没有使用其中的测试框架,所以这部分在这次的学习中,将直接跳过,但是这里做次**记录**,以方便后面复习的时候进行查漏补缺!

---

下面的内容将尽可能参考**Ruby on Rails.pdf**一书,这本书作为rails上手学习再适合不过

在上面的例子中 , 我们已经创建了`User`模型,接下来要实现一个更加进阶的例子,也是本书着重介绍的例子,**用户注册**!

