---
layout: post
title: 总结
tags: [Front-End]
---


**摘要：**你说这些是不是要不断学习,学以致用
{:.message}


# 知识点总结



## 一、HTML


1. HTML5新特性，语义化是什么?

> 答： 语义化 : 根据内容的结构化（内容语义化），选择合适的标签（代码语义化）便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析。
```
1.<section></section>         //定义文档中的主体部分的节、段。
2、<article></article>        //比section有更明确的语义。独立的、完整的内容，例如论坛的文章，博客的文本。。。
3、<aside></aside>            //用来装载页面中非正文的内容，独立于其他模块。例如广告、成组的链接、侧边栏。。。
4、<header></header>　        //定义文档、页面的页眉。也可以用在内容里。
5、<footer></footer>　        //定义了文档、页面的页脚，和header类似。
6、<nav></nav>          　    //定义了一个链接组组成的导航部分，到其他网页或页面的其他部分。
7、<hgroup></hgroup>          //用于对网页或区段(section)的标题元素(h1~h6)进行组合。
8、<figure></figure>          //用于对元素进行组合。
9、<figcaption></figcaption>  //为figure元素加标题。一般放在figure第一个子元素或者最后一个。
10、<details></details>       //定义元素的细节，用户可以点击查看或者隐藏。
11、<summary></summary>       //和details连用，用来包含details的标题。
12、<canvas></canvas>         //用来进行canvas绘图。
13、<video></video>           //定义视频。
14、<audio></audio>           //定义音频。
15、<embed></embed>           //定义嵌入网页的内容。比如插件。
16、<source></source>         //该标签为媒介元素(比如video、audio)定义媒介元素。
17、<command></command>　     //定义命令行为。
18、<mark></mark>　           //在视觉上向用户展现出那些想要突出的文字。
19、<keygen></keygen>　       //定义加密内容。
20、<output></output>　       //定义不同类型的输出，样式与span无异。
21、<progress></progress>　   //进度条，运行中的进度。
22、<time></time>　           //定义日期或者时间。
```

2. 什么是浏览器的标准模式和怪异模式?

>答：
>1. 盒模式的解析上：
在strict mode 中： width是内容宽度
在quirks mode 中： width则是元素的实际宽度
>2. 图片元素垂直对齐方式
在strict mode 中： vertical-align 属性默认取值为baseline 
在 quirks mode 中： vercital-align 属性默认为bottom，因此在图片底部会有几像素的空间。 等...


3. xhtml和html的区别？

>答：xhtml:可扩展超文本标记语言，是一种置标语言，表现方式与超文本标记语言（HTML）类似，不过语法上更加严格。
>* XHTML 元素必须被正确地嵌套。
>* XHTML 元素必须被关闭。
>* 标签名必须用小写字母。
>* XHTML 文档必须拥有根元素。

4. 使用data-的好处有哪些？

>答：HTML5规范里增加了一个自定义data属性.
>>data-属性用于储存私有的自定义数据，data-属性可以让我们在所有html元素上增加自定义data属性，存储的data属性能被JavaScript调用。
```
<div id="content" data-user-list="user_list">data-user_list自定义属性 </div>
var content= document.getElementById('content');
alert(content.dataset.userList)
//jquery
$('#content').data('userList')
//注意:data-之后的以连字符分割的多个单词组成的属性，获取的时候使用驼峰风格 
//设置
$('#content').dataset.name='我叫tom'
```


5. META标签是什么？

>答：META标签是HTML语言HEAD区的一个辅助性标签.META标签用来描述一个HTML网页文档的属性，例如作者、日期和时间、网页描述、关键词、页面刷新等。可以提高SEO和爬虫效率.


6. `<canvas>`是什么？

>答：HTML5 `<canvas>` 元素用于图形的绘制,`<canvas>`标签只是图形容器，必须使用脚本(通常是JavaScript)来绘制图形。


7. HTML废弃的标签有哪些？

>答：以下标签（能直接通过属性改变样式的标签都已经被废弃了）都被废弃了 
>`<b>,<u>,<i>,<s>，<font>` 没有任何语意。改变样式只需要通过css，html主要关注语意.

8. css js放置位置和原因？

>答：js是阻塞加载，会影响页面加载的速度，如果js文件比较大，算法也比较复杂的话，影响更大。
>CSS放在前端是页面渲染时首先是根据DOM结构生成一个DOM树然后加上CSS样式生成一个渲染树，如果CSS放在后面可能页面会出现闪跳的感觉，或者是白屏或者布局混乱样式很丑直到CSS加载完成。
>综上所述，script标签最好放在`</body>`标签的前面,而css标签应该放在`<head></head>`标签之间,浏览器边构建边渲染，效率要高的多.

