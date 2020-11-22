

## 前言
设计模式，是开发人员在开发程序过程中面临问题所使用的一些解决方案，是一套被反复使用的、多数人知晓的、经过分类编目的、代码设计经验的总结。

由于` JavaScript `不像那些强类型语言（如` Java `）是单线程弱类型语言，在前端中使用设计模式时变得简单粗暴。尽管如此，我们依然要遵守**设计模式的原则**，目的是**重用代码、让代码更容易被他人理解、保证代码可靠性**。

## 模式的起源
*[摘自网络]*

设计模式并非是软件开发中的专业术语，实际上最早诞生于建筑学。20世纪70年 代，哈佛大学建筑学博士和他的研究团队花了约 20 年的时间，研究了为解决同一问题而设计出不同结构建筑，从中发现了那些高质量设计中的相似性，并且用“模式”来指代相似性。

许多程序员从设计模式中学到了设计软件的灵感，或者找到了问题的解决答案。在社区中，有人对模式充满误解。有些人却认为设计模式只在`C++`或者`Java`中使用，`Javascript`这种动态语言没有设计模式一说。

近年来，前端技术发展迅速，不再是写几个`css` 样式和绑定事件了。大部分工具库、框架都在使用设计模式。了解它不仅为我们提供如何简洁而优雅地解决问题的思路，更能理解如何更正确、高效的使用那些工具库、框架。


## 七大原则

1.  开闭原则

**对扩展开放，对修改关闭。** 在程序需要进行拓展时，不能去修改原有的代码，实现一个热插拔的效果。

2.  里氏代换原则

**不应该重写基类**。任何基类可以出现的地方，子类一定可以出现，并且程序的功能不受到影响。**因此，里氏代换原则是对开闭原则的补充。**

3.  依赖倒转原则

**面向接口编程，而不是面向过程**。依赖倒置原则是实现开闭原则的重要途径之一，它降低了抽象与实现模块之间的耦合。

4.  单一职责原则

**一个类只负责一项功能**。如果一个对象承担了太多的职责，那么势必会造成非必要的资源占用。


5.  接口隔离原则

6.  迪米特原则

7.  合成复用原则


当我开始学设计模式，发现它在其他领域很常见，可以用在其他的方方面面。

`例1:`
``` js
interface UploadResponse{
    status:number;
    filepath:string;
}

function handleResponse( data: UploadResponse ): Image{
    const imgUrl = data.filepath;
    const imgEle = new Image();
    imgEle.src = imgUrl;
    return imgEle;
}
// axios(params).then(handleResponse);
```

`bad` 
``` js {3,4,5}
interface UploadResponse{
    status:number;
-   filepath:string;
+   smallImg:string;
+   bigImg:string;
}
```

`例1`是一个前端处理上传图片的简单示例。在某一个优化版本中，接口字段的变动都会导致前端工作量增加许多。同理，在组件中`例2`，也应该尽量避免直接修改原有的参数；

`例2`

``` html
<!-- author:A component: hello -->
<template>
    <div>hello {{uname}}</div>
</template>

<!-- user:B -->
<hello uname="vue" />
```

`bad`

``` html {2}
<template>
    <div>hello {{word}}</div>
</template>
```