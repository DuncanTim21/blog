---
layout: post
title: Moment.js的使用及总结
tags: [Dev-Tool]
---

**摘要：**大家在前端Javascript开发中会遇到处理日期时间的问题，经常会拿来一大堆处理函数才能完成一个简单的日期时间显示效果。而我经常使用的就是这款工具：moment.js，使用它可以轻松解决前端开发中遇到的种种日期时间问题。
{:.message}

> moment.js不依赖任何第三方库，支持字符串、Date、时间戳以及数组等格式，可以像PHP的date()函数一样，格式化日期时间，计算相对时间，获取特定时间后的日期时间等等，本文有如下举例。

### 日期格式化

```moment().format('MMMM Do YYYY, h:mm:ss a'); // 四月 28日 2018, 4:05:15 下午
moment().format('dddd');                    // 星期六
moment().format("MMM Do YY");               // 4月 28日 18
moment().format('YYYY [escaped] YYYY');     // 2018 escaped 2018
moment().format();                          // 2018-04-28T16:05:15+08:00```