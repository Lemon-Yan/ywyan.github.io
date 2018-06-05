---
layout: post
title:  "Vue.js学习之组件"
categories: 微信小程序
tags: 小程序
author: ywyan
---

* content
{:toc}

### 一、组件是什么？
>组件 (Component) 是 Vue.js 最强大的功能之一。组件可以扩展 HTML 元素，封装可重用的代码。在较高层面上，组件是自定义元素，Vue.js 的编译器为它添加特殊功能。在有些情况下，组件也可以表现为用 is 特性进行了扩展的原生 HTML 元素。

### 二、组件的使用
#####（一）全局注册
注册一个全局组件，使用 Vue.component(tagName, options)。
组件在注册之后，便可以作为自定义元素 在一个实例的模板中使用。注意确保在初始化根实例之前注册组件。

示例：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue组件</title>
</head>
<body>
<div id="example">
    <my-component></my-component>
</div>
</body>
<!--引入vue.js文件.--> 
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<script>
    //注册
    Vue.component('my-component', {
        template: '<div>组件测试</div>'
    })
    //创建根实例
    var example1 = new Vue({
        el: "#example"
    })
</script>
</html>
```
渲染为：
```
<div id="example">
  <div>组件测试</div>
</div>
```

#####（二）局部注册
不必把每个组件都注册到全局，可以通过某个 Vue 实例/组件的实例选项 components 注册仅在其作用域中可用的组件。
示例：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue组件</title>
</head>
<body>
<div id="example2">
    <my-component></my-component>
</div>
</body>
<!--引入vue.js文件.--> 
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<script>
  var child={
        template:"<div>测试局部注册组件</div>"
    }
   var example2=new Vue({
        el:"#example2",
        components:{
            'my-component':child
        }
    })
</script>
</html>
```

#####（三）DOM 模板解析注意事项
当使用 DOM 作为模板时 ，会受到 HTML 本身的一些限制，因为 Vue 只有在浏览器解析、规范化模板之后才能获取其内容。尤其要注意，像 <ul>、<ol>、<table>、<select> 这样的元素里允许包含的元素有限制，而另一些像 <option> 这样的元素只能出现在某些特定元素的内部。

在自定义组件中使用这些受限制的元素时会导致一些问题，例如：
```
<table>
  <my-row>...</my-row>
</table>
```
自定义组件 <my-row> 会被当作无效的内容，因此会导致错误的渲染结果。变通的方案是使用特殊的 is 特性：
```
<table>
  <tr is="my-row"></tr>
</table>
```
示例：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue组件</title>
</head>
<body>
<div id="example3">
    <table>
        <tr is="my-row"></tr>
    </table>
</div>
</body>
<!--引入vue.js文件.--> 
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<script>
var child2={
        template:"<tr>DOM 模板解析注意事项测试</tr>"
    }
    var example3=new Vue({
        el:"#example3",
        components:{
            'my-row':child2
        }
    })
</script>
</html>
```
#####（四）data必须是函数
构造 Vue 实例时传入的各种选项大多数都可以在组件里使用。只有一个例外：data 必须是函数。
示例：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue组件</title>
</head>
<body>
<div id="example4">
    <simple-counter></simple-counter>
    <simple-counter></simple-counter>
    <simple-counter></simple-counter>
</div>
</body>
<!--引入vue.js文件.--> 
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<script> 
    var counter={counter:0};
    var child3={
        template:'<button v-on:click="counter += 1">{{ counter }}</button>',
        data:function () {
            return {
                counter:0
            }
        }
    }
    var example4=new Vue({
        el:"#example4",
        components:{
            'simple-counter':child3
        }
    })
</script>
</html>
```