## 二、CSS

1. 谈谈盒模型，box-sizing?

> 答：content + margin + padding 构成盒模型
`box-sizing: content-box // 标准;
box-sizing: border-box; //IE `

2. CSS3新特性，伪类，伪元素，锚伪类?

<!-- >答：这个东西确实比较多,看到有别人做好的,也就施展一下拿来主义好了,谢谢原![博主](https://blog.csdn.net/zhouziyu2011/article/details/58605705). -->



3. CSS实现隐藏页面的方式？

>答：
>1. 将 opacity 设为 0                 `//依然占用位置`
>2. 将 visibility 设为 hidden
>3. 将 display 设为 none
>4. position 设为 absolute 然后将位置设到不可见区域。

4. 如何实现水平居中和垂直居中？

>答：

>---水平居中--- (.container为父标签,div为居中元素)
>>1. 为div设置定宽, `{margin: 0 auto}`
>>2. 对于行内元素，在父级块级元素css属性中使用 text-align：center即可.
>>3. div外包裹`<table>`标签(Table标签的长度自适应性),`table{margin: 0 auto;}`
>>4. 改变块级元素div的 display 为 inline 类型,然后使用 text-align:center 来实现居中效果.
>>5. `.container{position:relative;left:50%;} .container div{position:absolute;left:-50%;}`

>---垂直居中--- (.container为父标签,div为居中元素)
>>1. 通过设置父元素的 height 和 line-height 高度一致来实现.
>>2. 父元素高度确定的多行文本,使用插入 table.
>>3. `.container{position: relative;} .container div{position:absolute;top:50%;height: 300px;margin-top: -150px;}`
>>4. 用一个块级元素，设置已知大小，在让其高度达到父级容器的一半大小，再把要居中的元素往上提半个高度。跟方法3同理.
>>```
>>#wrapper{ background: gray;width: 500px;height: 500px;text-align: center;overflow: hidden;}
>>#null{width: 100%;height: 50%;background: yellow;}
>>#content {height: 100px;margin: -50px;}
>><div id="wrapper">
>>    <div id="null"></div>
>>    <div id="content">~</div>
>></div>
>>```
>>5. vertical-align这个属性的特点，它是相对兄弟级行高（line-height）来定位.所以要在后面加一个行内元素.
>>```
>>#wrapper{width: 800px;height: 800px;background: gray;text-align: center;}
>>#wrapper img{vertical-align: middle;}#wrapper #block{background: blue;line-height: 800px;
>><div id="wrapper">
>>    <img src="http://img0.bdstatic.com/img/image/2016ss1.jpg" alt="">
>>    <span id="block"></span>
>></div>
>>```
>>6. `.container{display: table;width: 100%;height: 100%;text-align: center;} div{display: table-cell;vertical-align: middle}`
>>7. 绝对定位居中法 
>>`.container{position: relative;background: gray;width: 800px;height: 800px;}`
`div {position: absolute;top: 0;bottom: 0;left: 0;right: 0;margin:auto;}`

5. *{box-sizing:border-box;}的作用，并说明使用它的好处?

>答：这就是上面盒模型的问题的衍生问题,使我们不再考虑padding的问题.
固定的盒子大小 padding增加不改变大小至改变内部位置  border改变也不会改变他的大小.


6.浮动元素引起的问题和解决办法？

>答：

>引起的问题
>>1. 由于浮动元素已脱离文档流，所以父元素无法被撑开，影响与父级元素同级的元素。 
>>2. 与浮动元素同级的非浮动元素（内联元素）会跟随其后，也是由于浮动元素脱离文档流，不占据文档流中额位置。 
>>3. 如果该浮动元素不是同级第一个浮动的元素，则它之前的元素也应该浮动，否则容易影响页面的结构显示。

>解决方法
>>1. 最后一个浮动元素后面添加属性为clear:both;
>>2. `.clearfix:after{content: ".";display: block;height: 0;clear: both;visibility: hidden;}`
>>3. 额外标签法，`<div style="clear:both;"></div>`
>>4. 设置overflow为hidden或者auto


7. link和@import引入css的区别?

>答：
区别1：link是XHTML标签，除了加载CSS外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CSS。
区别2：link引用CSS时，在页面载入时同时加载；@import需要页面网页完全载入以后加载。
区别3：link是XHTML标签，无兼容问题；@import是在CSS2.1提出的，低版本的浏览器不支持。
区别4：ink支持使用Javascript控制DOM去改变样式；而@import不支持。

8. css3的flexbox，以及适用场景？

>答：该布局模型的目的是提供一种更加高效的方式来对容器中的条目进行布局、对齐和分配空间。在传统的布局方式中，block 布局是把块在垂直方向从上到下依次排列的；而 inline 布局则是在水平方向来排列。弹性盒布局并没有这样内在的方向限制，可以由开发人员自由操作。
>试用场景：弹性布局适合于移动前端开发，在Android和ios上也完美支持


9. inline和inline-block的区别?

>答: inline-block 的元素（如input、img)既具有 block 元素可以设置宽高的特性，同时又具有 inline 元素默认不换行的特性。当然不仅仅是这些特性，比如 inline-block 元素也可以设置 vertical-align（因为这个垂直对齐属性只对设置了inline-block的元素有效） 属性。
**HTML 中的换行符、空格符、制表符等合并为空白符，字体大小不为 0 的情况下，空白符自然占据一定的宽度，使用inline-block 会产生元素间的空隙**。

