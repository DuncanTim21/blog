---
layout: post
title: Ant-Design-pro中Form.setFieldsValue方法进入死循环
tags: [Front-End]
---

**摘要：**在页面的制作中,出现了点击编辑按钮,出现model模态框来进行编辑的功能,而在Ant中就需要Form.setFieldsValue方法来对表单进行默认值的设置,[Form](https://ant.design/components/form-cn/).
但是在使用中却出现了死循环.
{:.message}




### 环境
我是在Ant-Design框架下进行,由于考虑代码的简洁性与可复用性以及后面的可读性.我将模态框内容单独抽离成为一个独立的组件,由this.props来向子组件传递需要渲染表单的内容,但是在另一个组件的生命周期函数中`componentWillReceiveProps`用了`nextProps`来接收传递的对象,之后调用`Form.setFieldsValue`方法,却出现了死循环.


### 原因
在仔细阅读Ant文档后,我找到了这样的解释.
> 设置一组输入控件的值（注意：不要在 componentWillReceiveProps 内使用，否则会导致死循环）

看起来并不是自己的逻辑出现了问题,再去了解一下Ant和react生命周期的一些底层原理.我可以基本清楚:

> `setFieldsValue` 本质是调用外层 wrapper 的 `setState`，间接调用`componentWillReceiveProps`，所以死循环了。

因此针对上面出现的原因我们可以得出如下几个解决方案:

### 解决方案

66