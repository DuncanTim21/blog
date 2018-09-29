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
其实`ruby`在当前的环境下不是很流行.在排行上也早已不是主流(py是世界上最好的语言!),但是和node一样,做一些简单的增删改查还是比较简单的,而且框架路由比较清晰,但是不可避免的代码冗余,重复.
```
moment("20111031", "YYYYMMDD").fromNow(); // 7 年前
moment("20120620", "YYYYMMDD").fromNow(); // 6 年前
moment().startOf('day').fromNow();        // 17 小时前
moment().endOf('day').fromNow();          // 7 小时内
moment().startOf('hour').fromNow();       // 39 分钟前
```
### 日历时间
```
moment().subtract(10, 'days').calendar(); // 2018年4月22日
moment().subtract(6, 'days').calendar();  // 上周四下午4点40
moment().subtract(3, 'days').calendar();  // 上周日下午4点40
moment().subtract(1, 'days').calendar();  // 昨天下午4点40分
moment().calendar();                      // 今天下午4点40分
moment().add(1, 'days').calendar();       // 明天下午4点40分
moment().add(3, 'days').calendar();       // 本周六下午4点40
moment().add(10, 'days').calendar();      // 2018年5月12日
```

### 多语言支持
```
moment().format('L');    // 2018-05-02
moment().format('l');    // 2018-05-02
moment().format('LL');   // 2018年5月2日
moment().format('ll');   // 2018年5月2日
moment().format('LLL');  // 2018年5月2日下午4点40分
moment().format('lll');  // 2018年5月2日下午4点40分
moment().format('LLLL'); // 2018年5月2日星期三下午4点40分
moment().format('llll'); // 2018年5月2日星期三下午4点40分
```

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