10. 哪些是块级元素那些是行级元素，各有什么特点?

>答: 
>- 常见的块级元素有 DIV, FORM, TABLE, P, PRE, H1~H6, DL, OL, UL 等.
>- 常见的行级元素有 SPAN, A, STRONG, EM, LABEL, INPUT, SELECT, TEXTAREA, IMG, BR 等.
>1. 行内元素会在一条直线上排列（默认宽度只与内容有关），都是同一行的，水平方向排列。
块级元素各占据一行（默认宽度是它本身父容器的100%（和父元素的宽度一致），与内容无关），垂直方向排列。块级元素从新行开始，结束接着一个断行。
>2. 块级元素可以包含行内元素和块级元素。行内元素不能包含块级元素，只能包含文本或者其它行内元素。
>3. 行内元素与块级元素属性的不同，主要是盒模型属性上：行内元素设置width无效，height无效(可以设置line-height)，margin上下无效，padding上下无效

11. 实现两栏布局有哪些方法？

>答: 
>1. 左侧float:left;右侧margin-left;
>2. 左侧float:left; 右侧overflow:hidden；
>  `.left{float: left;width: 200px;background-color:skyblue;}`
>  `.right{overflow:hidden; background-color: greenyellow;}`
>3. 利用绝对定位
>`.right{ position: relative; top: 0; left: 200px; right: 0}`
>4. **利用弹性布局**
>`.left{width: 200px;background-color:skyblue;}`
>`.right{flex: 1; background-color: greenyellow;}`
这里建议利用flex进行布局,不会有高度问题,左侧也不必定宽.


12. css中常用长度总结?

>答: 
>1. px：(pixel)像素，像素px是相对于显示器屏幕分辨率而言的(引自CSS2.0手册)。电子屏幕上组成一幅图画或照片的最基本单元；
>2. pt: (point)点，印刷行业常用单位，等于1/72英寸，就是我们在Word或者WPS等办公软件中使>用的字体大小单位；
>3. ppi: (pixel per inch)每英寸像素数，该值越高，则屏幕越细腻，用于计算机和电视屏幕上每英寸显示的像素点的数量；
>4. dpi: (dot per inch)每英寸多少点，该值越高，则图片越细腻，用于打印；
>5. dp: (dip，Density-independent pixel) 是安卓开发用的长度单位，1dp表示在屏幕像素点>密度为160ppi时1px长度；
>6. sp: (scale-independent pixel)安卓开发用的字体大小单位；
>7. em:(emphasize) 是相对长度单位，相对于当前对象内文本的字体尺寸，即em的计算是基于父级元素font-size的；
>8. rem: （root em，根em）是css3新增的一个相对单位，与em的区别在于，它是相对于html根元素的(在body标签里面设置字体大小不起作用)；
>9. vw：viewpoint width，视窗宽度，1vw等于视窗宽度的1%。
>10. vh：viewpoint height，视窗高度，1vh等于视窗高度的1%。
>11. vmin：vw和vh中较小的那个。
>12. vmax：vw和vh中较大的那个。 
>13. vw, vh, vmin, vmax：IE9+局部支持，chrome/firefox/safari/opera支持，iOS safari 8+支持，Android browser4.4+支持，chrome for android39支持


9. attribute和property的区别?

>答: 
>* property是DOM中的属性，是JavaScript里的对象；
>* attribute是HTML标签上的特性，它的值只能够是字符串；
> attributes是属于property的一个子集，它保存了HTML标签上定义属性.

9. inline和inline-block的区别?

>答: display：inline-block看上去值名inline-block是一个混合产物，实际上确是如此，将元素显示为行内块状元素，设置该属性后，其他的行内块级元素会排列在同一行。比如我们li元素一个inline-block，使其既有block的宽度高度特性，又有inline的同行特性，在同一行内有不同高度内容的元素时，通常要设置对齐方式如vertical-align: top;来使元素顶部对齐。

