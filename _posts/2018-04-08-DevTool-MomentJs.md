---
layout: post
title: Moment.js的使用及总结
tags: [Dev-Tool]
---

**摘要：**大家在前端Javascript开发中会遇到处理日期时间的问题，经常会拿来一大堆处理函数才能完成一个简单的日期时间显示效果。而我经常使用的就是这款工具：[moment.js](http://momentjs.cn/)，使用它可以轻松解决前端开发中遇到的种种日期时间问题。
{:.message}

> [moment.js](http://momentjs.cn/docs/)不依赖任何第三方库，支持字符串、Date、时间戳以及数组等格式，可以像PHP的date()函数一样，格式化日期时间，计算相对时间，获取特定时间后的日期时间等等，本文有如下举例。

### 日期格式化

```
moment().format('MMMM Do YYYY, h:mm:ss a'); // 四月 28日 2018, 4:05:15 下午
moment().format('dddd');                    // 星期六
moment().format("MMM Do YY");               // 4月 28日 18
moment().format('YYYY [escaped] YYYY');     // 2018 escaped 2018
moment().format();                          // 2018-04-28T16:05:15+08:00
```

### 相对时间

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

> `moment().add(7, 'd');`

未完成!dddddddsda asdasd as
