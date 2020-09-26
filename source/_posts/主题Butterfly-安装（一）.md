---
title: 主题Butterfly-安装
tags:
  - Hexo
  - Butterfly
abbrlink: dda3546a
date: 2020-09-16 17:39:17
copyright_author: Jerry
copyright_author_href: https://demo.jerryc.me/posts/21cfbf15/
copyright_url: https://demo.jerryc.me/posts/21cfbf15/
copyright_info: 此文章版權歸Butterfly所有
---

{% note danger %}
如果有安装这两个插件的，请卸载掉，会导致主题报错。
[hexo-inject](https://github.com/hexojs/hexo-inject) 和 [hexo-neat](https://github.com/rozbo/hexo-neat)
{% endnote %}

---
`hexo-theme-butterfly` 是基于 [Molunerfinn](https://github.com/Molunerfinn) 的 [hexo-theme-melody](https://github.com/Molunerfinn/hexo-theme-melody) 的基础上进行开发的。
文档也是在 [hexo-theme-melody](https://github.com/Molunerfinn/hexo-theme-melody) 的文档基础上修改。因为一些配置变更导致与原主题配置上有部分区别。故如果安装 `hexo-theme-butterfly` 主题，请参考这篇文档。

# 安裝
{% tabs buttfly %}
<!-- tab Git安装 -->
稳定版【建议】

在你的博客根目录里
``` 
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```

测试版
> 测试版可能存在 Bugs，追求稳定的请安装稳定版
  
如果想要安装比较新的 dev 分支，可以
``` POWERSHELL
git clone -b dev https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```
> 升级方法：在主题目录下，运行 `git pull`
  
<!-- endtab -->

<!-- tab npm安装 -->
> 此方法只支持 Hexo 5.0.0 以上版本
  
在你的博客根目录里
```POWERSHELL
npm i hexo-theme-butterfly
```
> 升级方法：在博客根目录下，运行 `npm update hexo-theme-butterfly`

<!-- endtab -->
{% endtabs %}

# 应用主题
修改站点配置文件`_config.yml`，把主题改为 `butterfly`
```YAML
theme: butterfly
```

# 安装插件
如果你没有 pug 以及 stylus 的渲染器，请下载安装：
```POWERSHELL
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

# 升级建议
> 以下方法只是建议，不一定需要那样做

为了减少升级主题后带来的不便，请使用以下其中一种方法就行。

{% tabs update %}
<!-- tab _config.butterfly.yml-->
> 此方法只支持 Hexo 5.0.0 以上版本，建议使用。
> 
> 如果已经在 source/_data/ 创建了 butterfly.yml，请记得删除掉。

把主题文件夹中的 _config.yml 复製到 Hexo 根目录里，同时重新命名为 _config.butterfly.yml。

以后只需要在 _config.butterfly.yml 进行配置就行。

Hexo 会自动合併主题中的_config.yml 和 _config.butterfly.yml 里的配置，如果存在同名配置，会使用_config.butterfly.yml 的配置，其优先度较高。

{% asset_img WeChat5936.png 图片介绍 %}
<!-- endtab -->
    
<!-- tab butterfly.yml-->
> 此方法支持 Hexo 3.0.0 以上版本
  
为了减少升级主题后带来的不便，`Butterfly` 使用了 [data files](https://hexo.io/docs/data-files.html) 特性。

推荐把主题默认的配置文件`_config.yml` 复製到 Hexo 根目录下的 `source/_data/` 目录下，然后将文件名改为 butterfly.yml（如果 `source/_data/` 的目录不存在就创建一个）。

{% note warning %}
注意，如果你创建了 butterfly.yml, 它将会替换主题默认配置文件_config.yml 里的配置项 (~~不是合併而是替换~~，3.1.0 开始将会是合併)

採用 butterfly.yml 的目的是，因为升级主题的时候，有可能会覆盖到配置文件，以至于每次更新的时候都需要重新配置文件。如果使用 butterfly.yml，就算主题目录下的_config.yml 被覆盖，主题只会去 butterfly.yml 读取配置。

~~由于主题在添加功能或者修復 Bugs 的情况下，可能会涉及到配置文件的修改。这时候，如果升级主题，需要把新增加的配置添加到 butterfly.yml 去，不然很大机会会出现报错。~~（ 3.1.0 之后，应该不会出现这种情况）
{% endnote %}
<!-- endtab -->

{% endtabs  %}