9. inline和inline-block的区别?

>答: display：inline-block看上去值名inline-block是一个混合产物，实际上确是如此，将元素显示为行内块状元素，设置该属性后，其他的行内块级元素会排列在同一行。比如我们li元素一个inline-block，使其既有block的宽度高度特性，又有inline的同行特性，在同一行内有不同高度内容的元素时，通常要设置对齐方式如vertical-align: top;来使元素顶部对齐。

9. inline和inline-block的区别?

>答: display：inline-block看上去值名inline-block是一个混合产物，实际上确是如此，将元素显示为行内块状元素，设置该属性后，其他的行内块级元素会排列在同一行。比如我们li元素一个inline-block，使其既有block的宽度高度特性，又有inline的同行特性，在同一行内有不同高度内容的元素时，通常要设置对齐方式如vertical-align: top;来使元素顶部对齐。

## 三,
1. HTML常见兼容性问题？

   答：

> 1. 双边距BUG float引起的  使用display
>
>
> 2. 3像素问题 使用float引起的 使用dislpay:inline -3px  
>
> 3. 超链接hover 点击后失效  使用正确的书写顺序 link visited hover active
>
> 4. Iez-index问题 给父级添加position:relative
>
> 5. Png透明 使用js代码改
>
> 6. Min-height最小高度 ！Important解决’
>
> 7. select在ie6下遮盖使用iframe嵌套
>
> 8. 为什么没有办法定义1px左右的宽度容器（IE6默认的行高造成的，使用over:hidden,zoom:0.08line-height:1px）
>
> 9. IE5-8不支持opacity，解决办法：
>
>    .opacity{
>
>    ​    opacity: 0.4
>
>    ​    filter: alpha(opacity=60); /* for IE5-7 */
>
>    ​    -ms-filter:"progid:DXImageTransform.Microsoft.Alpha(Opacity=60)"; /* for IE 8*/
>
>    }
>
> 10. IE6不支持PNG透明背景，解决办法: IE6下使用gif图片

2. 描述一个"reset"的CSS文件并如何使用它。知道**`**normalize.css**`**吗？你了解他们的不同之处？

   答：

> ​	重置样式非常多，凡是一个前端开发人员肯定有一个常用的重置CSS文件并知道如何使用它们。他们是盲目的在做还是知道为什么这么做呢？原因是不同的浏览器对一些元素有不同的默认样式，如果你不处理，在不同的浏览器下会存在必要的风险，或者更有戏剧性的性发生。
>
> 　　你可能会用Normalize来代替你的重置样式文件。它没有重置所有的样式风格，但仅提供了一套合理的默认浏览器达到一致和合理，但又不扰乱其他的东西（如粗体的标题）。
>
> 　　在这一方面，无法做每一个复位重置。它也确实有些超过一个重置，它处理了你永远都不用考虑的怪癖，像HTML一致或line-height不一致。

3. BFC是什么？

   答：

> BFC（块级格式化上下文），一个创建了新的BFC的盒子是独立布局的，盒子内元素的布局不会影响盒子外面的元素。在同一个BFC中的两个相邻的盒子在垂直方向发生margin重叠的问题
>
> BFC是指浏览器中创建了一个独立的渲染区域，该区域内所有元素的布局不会影响到区域外元素的布局，这个渲染区域只对块级元素起作用

4. 怎样实现三栏布局，两边宽度固定，中间自适应？

   答：

> 圣杯布局  双飞翼布局
>
> ```
> <!DOCTYPE html>
> <html>
> <head>
>     <meta charset="UTF-8">
>     <title></title>
>     <style type="text/css">
>         * {
>             margin: 0;
>             padding: 0;
>         }
>
>         #left {
>             width: 200px;
>             height: 200px;
>             float: left;
>             background-color: red;
>         }
>
>         #right {
>             width: 150px;
>             height: 200px;
>             float: right;
>             background-color: mistyrose;
>         }
>
>         #middle {
>             height: 200px;
>             margin: 0 150px 0 200px;
>             background-color: saddlebrown;
>             word-break: break-word;
>         }
>     </style>
> </head>
> <body>
> <div id="content">
>     <div id="left">我是左侧内容我是左侧内容我是左侧内容我是左侧内容我是左侧内容</div>
>     <div id="right">我是右侧内容我是右侧内容我是右侧内容我是右侧内容我是右侧内容我是右侧内容</div>
>     <div id="middle">我是中间内容我是中间内容我是中间内容我是中间内容我是中间内容我是中间内容我是容我是中间内容我是中间内容</div>
> </div>
> </body>
> </html>
> ```

