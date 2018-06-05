---
layout: post
title:  "HTML入门"
categories: HTML
tags: HTML
author: ywyan
---

* content
{:toc}


![](http://upload-images.jianshu.io/upload_images/4041074-c8da8e1abc0c7ab7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 一、HTML是什么 ？
>- HTML 是用来描述网页的一种语言。 
>- HTML 指的是超文本标记语言: HyperText Markup Language
>- HTML 不是一种编程语言，而是一种标记语言
>- 标记语言是一套标记标签 (markup tag)
>- HTML 使用标记标签来描述网页
>- HTML 文档包含了HTML 标签及文本内容
>- HTML文档也叫做 web 页面
>- 可以使用 HTML 来建立自己的 WEB 站点，HTML 运行在浏览器上，由浏览器来解析。

HTML文档的后缀名
- .html
- .htm
以上两种后缀名没有区别，都可以使用。

## 二、HTML网页结构
只有 在<body> 区域 (白色部分) 才会在浏览器中显示。
![image.png](http://upload-images.jianshu.io/upload_images/4041074-762de52548ec3165.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

示例：浏览器中运行
 ![image.png](http://upload-images.jianshu.io/upload_images/4041074-cb46d871414f8b48.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>测试案例</title>
</head>
<body> 
    <h1>我的第一个标题</h1> 
    <p>我的第一个段落。</p> 
</body>
</html>
```
示例解析：
> `<!DOCTYPE html>` 声明为 `HTML5` 文档
`<html>` 元素是 `HTML` 页面的根元素
`<head>` 元素包含了文档的元（meta）数据
`<title>` 元素描述了文档的标题
`<body>` 元素包含了可见的页面内容
`<h1>` 元素定义一个大标题
`<p>` 元素定义一个段落

**注意：**  对于中文网页需要使用 `<meta charset="utf-8">` 声明编码，否则会出现乱码。
             有些浏览器会设置 `GBK` 为默认编码，需要设置 `<meta charset="gbk">`。

## 三、HTML版本
![image.png](http://upload-images.jianshu.io/upload_images/4041074-18c01543c5995b11.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



## 四、HTML标签 和元素
![image.png](http://upload-images.jianshu.io/upload_images/4041074-3fe5a11aad65b85e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>HTML 标记标签通常被称为 `HTML` 标签 (HTML tag)。 
HTML 标签是由尖括号包围的关键词，比如 `<html>`
HTML 标签通常是成对出现的，比如 `<b>` 和 `</b>`
标签对中的第一个标签是开始标签，第二个标签是结束标签
开始和结束标签也被称为开放标签和闭合标签 
内容（Content）：这是元素的内容，在这种情况下只是文本。
元素（Element）：开始标记，加结束标记，加内容，等于元素。
空元素在开始标签中进行关闭（以开始标签的结束而结束）

（一）嵌套元素
把元素放到其它元素之中被称作嵌套。

> 正确示例：```<p>My cat is <strong>very</strong> grumpy.</p>```   
错误示例：```<p>My cat is <strong>very grumpy.</p></strong>```

需要确保元素被正确的嵌套：在上面的例子中先打开`<p>`元素，然后再打开`<strong>`元素，因此必须先将`<strong>`元素关闭，然后再去关闭`<p>`元素。

（二）块级元素和内联元素
>- 块级元素在页面中以块的形式展现，会出现在新的一行，其后的内容也会被挤到下一行展现。
块级元素通常用于展示页面上结构化的内容，例如段落、列表、导航菜单、页脚等等。
一个以block形式展现的块级元素不会被嵌套进内联元素中，但可以嵌套在其它块级元素中。
>- 内联元素通常出现在块级元素中并包裹文档内容的一小部分，而不是一整个段落或者一组内容。
内联元素不会导致文本换行，它通常出现在一堆文字之间，例如超链接元素<a>或者强调元素`<em>`和 `<strong>`。

（三）空元素
 不是所有元素都拥有开始标签，内容和结束标记. 一些元素只有一个标签，通常用来在此元素所在位置插入`/`嵌入一些东西 。
例如： ```<img src="img/demo.png">``` 元素`<img>`是用来在元素所在位置插入一张指定的图片。

## 五、HTML 属性
属性是 HTML 元素提供的附加信息，这些信息不会出现在实际的内容中。

![image.png](http://upload-images.jianshu.io/upload_images/4041074-0eef9530c92fe53c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>- HTML 元素可以设置属性 
>- 属性一般描述于开始标签
>- 属性总是以名称/值对的形式出现，比如：name="value"。
>- 属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。 

**提示:** 在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：name='John "ShotGun" Nelson'

>- 属性和属性值对大小写不敏感。不过，万维网联盟在其 HTML 4 推荐标准中推荐小写的属性/属性值。
而新版本的 (X)HTML 要求使用小写属性。 
>- 布尔属性：有时会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值。例如**disabled** 属性，他们可以标记表单输入使之变为不可用(变灰色)，此时用户不能向他们输入任何数据。
```<input type="text" disabled="disabled">```或```<input type="text" disabled>```

适用于大多数 HTML 元素的属性：
![image.png](http://upload-images.jianshu.io/upload_images/4041074-d11831f316471276.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 六、实体引用： 在HTML中包含特殊字符
在HTML中，字符 <, >,",' 和 & 是特殊字符，它们是HTML语法自身的一部分。
必须使用字符引用表示字符的特殊编码, 每个字符引用以符号&开始, 以分号(;)结束。
![image.png](http://upload-images.jianshu.io/upload_images/4041074-93dc75c63efe38b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**提示**: 维基百科上有一个包含所有可用HTML字符实体引用的列表：[XML和HTML字符实体引用列表](http://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references)。

## 七、HTML注释
在HTML中有一种可用的机制来在代码中书写注释 ，注释是被浏览器忽略的，而且是对用户不可见的，它们的目的是允许描述你的代码是如何工作的和不同部分的代码做了什么等等。

为了将一段HTML中的内容置为注释，你需要将其用特殊的记号<!--和-->包括起来， 比如：
```
<!-- 测试 -->
<p>测试部分</p> 
```


参考：[菜鸟教程](http://www.runoob.com/html/html-tutorial.html)
