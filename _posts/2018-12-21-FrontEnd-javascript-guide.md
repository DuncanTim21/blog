---
layout: post
title: JS 编码规范
tags: [Front-End]
---

# JS 编码规范

> 参考链接：[JavaScript Standard Style](https://standardjs.com/)

## 目录
* [缩进](#js-tab)
* [分号](#js-semicolon)
* [引号](#js-quote)
* [空格](#js-space)
* [空行](#js-space-line)
* [换行](#js-br)
* [注释](#js-comment)
* [变量](#js-variable)
* [其它](#js-other)

<a id="js-tab"></a>

## 缩进
使用 4 个空格做为一个缩进层级，不允许使用 Tab 缩进

<a id="js-semicolon"></a>

## 分号
需在后面加分号的情况：
* 变量声明
* 表达式(包括函数表达式)
* return
* throw
* break
* continue
* do-while

<a id="js-quote"></a>

## 引号
最外层统一使用单引号，单双引号交替使用。

<a id="js-space"></a>

## 空格
> 一般编辑器 Format 后会自动处理

* 不需要使用空格的情况
    * 对象的属性名后
    * 前缀一元运算符后
    * 后缀一元运算符前
    * 函数调用括号前
    * 无论是函数声明还是函数表达式，'('前不要空格
    * 数组的'['后和']'前
    * 对象的'{'后和'}'前
    * 运算符'('后和')'前

* 需要空格的情况
    * 二元运算符前后
    * 三元运算符 '? :' 前后
    * 代码块 '{' 前
    * 下列关键字前：else, while, catch, finally
    * 下列关键字后：if, else, for, while, do, switch, case, try, catch, finally, with, return, typeof
    * 单行注释 '//' 后（若单行注释和代码同行，则 '//' 前也需要），多行注释 '*' 后
    * 对象的属性值前
    * for 循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
    * 无论是函数声明还是函数表达式，'{' 前一定要有空格
    * 函数的参数之间

<a id="js-space-line"></a>

## 空行
需要空行的情况：
* 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
* 注释前（当注释在代码块的第一行时，则无需空行）
* 代码块后（在函数调用、数组、对象中则无需空行）

<a id="js-br"></a>

## 换行
* 不需要换行的情况
    * 关键字 else, catch, finally 后
    * 代码块 '{' 前

* 需要换行的情况
    * 代码块'{'后和'}'前
    * 变量赋值后

<a id="js-comment"></a>

## 注释
* 单行注释
    * 双斜线后，必须跟一个空格
    * 缩进与下一行代码保持一致

* 多行注释
    * 最少三行, '*'后跟一个空格
    * 使用范围
        * 难于理解的代码段
        * 可能存在错误的代码段
        * 浏览器特殊的 HACK 代码
        * 业务逻辑强相关的代码  

* 文档注释
    * 各类标签 @class, @file, @param, @return, 参考 [docblocker](https://github.com/Warin/Sublime/tree/master/DocBlockr) 、[jsdoc](http://usejsdoc.org/) 等插件，以便生成自动化文档
    * 建议在以下情况下使用：
        * 所有常量
        * 所有函数
        * 所有类

<a id="js-variable"></a>

## 变量
* 变量命名
    * 标准变量采用驼峰式命名规则
    * 'ID' 在变量名中全大写
    * 'URL' 在变量名中全大写
    * 'Android' 在变量名中大写第一个字母
    * 'iOS' 在变量名中小写第一个，大写后两个字母
    * 常量全大写，用下划线连接
    * 构造函数，大写第一个字母
    * jQuery/Zepto 对象必须以 '$' 开头命名

* 变量声明
    * 单个函数中的变量声明前置，用一个 var 声明
    * 使用 ES6 语法时，var/let/const 的使用
    * 采用***字面量***方式声明变量

* 函数
    * 立即执行函数外必须包一层括号
    * 不要给 inline function 命名
    * 注意函数提升

* 数组/对象
    * 对象属性名不需要加引号(JSON 对象属性名除外)
    * 对象缩进遵守缩进规则
    * 数组中不要存空元素

* Null
    * 适用场景
        * 初始化一个将来可能被赋值为对象的变量
        * 与已经初始化的变量做比较
        * 作为一个参数为对象的函数的调用传参
        * 作为一个返回对象的函数的返回值
    * 不适用场景
        * 不要用null来判断函数调用时有无传参
        * 不要与未初始化的变量做比较

* Undefined
    * 永远不要直接使用 undefined 进行变量判断
    * 使用 typeof 和字符串 'undefined' 对变量进行判断

```javascript
'undefined' === typeof a;
```

<a id="js-other"></a>

## 其它
* 不要在内置对象的原型上添加方法，如：Array, Date
* 不要先使用后声明变量
* 不要在同个作用域下声明同名变量
* 不要在一些不需要的地方加括号，如：delete (a.b)
* 不要使用未声明的变量
* 不要声明了变量却不使用
* 不要在应该做比较的地方做赋值
* 不要在提交的代码里出现debugger
* 不要在循环内部声明函数
* 不要出现空的代码块(空函数声明除外)
* 用'===', '!==' 代替 '==', '!='
* for-in里一定要有hasOwnProperty的判断
* 对上下文this的引用只能使用 'me', 'self'其中一个来命名