5. 精灵图(CSS Sprites)的优点和缺点

   答：

>   精灵图是一种网页图片应用处理方式。就是把网页中很多小背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background-repeat”，“background-position”的组合进行背景图显示及定位，达到显示某一部分背景图的效果。
>
>   精灵图的优点：
>
少图片的体积，因为每个图片都有一个头部信息，把多个图片放到一个图片里，就会共用同一个头部信息，从而减少了字节数。
>   2. 减少了网页的http请求次数，从而加快了网页加载速度，提高用户体验。
>   3. 解决了网页设计师在图片命名上的困扰，只需对一张集合的图片上命名就可以了，不需要对每一个小元素进网页的制作效率。
>   4. 更换风格方便，只需要在一张或少张图片上修改图片的颜色或样式，整个网页的风格就可以改变。维护起来更加方便。
>
>   精灵图的缺点：
>
>   1. 在图片合并的时候，你要把多张图片有序的合理的合并成一张图片，还要留好足够的空间，防止板块内出现还好，最痛苦的是在宽屏，高分辨率的屏幕下的自适应页面，你的图片如果不够宽，很容易出现背景断裂；
>   2. 在开发的时候比较麻烦，你要通过photoshop或其他工具测量计算每一个背景单元的精确位置，这是针线活，繁琐；
>   3. 在维护的时候比较麻烦，如果页面背景有少许改动，一般就要改这张合并的图片，无需改的地方最好不要动的css，如果在原来的地方放不下，又只能（最好）往下加图片，这样图片的字节就增加了，还要改动css。
>   4. 精灵图不能随意改变大小和颜色。精灵图改变大小会失真模糊，降低用户体验，css3新属性可以改变精灵图颜色，但是比较麻烦，并且新属性有兼容问题。现在一般都是用web字体(图标字体)来代替精灵图。

## 二、JavaScript基础模块

### 基础部分

1. JS中有哪些数据类型？

   答：

> 简单数据类型：Undefined、Null、Boolean、Number 和String。
> 复杂数据类型：Object

2. "==" 和 "===" 的区别？

   答：

> 前者会自动转换类型,而后者不会。
>
> 前者比较的是值，后者比较的是值和类型。

3. JS中的常用内置对象有哪些？并列举该对象的常用方法？

   答：

