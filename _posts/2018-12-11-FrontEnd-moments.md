---
layout: post
title: 日期时间的问题处理
tags: [Front-End]
---


**摘要：** 大家在前端Javascript开发中会遇到处理日期时间的问题，经常会拿来一大堆处理函数才能完成一个简单的日期时间显示效果。在之前的文章中我是用工具类`[moment.js]`进行处理,但是一些需求,终归还是要自己来造一些轮子.在这里简单的总结一下一些基础的Date()方法,和时间格式的操作.


### 获取日期

```
var myDate = new Date();                       //获取系统当前时间
```


```
1 myDate.getYear();                         //获取当前年份(2位)
2 myDate.getFullYear();                     //获取完整的年份(4位,1970-????)
3 myDate.getMonth();                        //获取当前月份(0-11,0代表1月)
4 myDate.getDate();                         //获取当前日(1-31)
5 myDate.getDay();                          //获取当前星期X(0-6,0代表星期天)
6 myDate.getTime();                         //获取当前时间(从1970.1.1开始的毫秒数) => 1542789110559
7 myDate.getHours();                        //获取当前小时数(0-23)
8 myDate.getMinutes();                      //获取当前分钟数(0-59)
9 myDate.getSeconds();                      //获取当前秒数(0-59)
10 myDate.getMilliseconds();                //获取当前毫秒数(0-999)
11 myDate.toLocaleDateString();             //获取当前日期 => "2018/11/21"
12 var mytime=myDate.toLocaleTimeString();  //获取当前时间 => "下午4:31:50"
13 myDate.toLocaleString( );                //获取日期与时间 => 2018/11/21 下午4:31:50"
//获取时间前10条返回类型均为number;
```

### 获取时间戳

```
1. var timestamp =Date.parse(new Date());   // 1542789110000
2. var timestamp =(new Date()).valueOf();   // 1542789110559
3. var timestamp=new Date().getTime()；     // 1542789110559
```

> 注意 : **第一种方法得到的结果将后三位（毫秒）转换成了000显示，使用时可能会出现问题.** 这也就解释了我做highchart时,后台返回时间与需要判断时间做匹配时出现错误的问题,因为精度的原因,~~ `==` 在这里是无法使用的~~,所以对于一些细节的问题,可能导致方法的失败,仍需不断总结.
 
* 对于日期格式我们要时刻注意时区的问题,不管是前端还是后端处理数据!!!


### 日期格式化


```
**************************************时间格式化处理************************************
function dateFormat(fmt,date)   
{ //author: meizz   
  var o = {   
    "M+" : date.getMonth()+1,                 //月份   
    "d+" : date.getDate(),                    //日   
    "h+" : date.getHours(),                   //小时   
    "m+" : date.getMinutes(),                 //分   
    "s+" : date.getSeconds(),                 //秒   
    "q+" : Math.floor((date.getMonth()+3)/3), //季度   
    "S"  : date.getMilliseconds()             //毫秒   
  };   
  if(/(y+)/.test(fmt))   
    fmt=fmt.replace(RegExp.$1, (date.getFullYear()+"").substr(4 - RegExp.$1.length));   
    // RegExp.$1 为匹配的第一个字符 
  for(var k in o)   
    if(new RegExp("("+ k +")").test(fmt))   
  fmt = fmt.replace(RegExp.$1, (RegExp.$1.length==1) ? (o[k]) : (("00"+ o[k]).substr((""+ o[k]).length)));   
  return fmt;   
}
```
---

```
var crtTime = new Date();
return dateFormat("yyyy-MM-dd hh:mm:ss",crtTime);  => '2018-11-21 16:31:50'
//这是一个比较经典的时间格式化函数,在平时的使用中我可能用拼字符串比较多,
而不是写一个公共方法,不过这种思维方式要在之后的工作学习中慢慢转变.
```

### 字符后添加 '.00' 增加精度

```
        var getFloatStr = function (num) {
            num += '';
            num = num.replace(/[^0-9|\.]/g, '');

            if (/^0+/)
                num = num.replace(/^0+/, '');
            if (!/\./.test(num))
                num += '.00';
            if (/^\./.test(num))
                num = '0' + num;
            num += '00';
            num = num.match(/\d+\.\d{2}/)[0];
            return num;
        };
```

---
> 本来是写一些关于时间的公共函数,但是写了几个总觉得易用性,适配性和鲁棒性都特别差,最后还是不放上来献丑了,其实上面的方法已经完全够工作中的使用,更不要提还有`moment.js`这样强大的工具集,写过一次也就有了思路,再把握好函数中一些该注意的点,将不会有任何问题!