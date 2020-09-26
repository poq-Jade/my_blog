---
title: Hexo问题总结
abbrlink: 17376
date: 2020-09-17 14:39:30
tags:
---

# 若文章名有中文，博客文章链接默认带有中文

> 原因：站点配置文件中 Permalink 默认为：`posts:/:year/:month/:day/:title/`
> 解决办法：使用`npm i hexo-abbrlink --save`安装插件，按插件文档配置好站点文件，
> 会利用算法将博客文章链接优化为不带中文的3层链接形式。
 
修改根目录站点配置文件config.yml，改为：
```
permalink: posts/:abbrlink.html  # 此处可以自己设置，也可以直接使用 :/abbrlink
abbrlink:
    alg: crc32   #算法： crc16(default) and crc32
    rep: hex     #进制： dec(default) and hex 
```
{% note danger %}
若文章头设置了layout会导致该篇文章链接生成失败！
{% endnote %}

# 插件推荐
``` 
 hexo-abbrlink                  // Hexo 链接优化
 hexo-baidu-url-submit          // 百度链接主动提交
 hexo-blog-encrypt              // 博客文章加密
 hexo-autonofollow              // 出站链接优化
 hexo-deployer-git              // 上传部署
 hexo-generator-baidu-sitemap   // 百度站点地图
 hexo-generator-feed            // RSS 插件
 hexo-generator-searchdb        // 站内搜索
 hexo-generator-sitemap         // 站点地图
 hexo-neat                      // 博客压缩
 hexo-pdf                       // 博客文章 PDF 显示
 hexo-wordcount                 // 计数插件
 hexo-lazyload-image            // 图片懒加载
```