> 1. Arguments 函数参数集合
>
>     arguments[ ] 函数参数的数组
>
>     Arguments 一个函数的参数和其他属性 
>
>    Arguments.callee 当前正在运行的函数 
>
>    Arguments.length 传递给函数的参数的个数 
>
> 2. Array 数组 
>
>    length属性 动态获取数组长度 
>
>    join() 将一个数组转成字符串。返回一个字符串。 
>
>    reverse() 将数组中各元素颠倒顺序 
>
>    delete运算符 只能删除数组元素的值，而所占空间还在，总长度没变(arr.length)。 
>
>    shift() 删除数组中第一个元素，返回删除的那个值，并将长度减 1。
>
>     pop() 删除数组中最后一个元素，返回删除的那个值，并将长度减1。 
>
>    unshift() 往数组前面添加一个或多个数组元素，长度要改变。
>
>    push() 往数组结尾添加一个或多个数组元素，长度要改变。
>
>    concat( ) 连接数组 
>
>    slice( ) 返回数组的一部分 
>
>    sort( ) 对数组元素进行排序 
>
>    splice( ) 插入、删除或替换数组的元素 
>
>    toLocaleString( ) 把数组转换成局部字符串 
>
>    toString( ) 将数组转换成一个字符串
>
> 3. Boolean 布尔对象 
>
>    Boolean.toString( ) 将布尔值转换成字符串 
>
>    Boolean.valueOf( ) Boolean对象的布尔值 
>
> 4. Error 异常对象 
>
>    Error.message 可以读取的错误消息 
>
>    Error.name 错误的类型 
>
>    Error.toString( ) 把Error 对象转换成字符串
>
>    EvalError 在不正确使用 eval()时抛出 
>
>    SyntaxError 抛出该错误用来通知语法错误 
>
>    RangeError 在数字超出合法范围时抛出 
>
>    ReferenceError 在读取不存在的变量时抛出 
>
>    TypeError 当一个值的类型错误时，抛出该异常 
>
>    URIError 由URl的编码和解码方法抛出 
>
> 5. Function 函数构造器 
>
>    Function 函数构造器 
>
>    Function.apply( ) 将函数作为一个对象的方法调用 
>
>    Function.arguments[] 传递给函数的参数 
>
>    Function.call( ) 将函数作为对象的方法调用 
>
>    Function.caller 调用当前函数的函数 
>
>    Function.length 已声明的参数的个数 
>
>    Function.prototype 对象类的原型 
>
>    Function.toString( ) 把函数转换成字符串
>
> 6. Math 数学对象
>
>    Math对象是一个静态对象 
>
>    Math.PI 圆周率。 
>
>    Math.abs() 绝对值。 
>
>    Math.ceil() 向上取整(整数加 1，小数去掉)。 
>
>    Math.floor() 向下取整(直接去掉小数)。 
>
>    Math.round() 四舍五入。 
>
>    Math.pow(x，y) 求 x的y次方。 
>
>    Math.sqrt() 求平方根。
>
> 7. Number 数值对象
>
>    Number.MAX_VALUE 最大数值 
>
>    Number.MIN_VALUE 最小数值 
>
>    Number.NaN 特殊的非数字值 
>
>    Number.NEGATIVE_INFINITY 负无穷大 
>
>    Number.POSITIVE_INFINITY 正无穷大 
>
>    Number.toExponential( ) 用指数计数法格式化数字
>
>    Number.toFixed( ) 采用定点计数法格式化数字 
>
>    Number.toLocaleString( ) 把数字转换成本地格式的字符串 
>
>    Number.toPrecision( ) 格式化数字的有效位
>
>    Number.toString( ) 将—个数字转换成字符串 
>
>    Number.valueOf( ) 返回原始数值 
>
> 8. Object 基础对象
>
>    Object 含有所有 JavaScript 对象的特性的超类 
>
>    Object.constructor 对象的构造函数 
>
>    Object.hasOwnProperty( ) 检查属性是否被继承 
>
>    Object.isPrototypeOf( ) 一个对象是否是另一个对象的原型 
>
>    Object.propertyIsEnumerable( ) 是否可以通过 for/in循环看到属性 
>
>    Object.toLocaleString( ) 返回对象的本地字符串表示 
>
>    Object.toString( ) 定义一个对象的字符串表示 
>
>    Object.valueOf( ) 指定对象的原始值 
>
> 9. RegExp 正则表达式对象
>
>    RegExp.exec( ) 通用的匹配模式 
>
>    RegExp.global 正则表达式是否全局匹配 
>
>    RegExp.ignoreCase 正则表达式是否区分大小写 
>
>    RegExp.lastIndex 下次匹配的起始位置 
>
>    RegExp.source 正则表达式的文本 
>
>    RegExp.test( ) 检测一个字符串是否匹配某个模式 
>
>    RegExp.toString( ) 把正则表达式转换成字符串
>
> 10. String 字符串对象
>
>   Length 获取字符串的长度。
>
>   toLowerCase() 将字符串中的字母转成全小写。
>
>   toUpperCase() 将字符串中的字母转成全大写。
>
>   charAt(index) 返回指定下标位置的一个字符。如果没有找到，则返回空字符串。
>
>   substr() 在原始字符串，返回一个子字符串 
>
>   substring() 在原始字符串，返回一个子字符串。 
>
>   split() 将一个字符串转成数组。 
>
>   charCodeAt( ) 返回字符串中的第 n个字符的代码
>
>   concat( ) 连接字符串 
>
>   fromCharCode( ) 从字符编码创建—个字符串 
>
>   indexOf( ) 返回一个子字符串在原始字符串中的索引值(查找顺序从左往右查找)。如果没 有找到，则返回-1。
>
>   lastIndexOf( ) 从后向前检索一个字符串 
>
>   localeCompare( ) 用本地特定的顺序来比较两个字符串 
>
>   match( ) 找到一个或多个正则表达式的匹配 
>
>   replace( ) 替换一个与正则表达式匹配的子串 
>
>   search( ) 检索与正则表达式相匹配的子串 
>
>   slice( ) 抽取一个子串 
>
>   toLocaleLowerCase( ) 把字符串转换小写 
>
>   toLocaleUpperCase( ) 将字符串转换成大写 
>
>   toLowerCase( ) 将字符串转换成小写 
>
>   toString( ) 返回字符串 
>
>   toUpperCase( ) 将字符串转换成大写 
>
>   valueOf() 字符串

4. 什么是闭包？

   答：

