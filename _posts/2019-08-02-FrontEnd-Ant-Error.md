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

官方给出了`mapPropsToFields	`方法作为解决方案,

> 把父组件的属性映射到表单项上（如：把 Redux store 中的值读出），需要对返回值中的表单域数据用 `Form.createFormField` 标记

但是我们的需求需要不断传值来更改`Modal`中的内容,而不是一次的渲染,这个方法就无法实现我们的需求.

所以改用`componentWillReceiveProps + setFieldsValue`!是我们不可避免要踩的一个坑.


如何避免setFieldsValue和 react生命周期方法发生的互撕行为呢?我们不由的就想到了**节流阀**,我们万能的**Flag**!!

```js
componentWillReceiveProps(nextProps){
    const {a} = nextProps;
    const {setFieldsValue} = nextProps.form;
    if (this.state.flag) {
        ......(your code)
        setFieldsValue(a);
        this.setState({
        flag: false,
        })
    }
}
```

这个逻辑确实可以很好的解决我们死循环的一些根本问题,但是在实际的项目中,我的默认值只会渲染一次,重新另一个编辑按钮,`Modal`的默认值就不会再次更改.而我其实也有偷懒的做法,将`Modal`的`key`绑定为`{math.random}`,这样做的作用是我们在点击编辑按钮时,每次打开的都是一个新的模态框,很明显在用户点击多个模态框后,页面的性能会大大降低,可以实现,但是我们不提倡这样做,所以我们要在这个逻辑的基础上提出新的方案.

```js
componentWillReceiveProps (nextProps) {
if (!isEqual(this.props.defaultValues, nextProps.defaultValues)) {
    this.props.form.setFieldsValue(nextProps.defaultValues)
    }
}
```
我们可以抓住recat中**this.props**与**nextProps**的关系来入手,当我们判断到前后两次传回的值相同后,再用`setFieldsValue`来修改表单的内容,这样即不会损害页面性能,也完美的避免了生命周期方法发生的互撕行为,完成了项目的需求.

![效果1](/blog/assets/img/docs/Ant-work/ant1.png)
![效果2](/blog/assets/img/docs/Ant-work/ant2.png)

