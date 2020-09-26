---
title: Hexo图片的使用
tags:
  - Hexo
abbrlink: 8985cdfe
date: 2020-09-14 16:56:54
---
# 文章资源文件夹
  对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，Hexo也提供了更组织化的方式来管理资源。这个稍微有些复杂但是管理资源非常方便的功能可以通过将 config.yml 文件中的 post_asset_folder 选项设为 true 来打开。
  
 _config.yml
```
post_asset_folder: true
```

>使用以下方式加载文章图片，可以避免上传到github上后图片不显示问题

{% tabs imgs %}
<!-- tab 本地文件 -->
```
{% asset_img WeChat835.png 图片名 图片介绍 %}
```
{% asset_img WeChat835.png 图片介绍 %}
<!-- endtab -->

<!-- tab 外网图片 -->
```
![图片名](https://pandao.github.io/editor.md/images/logos/editormd-logo-180x180.png "图片介绍")
```
![图片名](https://pandao.github.io/editor.md/images/logos/editormd-logo-180x180.png "图片介绍")
<!-- endtab -->

{% endtabs %}