> 简单的说，作用域是针对变量的，比如我们创建一个函数a1，函数里面又包了一 个子函数 a2。此时就存在三个作用域： 全局作用域、a1作用域、a2 作用域；即全局作用域包含了a1的作用域，a2 的作用 域包含了 a1的作用域。 当a1 在查找变量的时候会先从自身的作用域区查找，找不到再到上一级a2 的作用域 查找，如果还没找到就到全局作用域区查找，这样就形成了一个作用域链。 理解闭包首先要理解，js 垃圾回收机制，也就是当一个函数被执行完后，其作用域会被 收回，如果形成了闭包，执行完后其作用域就不会被收回。 如果某个函数被他的父函数之外的一个变量引用，就会形成闭包。 闭包的作用，就是保存自己私有的变量，通过提供的接口（方法）给外部使用，但外部 不能直接访问该变量。

5. 什么是原型链？

   答：

> Javascript 是面向对象的，每个实例对象都有一个__proto_属性，该属性指向它原 型对象，这个实例对象的构造函数有一个原型属性 prototype，与实例的__proto__属性指 向同一个对象。当一个对象在查找一个属性的时，自身没有就会根据__proto__ 向它的原型 进行查找，如果都没有，则向它的原型的原型继续查找，直到查到 Object.prototype._proto_为null，这样也就形成了原型链。

6. 有哪些方式继承？

   答：

> 1. 借用构造函数。也叫伪造对象或经典继承。 思路：在子类构造函数的内部调用超类型构造函数。可以通过使用 apply()和call()方法 在新创建的对象上执行构造函数。 缺点：方法都在构造函数中定义，函数的复用就无从谈起。在超类型的原型中定义的方 法，对子类而言也是不可见的，结果所有的类型都只能使用构造函数模式。
> 2. 组合继承。也叫伪经典继承。指的是将原型链和借用构造函数的技术组合到一起， 从而发挥二者之长。 思路：使用原型链实现对原型属性属性和方法的继承，通过借用构造函数来实现实例属 性的继承。 优点：既通过在原型上定义方法实现了函数复用，又能保证每一个实例都有它自己的数 组。 组合继承避免了原型链和借用构造函数的缺陷，融合了他们的优点，成为 JavaScript 中常用的继承模式。
> 3. 原型链继承。 思路：借助原型可以基于已有的对象创建对象，同时还不必因此创建自定义类型。 在object()函数内部，先创建一个临时的构造函数，然后将传入的对象作为这个构造函 数的原型，最后返回了这个临时类型的一个新实例。
> 4. 寄生式继承。 思路：创建一个仅用于封装继承过程的函数，该函数在内部以某种方式来增强对象，最 后再像真的是它做了所有的工作一样返回对象。缺点：使用寄生式继承来为对象添加函数，会由于不能做到函数复用二降低效率，这一 点和构造函数模式类似。 
> 5. ）寄生组合式继承。是JavaScript 最常用的继承模式。 思路：通过借用构造函数来继承属性，通过原型链的混成形式来继承方法。 本质上，就是使用寄生式继承来继承超类型的原型，然后再将结果指定给子类型的原型。 开发人员普遍认为寄生组合式继承时引用类型最理想的继承范式。 extend（）方法才用了这样的方式。

7. 字符创的常用方法有哪些？

   答：

> charCodeAt 方法返回一个整数，代表指定位置字符的 Unicode 编码；
>
> charAt方法返回指定索引位置处的字符。如果超出有效范围的索引值返回空字符串； 
>
> slice方法返回字符串的片段；
>
> substring方法返回位于String 对象中指定位置的子字符串。 
>
> substr方法返回一个从指定位置开始的指定长度的子字符串。
>
> indexOf方法返回 String 对象内第一次出现子字符串位置。如果没有找到子字符串， 则返回-1；
>
> lastIndexOf方法返回 String对象中字符串最后出现的位置。如果没有匹配到子字符 串，则返回-1；
>
> search方法返回与正则表达式查找内容匹配的第一个字符串的位置。 
>
> concat 方法返回字符串值，该值包含了两个或多个提供的字符串的连接；
>
> split 将一个字符串分割为子字符串，然后将结果作为字符串数组返回；

8. DOM节点的增删改查？

   答：

> 1. 创建节点、追加节点
>
>    createElement（标签名）创建一个元素节点（具体的一个元素）。
>
>    createTextNode（节点文本内容）创建一个文本节点。
>
>    createDocumentFragment() //创建一个 DOM 片段。
>
>    appendChild（节点）追加一个节点。
>
> 2. 插入节点
>
>    appendChild（节点）也是一种插入节点的方式，还可以添加已经存在的元素，会将其
>    元素从原来的位置移到新的位置。
>
>    insertBefore（a,b）是参照节点，意思是 a节点会插入 b节点的前面。
>
> 3. 删除、移除节点
>
>    removeChild(节点) 删除一个节点，用于移除删除一个参数（节点）。其返回的被移除
>    的节点，被移除的节点仍在文档中，只是文档中已没有其位置了。
>
> 4. 复制节点
>
>    cloneNode() 方法，用于复制节点， 接受一个布尔值参数， true 表示深复制（复制节点
>    及其所有子节点）， false 表示浅复制（复制节点本身，不复制子节点）。
>
> 5. 替换节点
>
>    replaceChild(插入的节点，被替换的节点) ，用于替换节点，接受两个参数，第一参数
>    是要插入的节点，第二个是要被替换的节点。返回的是被替换的节点。
>
> 6. 查找节点
>
>    getElementsByTagName() //通过标签名称
>    getElementsByName() //通过元素的Name 属性的值(IE容错能力较强，会得到一
>    个数组，其中包括 id等于 name值的)
>    getElementById() //通过元素 Id，唯一性

