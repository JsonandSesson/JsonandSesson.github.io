---
title: 测试扩展标签
tags: ['web爬虫']
categories: ['爬虫','可视化工具']
date: 2022-05-06 10:46:00
swiperImg: '/medias/1.jpg'
img: '/medias/1.jpg'
swiper: true
toc: true
tocOpen: true
copyright: true
top: true
---

## 按钮
不设置任何参数的 {% btn 按钮, / %} 适合融入段落中。
黄色按钮 {% btn warning, 按钮, / %} 适合融入段落中。
蓝色按钮 {% btn info, 按钮, / %} 适合融入段落中。
绿色按钮 {% btn success, 按钮, / %} 适合融入段落中。
红色按钮 {% btn danger, 按钮, / %} 适合融入段落中。
{% btn hollow, 示例博客, https://baidu.com, fa fa-qq %}
{% btn solid, 示例博客, https://baidu.com, fa fa-weixin %}

## 折叠栏 folding
{% folding %}
![](https://pic4.zhimg.com/80/v2-5e0b1aaa1994f6d7cb9aac94a6f4e0b3_1440w.jpg)
{% endfolding  %}

{% folding cyan open, 青色折叠栏，默认展开 %}

这是一个默认打开的折叠框。

{% endfolding %}


{% folding green, 查看代码测试 %}
```
 npm install xxx
```
{% endfolding %}


## 多选框 checkbox
{% checkbox 纯文本测试 %}
{% checkbox checked, 外部 [链接](https://guides.github.com/features/mastering-markdown/) 且默认选中%}
{% checkbox red, 红色框框 %}
{% checkbox green checked, 绿色且默认选中 %}
{% checkbox plus green  checked, 绿色选中增加样式 %}
{% checkbox minus yellow checked, 黄色选中减少样式 %}
{% checkbox times red checked, 红色选中叉 %}

## 图片
{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
{% endgallery %}


## 图片收藏夹
> 跳转个人的壁纸
<div class="gallery-group-main">
    {% galleryGroup '壁纸' '收藏的一些壁纸' '/gallery/bizhi' https://pic1.zhimg.com/80/v2-23c3820e8abfb1cef689531af2dc6d09_1440w.jpg?source=1940ef5c %}
    {% galleryGroup '古典图片' '中国古典图片' '/gallery/gudian' https://pic1.zhimg.com/80/v2-8d542d68cbbf0e5f503da9e3f72b8447_1440w.jpg?source=1940ef5c %}
    {% galleryGroup '风景' '风景图片' '/gallery/fengjing' https://pic1.zhimg.com/80/v2-56164ef0695767475935c9e019c594ae_1440w.jpg?source=1940ef5c %}
</div>
