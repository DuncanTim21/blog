---
layout: post
title: 富文本编辑器 Ckeditor 使用
tags: [Front-End]
---

**摘要：**在页面的制作中 总会遇到文本域,为了用户的体验,不免要用到富文本编辑器 ,在这里可能用到最多的就是[Ckeditor](https://ckeditor.com/) 这个插件,虽然国内有百度做的ueditor这样的编辑器,但是UI实在不是我的风格,如果有需要的,也可以看看.
{:.message}

## What is Ckeditor?

先来看看 <a href="https://docs.ckeditor.com/ckeditor4/latest/guide/index.html" target="_blank">官方文档</a> 中的介绍：
> CKEditor是新一代的FCKeditor，是一个重新开发的版本。CKEditor是全球最优秀的网页在线文字编辑器之一，因其惊人的性能与可扩展性而广泛的被运用于各大网站。

## How to use Ckeditor?
1.将下载下来的ckeditor文件解压后，直接复制，粘贴到WEB项目的webroot目录。（项目一放进去就报错，不用管它。这是因为IDE工具版本的问题）
2.在网页上添加两句话：

2.导入JS文件：<script src="//cdn.ckeditor.com/4.4.5/standard/ckeditor.js"></script>  注意：这句话是在电脑能联网的时候才有效的，因为路径是通过网络访问到的。

你也可以使用另外一句话：<script src="ckeditor_4.4.5_standard/ckeditor/ckeditor.js"></script> 这样，就可以在没有联网的情况也可以使用到ckeditor。

其实就是导入一份JS文件，如果你看不到效果的话，检查下路径是否有错误就可以了。

3.弄个textarea标签显示ckeditor：<textarea id="editor" class="ckeditor"></textarea>(注意，里面的id  class属性值一个都不能错，不能省)