9. 什么是预解析？

   答：

> 在代码整体执行之前，先解析一部分。 
>
> 预解析之后，代码才会从上往下依次整体执行，但是预解析执行过的代码不会 重复执行。
>
> js预解析干了什么事：js 中预解析会把声明部分的代码预先执行。 
>
> 声明相关的代码可以分为两部分： 
>
> 1、 变量声明 通过 var关键字定义的变量。
>
> 2、函数声明 通过 function关键字声明的函数
>
> 预解析时如果遇到重复的变量声明，那么忽略。 
>
> 预解析时如果遇到重复的函数声明，保留后面的函数。 
>
> 预解析时如果遇到变量与函数重名的情况，保留函数。

10. 什么是变量名提升？

  答：

> 使用 var关键字定义的变量，被称为变量声明； 
>
> 函数声明提升的特点是，在函数声明的前面，可以调用这个函数。

11. JS中的typeof关键字能返回哪些数据类型？

    答：

> typeof一般判断基本数据类型。是一个操作符而不是函数，圆括号可有可无。 
>
> typeof 返回值有：string，number，boolean，undefined，object ，function， 
>
> 基本数据类型：Boolean、Number、String、Undefined、Null 
>
> 基本数据类型中数字，字符串，布尔类型返回其对类型 undefined返回 undefined 
>
> 九大内置构造函数及其他所有函数返回function； 
>
> 其他所有复杂类型对象和null返回 object 

12. 简述创建函数的几种方式？

    答：

> 1. 函数声明
>
>    function sum1(num1,num2){
>
>    ​	return num1+num2;
>
>    }
>
> 2. 函数表达式
>
>    var sum2 = function(num1,num2){
>
>    ​	return num1+num2;
>
>    }
>
> 3. 函数对象方式
>
>    var sum3 = new Function("num1","num2","return num1+num2");

13. 代码实现数组排序并去重

    答：

    ```
    function fn(arr){
      for(var i = 0; i < arr.length-1; i++){
        for(var j = 0; j < arr.length-1-i; j++){
          if(arr[j]<arr[j+1]){
            var temp = arr[j];
            arr[j] = arr[j+1];
            arr[j+1] = temp;
          }
        }
      }
      for(var k = 0; k < arr.length; k++){
        var c = arr[k];
        for(var l = k+1; l < arr.length; l++){
          if(arr[l] == c){
            arr.splice(l, 1);
            l--;
          }
        }
      }
      return arr
    }
    var arr = [1, 2, 5, 6, 8, 9, 10, 6, 5, 7, 4, 3, 5]
    console.log(fn(arr))
    ```

  14.写出下面代码输出的结果

  	A. console.log( undefined || 1 );      -->  1

  ​	B. console.log( null || NaN );            -->   NaN

  ​	C. console.log( 0 && 1 );                     -->   0

  	D. console.log( 0 && 1 || 0 );            -->   0

  15. 下列代码将会输出什么？

      ```
      var foo = 1;
      function fn() {
        console.log( foo );   -->  undefined
        var foo = 2;
        console.log( foo );   -->  2
      }
      fn();
      ```

### 实际工作部分

1. 什么是短路表达式？

   答：

> 短路表达式只是一种简写形式，也就是用 && 和 || 来赋值或者执行函数的形式
>
> 例如：
>
> var foo = foo1 || foo2;
>
> 意思是如果foo1是真的，那么就把foo1的值赋给foo，否则把foo2的值赋给foo。
>
> foo && foo()
>
> 当foo存在的时候，我们就执行foo函数，如果这个时候foo不是一个函数，就会报错，所以这个只是一种简写形式而已。

2. 控制台中使用哪些部分调试？

   答：

> 主要用console来进行调试
>
> 1. console.log 用于输出普通信息
> 2. console.info 用于输出提示性信息
> 3. console.error用于输出错误信息
> 4. console.warn用于输出警示信息
> 5. console.debug用于输出调试信息

