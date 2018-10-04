---
layout: post
title: IDE运维平台功能及其技术介绍
tags: [Dev-Tool]
---

**摘要：**这个月因为家事,已经好久没有更新过技术博客了,既然要重新开始,过去也不能遗忘,而上一份工作的经历必然是不可避免要提到的,这篇的内容将详细的描述上份工作中的工作内容,及工作技术问题.
{:.message}

这份工作对我来说其实是一次新的尝试,之前在广州这边,工作内容全部都是前端的,这期间也慢慢熟悉了前端的很多技术点和框架,在不可避免的回到西安之后,老同学为我提供了一个接近于全栈的工作岗位机会。而要用到的技术框架,`React`下的`AntDesign`搭配`rails`进行开发西安银行IDE运营门户.这些技术是我之前完全没有接触到的,就这样在西安,我又重新上路!!

### 工作基本内容
`IDE运营门户`面向的是西安银行运维部门搭建的门户网站,甲方需要将之前的一些老的运维门户重新制作,并将一些平台的接口全部接入这个平台上,做到统一高效的运维平台.而因为甲方工作地点的原因,我们的团队也不可避免的被外派到银行这边,平台的前身是使用了`ruby on rails`+`HTML`这样的前后端技术, 而需求是在原有的后台代码之上,采用`MVVM`的工作模式,编写新的后台接口,并接入新的前端平台之上.

这里我将介绍一下我们用到的核心框架及技术. 



### ruby on rails
这个后端语言我在学习的时候在另一篇文章上有过简单的介绍,这次在大量的学习和使用后,有了不同的见解和心得.

其实`ruby`在当前的环境下不是很流行.在排行上也早已不是主流(py是世界上最好的语言!),但是和node一样,做一些简单的增删改查还是比较简单的,而且框架路由比较清晰,但是不可避免的代码冗余,重复.既然我们要将平台作为一个产品,代码的规范性和可读性就成为了主要的要求.

如果对`ruby`语言还有疑惑,可以翻看我的前一篇文章,这里我们不多做阐述.


### AntDesign
```
提炼自企业级中后台产品的交互语言和视觉风格。

开箱即用的高质量 React 组件。

使用 TypeScript 构建，提供完整的类型定义文件。

全链路开发和设计工具体系。
```

这次平台框架是使用了我不太熟悉的以React为基础的框架,之前对于Vue比较熟悉,都是MVVM的模式,上手也比较快,一些其他额区别,在文档中可以很快熟悉.

对于基础的AntD ,我们做了一些自己的修改和封装,包括一些请求的时机和判断.

![特色](/blog/assets/img/docs/Ant-work/ant3.png)




### IDE功能

平台作为运维部门的门户平台,当然要将各个平台的功能集中展示,并代替各个平台的一些主要功能,再做到产品封装.

![发布](/blog/assets/img/docs/Ant-work/发布.PNG)

![告警](/blog/assets/img/docs/Ant-work/告警.PNG)

![表格](/blog/assets/img/docs/Ant-work/表格.PNG)

![配置页面](/blog/assets/img/docs/Ant-work/配置页面.PNG)


![特色](/blog/assets/img/docs/Ant-work/ant1.png)

![特色](/blog/assets/img/docs/Ant-work/ant2.png)





#### 日期对象 
可以`Moment`使用预先存在的本地`JavaScript Date`对象创建一个。
```
var day = new Date(2011, 9, 16);
var dayWrapper = moment(day);
```
这克隆了`Date`对象; 进一步的改变`Date`不会影响到`Moment`，反之亦然。

#### 当前时间 
获取当前日期和时间，只需调用`moment()`不带参数
```
var now = moment();
```

#### 字符串+格式 

> moment(String, String);
> 
> moment(String, String, String);
> 
> moment(String, String, Boolean);
> 
> moment(String, String, String, Boolean);

`moment("12-25-1995", "MM-DD-YYYY");`

解析器会忽略非字母数字字符，因此以下两者都会返回相同的内容
```
moment("12-25-1995", "MM-DD-YYYY");
moment("12/25/1995", "MM-DD-YYYY");
```

#### 加法
> moment().add(Number, String);
> 
> moment().add(Duration);
> 
> moment().add(Object);

通过增加时间来改变原始时刻。

这是一个非常强大的功能，可以将时间添加到现有时刻。要添加时间，请传递您想要添加的时间以及要添加的类型。

> 
`moment().add(7, 'days');`

如果你喜欢整个简洁的东西，还有一些速记键.

<<<<<<< HEAD
> `moment().add(7, 'd');`

未完成!!!!al