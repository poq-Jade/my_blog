---
title: 主题Butterfly-配置（三）
abbrlink: 36519
date: 2020-09-18 11:23:12
tags:
  - Hexo
  - Butterfly
copyright_author: Jerry
copyright_author_href: https://demo.jerryc.me/posts/21cfbf15/
copyright_url: https://demo.jerryc.me/posts/21cfbf15/
copyright_info: 此文章版權歸Butterfly所有
---

# 语言
修改站点配置文件 `_config.yml`
默认语言是 en
主题支持三种语言

* default(en)
* zh-CN (简体中文)
* zh-TW (繁体中文)

# 网站资料
修改网站各种资料，例如标题、副标题和邮箱等个人资料，请修改博客根目录的`_config.yml`

# 导航菜单
修改 `主题配置文件`
```YAML
menu:
  Home: / || fas fa-home
  Archives: /archives/ || fas fa-archive
  Tags: /tags/ || fas fa-tags
  Categories: /categories/ || fas fa-folder-open
  List||fas fa-list:
    - Music || /music/ || fas fa-music
    - Movie || /movies/ || fas fa-video
  Link: /link/ || fas fa-link
  About: /about/ || fas fa-heart
```
必须是 `/xxx/`，后面 `||` 分开，然后写图标名。
注意： 导航的文字可自行更改
例如：
```MARKDOWN
menu:
  首页: / || fas fa-home
  时间轴: /archives/ || fas fa-archive
  标籤: /tags/ || fas fa-tags
  分类: /categories/ || fas fa-folder-open
  清单||fa fa-heartbeat:
    - 音乐 || /music/ || fas fa-music
    - 照片 || /Gallery/ || fas fa-images
    - 电影 || /movies/ || fas fa-video
  友链: /link/ || fas fa-link
  关于: /about/ || fas fa-heart 
```
{% asset_img  hexo-theme-butterfly-doc-menu.png %}

# 代码

{% note info %}
代码块中的所有功能只适用于 Hexo 默认的 highlight 渲染
如果使用第三方的渲染器，不一定会有效
{% endnote %}

## 代码高亮主题
{% tabs code %}
<!-- tab 默认主题-->
`Butterfly` 支持 6 种代码高亮样式：
* darker
* pale night
* light
* ocean
* mac
* mac light

修改 `主题配置文件`
```YAML
highlight_theme: light
```

> darker
  
{% asset_img hexo-theme-butterfly-doc-code-darker.png %}

> pale night

{% asset_img hexo-theme-butterfly-doc-code-pale-night.png %}
 
> light

{% asset_img hexo-theme-butterfly-doc-code-light.png %}

> ocean

{% asset_img hexo-theme-butterfly-doc-highlight-ocean.png %}

> mac

{% asset_img hexo-theme-butterfly-doc-highlight-mac.png %}

> mac light

{% asset_img hexo-theme-butterfly-docs-mac-light.png %}  


<!--endtab -->


<!-- tab 自定义主题-->
主题从 3.0 开始，支持使用自定义的代码顔色。
目前 Highlight 官方提供了 100 多种 CSS 配色，如果你不喜欢主题默认的代码配色，可以自己自定义。
Highlight 提供的 CSS 列表：[点击](https://github.com/highlightjs/highlight.js/tree/master/src/styles)
Highlight 提供的 CSS Demo: [点击](https://highlightjs.org/static/demo/)

1. 配置 `hljs` 为 `true`
修改 Hexo 根目录下的`_config.yml`

```YAML
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
  hljs: true
```

2. 配置 `highlight_theme` 为 `false`
修改 `主题配置文件`

```YAML
highlight_theme: false
```

3. 下载和修改 CSS 文件
下载需要的 CSS 文件，CSS 可由[这里](https://github.com/highlightjs/highlight.js/tree/master/src/styles)获得
打开 CSS 文件，在开头补上这些 CSS
```CSS
/* 代码框背景色和字体顔色,与hljs一样就行 */
/* 必须配置(把下面.hljs的color和background复制到这里来) */
#article-container pre, 
#article-container figure.highlight {
  background: xxx ;  
  color: xxx
}

/* 代码框工具栏 (如果你关掉了copy、lang和shrink,可不用配置这个 */
#article-container figure.highlight .highlight-tools {
  color: xxx;
  background: xxx
}

/* 代码框行数(如果已经关掉line_number,可以不用配置这个) */
#article-container figure.highlight .gutter pre {
  background-color: xxx;
  color: xxx
}

/* 代码块figcaption配置(hexo自带标签https://hexo.io/zh-tw/docs/tag-plugins.html#Code-Block) */
/* 不需要可以不用配置这个 */
#article-container figure.highlight figcaption a {
  color: xxx !important
}

/* 代码框滚动条 (需要可配置，默认为主题主顔色）*/
/* 不需要可以不用配置这个 */
#article-container figure.highlight table::-webkit-scrollbar-thumb {
  background: #5c4627
}
```

把顔色修改成你需要的顔色
同时，找到`.hljs`, 在 class 名字前添加`#article-container figure.highlight`
```CSS
#article-container figure.highlight .hljs {
    xxxx
    xxxx
    xxxx
}
```
4. 引入文件
修改 `主题配置文件`
```YAML
inject:
  head:
    - <link rel="stylesheet" href="/self/xxxx.css">
```
在 head 里引入 CSS 文件
运行 Hexo 就能看到修改的效果了
具体 Demo 可查看
[自定义代码配色](https://demo.jerryc.me/posts/b37b5fe3/)
<!--endtab -->
{% endtabs %}

## 代码复制 
主题支持代码复制功能

修改 `主题配置文件`
```YAML
highlight_copy: true
```

## 代码框展开 / 关闭
在默认情况下，代码框自动展开，可设置是否所有代码框都关闭状态，点击 `>` 可展开代码

true 全部代码框不展开，需点击 `>` 打开
false 代码狂展开，有 `>` 点击按钮
none 不显示 `>` 按钮
修改 `主题配置文件`

```YAML
highlight_shrink: true #代码框不展开，需点击 '>' 打开
```

{% note info %}
你也可以在 post/page 页对应的 markdown 文件 front-matter 添加 highlight_shrink 来独立配置。

当主题配置文件中的 highlight_shrink 设为 true 时，可在 front-matter 添加 highlight_shrink: false 来单独配置文章展开代码框。

当主题配置文件中的 highlight_shrink 设为 false 时，可在 front-matter 添加 highlight_shrink: true 来单独配置文章收缩代码框。
{% endnote %}

## 代码换行
在默认情况下，`hexo-highlight` 在编译的时候不会实现代码自动换行。如果你不希望在代码块的区域里有横向滚动条的话，
那么你可以考虑开启这个功能。

修改 `主题配置文件`
```YAML
code_word_wrap: true
```
然后找到你站点的 Hexo 配置文件`_config.yml`，将 `line_number` 改成 `false`:
```YAML
highlight:
  enable: true
  line_number: false
  auto_detect: false
  tab_replace:
```

# 社交图标
Butterfly 支持 [font-awesome v5](https://fontawesome.com/icons?from=io) 图标.
书写格式 图标名：url || 描述性文字

```YAML
social:
  fab fa-github: https://github.com/xxxxx || Github
  fas fa-envelope: mailto:xxxxxx@gmail.com || Email
```
图标名可在这寻找
{% asset_img hexo-theme-butterfly-doc-fontawesome.png %}
    
# 主页文章节选 (自动节选和文章页 description)
因为主题 UI 的关係，`主页文章节选`只支持`自动节选`和`文章页description`。

在 `butterfly` 里，有三种可供选择
* description 只显示 description
* both 优先选择 description，如果没有配置 description，则显示自动节选的内容
* auto_excerpt 只显示自动节选
修改 `主题配置文件`
```YAML
index_post_content:
  method: 3
  length: 500 # if you set method to 2 or 3, the length need to config
```

`description` 在 front-matter 里添加
{% asset_img hexo-theme-butterfly-doc-post-description.png %}

# 顶部图
`顶部图`有 2 种配置：具体 url 和（留空，true 和 false，三个效果一样）

## page 页
### 当具体 url 时
主页的顶部图可以在主题配置文件中设置 `index_img`
archives 页的顶部图可以在主题配置文件中设置 `archive_img`
其他 `page` 页的顶部图可以在各自的 md 页面设置 front-matter 中的 `top_img`

{% note info %}
页面如果没有设置各自的 `top_img`，则会显示 `default_top_img` 图片
配置中的 `tag_img` 和 `category_img` 分别是 子标签页 和 子分类 的 顶部图配置，
如果你是想配置 `tags`页 和 `categories`页的顶部图，请到对应的 md 页面设置 `front-matter` 中的 `top_img`
{% endnote %}

### 当顶部图留空，true 和 false
主页会显示纯颜色的顶部图
其他 page 的顶部图没有设置时，也会显示纯颜色的顶部图

## post 页
post 页的顶部图会优先显示各自 `front-matter` 中的 `top_img`, 如果没有设置，则会缩略图（即各自 front-matter 中的 cover)，如果没有则会显示显示 `default_top_img` 图片

# 文章置顶
【推荐】`hexo-generator-index`从 2.0.0 开始，已经支持文章置顶功能。你可以在文章的 `front-matter` 区域里添加 `sticky: 1` 属性来把这篇文章置顶。数值越大，置顶的优先级越大。

当然，你也可以安装第三方插件来实现这个功能 ([hexo-generator-index-pin-top](https://github.com/netcan/hexo-generator-index-pin-top) 或者 [hexo-generator-indexed](https://github.com/next-theme/hexo-generator-indexed))

如果使用 `hexo-generator-index-pin-top`, 需要先卸载掉 `hexo-generator-index`，然后在文章的 front-matter 区域里添加 `top: true` 属性来把这篇文章置顶

如果使用 `hexo-generator-indexed`, 需要先卸载掉 `hexo-generator-index`，然后在文章的 `front-matter` 区域里添加 `sticky: 1` 属性来把这篇文章置顶。数值越大，置顶的优先级越大

# 文章封面
文章的 markdown 文档上，在 `Front-matter` 添加 `cover`, 并填上要显示的图片地址。
如果不配置 `cover`, 可以设置显示默认的 cover.

如果不想在首页显示 cover, 可以设置为 `false`

修改 `主题配置文件`
```YAML
cover:
  # 是否显示文章封面
  index_enable: true
  aside_enable: true
  archives_enable: true
  # 封面显示的位置
  # 三个值可配置 left , right , both
  position: both
  # 当没有设置cover时，默认的封面显示
  default_cover:
```

当配置多张图片时，会随机选择一张作为 cover. 此时写法应为
```YAML
default_cover:
  - https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg.png
  - https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg2.png
  - https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg3.png
```

# 文章页相关配置
## 文章 meta 显示
这个选项是用来显示文章的相关信息的。

修改 `主题配置文件`
```YAML
post_meta:
  page:
    date_type: both # created or updated or both 主页文章日期是创建日或者更新日或都显示
    categories: true # true or false 主页是否显示分类
    tags: true # true or false 主页是否显示标籤
    label: true # true or false 显示描述性文字
  post:
    date_type: both # created or updated or both 文章页日期是创建日或者更新日或都显示
    categories: true # true or false 文章页是否显示分类
    tags: true # true or false 文章页是否显示标籤
    label: true # true or false 显示描述性文字
```
{% asset_img hexo-theme-butterfly-docs-page-meta.png %}

在文章顶部的资料，

`date_type`: 可设置文章日期显示创建日期 (`created`) 或者更新日期 (`updated`) 或者两种都显示 (`both`)

`categories` 是否显示分类

{% asset_img hexo-theme-butterfly-doc-post-info.png %}

`tags` 是否显示标签
{% asset_img hexo-theme-butterfly-doc-post-tag.png %}

## 文章版权
为你的博客文章展示文章版权和许可协议。

修改 `主题配置文件`
```YAML
post_copyright:
  enable: true
  decode: false
  license: CC BY-NC-SA 4.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/4.0/
```

由于 `Hexo 4.1` 开始，默认对网址进行解码，以至于如果是中文网址，会被解码，可设置 `decode: true` 来显示中文网址。

如果有文章（例如：转载文章）不需要显示版权，可以在文章 Front-matter 单独设置
```YAML
copyright: false
```

从 `3.0.0` 开始，支持对单独文章设置版权信息，可以在文章 `Front-matter` 单独设置
```MARKDOWN
copyright_author: xxxx
copyright_author_href: https://xxxxxx.com
copyright_url: https://xxxxxx.com
copyright_info: 此文章版权归xxxxx所有，如有转载，请註明来自原作者
```

## 文章打赏
在你每篇文章的结尾，可以添加打赏按钮。相关二维码可以自行配置。

对于没有提供二维码的，可配置一张软件的 icon 图片，然后在 link 上添加相应的打赏链接。用户点击图片就会跳转到链接去。

link 可以不写，会默认为图片的链接。

修改 `主题配置文件`
```YAML
reward:
  enable: true
  QR_code:
    - img: /image/wechat.jpg
      link:
      text: 微信
    - img: /image/alipay.jpg
      link:
      text: 支付宝
```
{% asset_img hexo-theme-butterfly-doc-post-donate.png %}

## 文章隐藏
> 2.3.0 开始主题不再默认提供文章隐藏功能

如需要文章隐藏功能，请装插件 [hexo-generator-indexed](https://github.com/next-theme/hexo-generator-indexed) 或者 [hexo-hide-posts](https://github.com/printempw/hexo-hide-posts)

## TOC
在文章页，会有一个目录，用于显示 TOC。

`enable`: 是否显示 TOC
`number`: 是否显示章节数
`auto_open`: 可选择进入文章页面时，是否自动打开 sidebar 显示 TOC

修改 `主题配置文件`

```YAML
toc:
  enable: true
  number: true
  auto_open: true # auto open the sidebar
```

### 为特定的文章配置
在你的文章 `md` 文件的头部，加入 `toc_number`、`toc` 和 `auto_open`，并配置 `true` 或者 `false` 即可。

主题会优先判断文章 Markdown 的 Front-matter 是否有配置，如有，则以 Front-matter 的配置为準。否则，以主题配置文件中的配置为準

## 相关文章
相关文章推荐的原理是根据文章 `tags` 的比重来推荐

修改 `主题配置文件`
```YAML
related_post:
  enable: true
  limit: 6 # 显示推荐文章数目
  date_type: created # or created or updated 文章日期显示创建日或者更新日
```

## 文章锚点
开启文章锚点后，当你在文章页进行滚动时，文章链接会根据标题 ID 进行替换
(注意：每替换一次，会留下一个歷史记录。所以如果一篇文章有很多锚点的话，网页的歷史记录会很多。)

修改 `主题配置文件`
```YAML
# anchor
# when you scroll in post , the url will update according to header id.
anchor: true
```

## 文章过期提醒
可设置是否显示文章过期提醒，以更新时间为基準。
```YAML
# Displays outdated notice for a post (文章过期提醒)
noticeOutdate:
  enable: true
  style: flat # style: simple/flat
  limit_day: 365 # When will it be shown
  position: top # position: top/bottom
  message_prev: It has been
  message_next: days since the last update, the content of the article may be outdated.
```
`limit_day`： 距离更新时间多少天才显示文章过期提醒

`message_prev`： 天数之前的文字

`message_next`：天数之后的文字

# 头像
修改 `主题配置文件`
```YAML
avatar:
  img: /img/avatar.png
  effect: true # 头像会一直转圈
```

# 图片描述
可开启图片 Figcaption 描述文字显示

修改 `主题配置文件`
```YAML
photofigcaption: true
```

# 复製相关配置
可配置网站是否可以复製、复製的内容是否添加版权信息
```MARKDOWN
# copy settings
# copyright: Add the copyright information after copied content (复製的内容后面加上版权信息)
copy:
  enable: true
  copyright:
    enable: true
    limit_count: 50
```
配置          |解释
:-------------|:------
enable        |是否开启网站复製权限
copyright     |复製的内容后面加上版权信息
enable        |是否开启复製版权信息添加
limit_count   |字数限制，当复製文字大于这个字数限制时，将在复製的内容后面加上版权信息

> 添加版权信息后
```
Lorem ipsum dolor sit amet, test link consectetur adipiscing elit. Strong text pellentesque ligula commodo viverra vehicula. Italic text at ullamcorper enim. Morbi a euismod nibh. Underline text non elit nisl. Deleted text tristique, sem id condimentum tempus, metus lectus venenatis mauris, sit amet semper lorem felis a eros. Fusce egestas nibh at sagittis auctor. Sed ultricies ac arcu quis molestie. Donec dapibus nunc in nibh egestas, vitae volutpat sem iaculis. Curabitur sem tellus, elementum nec quam id, fermentum laoreet mi. Ut mollis ullamcorper turpis, vitae facilisis velit ultricies sit amet. Etiam laoreet dui odio, id tempus justo tincidunt id. Phasellus scelerisque nunc sed nunc ultricies accumsan.


作者: Jerry
连结: http://localhost:4000/posts/bd3c650b/#Paragraph
来源: Butterfly
着作权归作者所有。商业转载请联络作者获得授权，非商业转载请註明出处。
```

# Footer 设置
## 博客年份
`since` 是一个来展示你站点起始时间的选项。它位于页面的最底部。

修改 `主题配置文件`
```YAML
index_post_content:
  method: 3
  length: 500 # if you set method to 2 or 3, the length need to config
```
`description` 在 front-matter 里添加
{% asset_img hexo-theme-butterfly-doc-post-description.png %}

## 页脚自定义文本
`custom_text` 是一个给你用来在页脚自定义文本的选项。通常你可以在这里写声明文本等。支持 HTML。

修改 `主题配置文件`
```YAML
custom_text: Hi, welcome to my <a href="https://jerryc.me/">blog</a>!
```

## ICP
对于部分有备案的域名，可以在 ICP 配置显示。

修改 `主题配置文件`
```YAML
ICP:
  enable: true
  url: http://www.beian.miit.gov.cn/state/outPortal/loginPortal.action
  text: 粤ICP备xxxx
  icon: /img/icp.png
```

# 右下角按钮
## 简繁转换
简体繁体互换

右下角会有简繁转换按钮。

修改 `主题配置文件`
```YAML
translate:
  enable: true
  # 默认按钮显示文字(网站是简体，应设置为'default: 繁')
  default: 简
  #网站默认语言，1: 繁体中文, 2: 简体中文
  defaultEncoding: 1
  #延迟时间,若不在前, 要设定延迟翻译时间, 如100表示100ms,默认为0
  translateDelay: 0
  #当文字是简体时，按钮显示的文字
  msgToTraditionalChinese: "繁"
  #当文字是繁体时，按钮显示的文字
  msgToSimplifiedChinese: "简"
```

## 夜间模式
右下角会有夜间模式按钮

修改 `主题配置文件`
```YAML
# dark mode
darkmode:
  enable: true
  # dark mode和 light mode切换按钮
  button: true
  autoChangeMode: false
```
{% asset_img hexo-theme-butterfly-doc-dark-mode.png %}

{% note %}
V2.0.0 开始增加一个选项，可开启自动切换 light mode 和 dark mode

autoChangeMode: 1 跟随系统而变化，不支持的浏览器 / 系统将按照时间晚上 6 点到早上 6 点之间切换为 dark mode

autoChangeMode: 2 只按照时间 晚上 6 点到早上 6 点之间切换为 dark mode, 其余时间为 light mode

autoChangeMode: false 取消自动切换
{% endnote %}

## 閲读模式
閲读模式下会去掉除文章外的内容，避免干扰閲读。

只会出现在文章页面，右下角会有閲读模式按钮。

修改 `主题配置文件`
```YAML
readmode: true
```

# 侧边栏设置
## 侧边排版
可自行决定哪个项目需要显示，可决定位置，也可以设置不显示侧边栏。

修改 `主题配置文件`
```YAML
aside:
  enable: true
  mobile: true # 手机页面（ 显示宽度 < 768px ）是否显示aside内容
  position: right # left or right
  card_author:
    enable: true
    description:
    button:
      icon: fab fa-github
      text: Github
      link: https://github.com/jerryc127/hexo-theme-butterfly
  card_announcement:
    enable: true
    content: This is my Blog
  card_recent_post:
    enable: true
    limit: 5 # if set 0 will show all
    sort: date # date or updated
  card_categories:
    enable: true
    limit: 8 # if set 0 will show all
    expand: none # none/true/false
  card_tags:
    enable: true
    limit: 40 # if set 0 will show all
    color: false
  card_archives:
    enable: true
    type: monthly # yearly or monthly
    format: MMMM YYYY # eg: YYYY年MM月
    order: -1 # Sort of order. 1, asc for ascending; -1, desc for descending
    limit: 8 # if set 0 will show all
  card_webinfo:
    enable: true
    post_count: true
    last_push_date: true
```

> position: left
  
{% asset_img hexo-theme-butterfly-doc-aside-left.png %}

> position: right
  
{% asset_img hexo-theme-butterfly-doc-aside-right.png %}

> card_tags color: false
  
{% asset_img 20200426182730.png %}

> card_tags color: true
  
{% asset_img 20200426183025.png %}

## 访问人数 **busuanzi (UV 和 PV)**
访问 busuanzi 的官方网站查看更多的介绍。

修改 `主题配置文件`
```YAML
busuanzi:
  site_uv: true
  site_pv: true
  page_pv: true
```
{% asset_img hexo-theme-butterfly-doc-busuanzi-site-pv.png %}
{% asset_img hexo-theme-butterfly-doc-pv.png %}

## 运行时间
网页已运行时间

修改 `主题配置文件`
```YAML
runtimeshow:
  enable: true
  publish_date: 6/7/2018 00:00:00  
  ##网页开通时间
  #格式: 月/日/年 时间
  #也可以写成 年/月/日 时间
```
{% asset_img hexo-theme-butterfly-doc-runtime.png %}

## 最新评论
> 3.1.0 起支持
  
{% note primary %}
最新评论只会在刷新时才会去读取，并不会实时变化

由于 API 有 访问次数限制，为了避免调用太多，主题默认存取期限为 10 分鐘。也就是説，调用后资料会存在 localStorage 里，10 分鐘内刷新网站只会去 localStorage 读取资料。10 分鐘期限一过，刷新页面时才会去调取 API 读取新的数据。
{% endnote %}

{% note warning%}
由于 Leancloud Api 限制，Leancloud 的 appId 和 appKey 最好和 Valine 评论是同一个，不然遇到最新评论 和 Valine 评论共存的页面，会出现报错，其中一方会无法运行。
{% endnote %}

在侧边栏显示最新评论板块

修改 主题配置文件
```JS
newest_comments:
  enable: false
  limit: 6
  avatar: true
  leancloud:
    enable: false
    appId: # leancloud application app id
    appKey: # leancloud application app key
    serverURL: # This configuration is suitable for domestic custom domain name users, overseas version will be automatically detected (no need to manually fill in)
    default_avatar: mp # mp/identicon/monsterid/wavatar/retro/robohash/blank
  github_issues:
    enable: false
    repo:
  disqus:
    enable: false
    forum:
    api_key:
```
部分配置解释：

配置                        |解释
:---------------------------|:---
limit                       |显示的数量
avatar                      |是否显示头像
leancloud - appId           |等同于 valine 配置中的 appId
leancloud - appKey          |等同于 valine 配置中的 appKey
leancloud - serverURL       |等同于 valine 配置中的 serverURLs，国内版才需要配置
leancloud - default_avatar  |默认头像，对于一些没有配置 Gravatar 头像的，将会显示默认头像
github_issues - repo        |评论存在的仓库，例如 jerryc127/jerryc127.github.io
disqus - forum              |等同于 disqusjs 的 shortname
disqus - api_key            |等同于 disqusjs 的 apikey

> default_avatar
  
参数              |效果
:-----------------|:---
留空（默认）      |![](https://www.gravatar.com/avatar/00000000000000000000000000000000)
mp                |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=mp)
identicon         |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=identicon)
monsterid	      |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=monsterid)
wavatar	          |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=wavatar)
retro	          |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=retro)
robohash	      |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=robohash)
blank	          |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=blank)
404	              |![](https://www.gravatar.com/avatar/00000000000000000000000000000000?d=mp&f=y)


# 标签外挂（Tag Plugins）
{% note info %}
标籤外挂是 Hexo 独有的功能，并不是标準的 Markdown 格式。

以下的写法，只适用于 Butterfly 主题，用在其它主题上不会有效果，甚至可能会报错。使用前请留意
{% endnote %}

{% note warning %}
标签外挂虽然能为主题带来一些额外的功能和 UI 方面的强化，但是，标签外挂也有明显的限制，使用时请留意。
{% endnote %}

## Note (Bootstrap Callout)
移植于 next 主题

修改 `主题配置文件`
```YAML
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```
用法
```MARKDOWN
{% note [class] [no-icon] %}
Any content (support inline tags too.io).
{% endnote %}

[class]   : default | primary | success | info | warning | danger.
[no-icon] : Disable icon in note.

All parameters are optional.
```
例如：
```MARKDOWN
{% note default %}
default 提示块标籤
{% endnote %}

{% note primary no-icon %}
primary 提示块标籤
{% endnote %}

{% note success %}
success 提示块标籤
{% endnote %}

{% note info %}
info 提示块标籤
{% endnote %}

{% note warning %}
warning 提示块标籤
{% endnote %}

{% note danger %}
danger 提示块标籤
{% endnote %}
```

> style: modern

{% note warning %}
此处只展示style: simple 样式、剩余的modern、flat、disabled不展示。
{% endnote %}  
{% asset_img 20200105232825.png %}

## Gallery 相册图库
> 2.2.0 以上提供

一个图库集合。

写法
```MARKDOWN
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
```
* name：图库名字
* description：图库描述
* link：连接到对应相册的地址
* img-url：图库封面的地址

例如：

```
<div class="gallery-group-main">
{% galleryGroup '壁纸' '收藏的一些壁纸' '/Gallery/wallpaper' https://i.loli.net/2019/11/10/T7Mu8Aod3egmC4Q.png %}
{% galleryGroup '漫威' '关于漫威的图片' '/Gallery/marvel' https://i.loli.net/2019/12/25/8t97aVlp4hgyBGu.jpg %}
{% galleryGroup 'OH MY GIRL' '关于OH MY GIRL的图片' '/Gallery/ohmygirl' https://i.loli.net/2019/12/25/hOqbQ3BIwa6KWpo.jpg %}
</div>
```

## Gallery 相册
> 2.0.0 以上提供

区别于旧版的 Gallery 相册，新的 Gallery 相册会自动根据图片长度进行排版，书写也更加方便，与 markdown 格式一样。可根据需要插入到相应的 md。

写法:
```MARKDOWN
{% gallery %}
markdown 图片格式
{% endgallery %}
```
例如
```MARKDOWN
{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}
```

## tag-hide
> 2.2.0 以上提供
{% note warning %}
请注意，tag-hide 内的标签外挂 content 内都不建议有 h1 - h6 等标题。因为 Toc 会把隐藏内容标题也显示出来，而且当滚动屏幕时，如果隐藏内容没有显示出来，会导致 Toc 的滚动出现异常。

如果你想把一些文字、内容隐藏起来，并提供按钮让用户点击显示。可以使用这个标签外挂。
{% endnote %}

{% tabs tag_hide %}
<!-- tab Inline -->
`inline` 在文本里面添加按钮隐藏内容，只限文字

( content 不能包含英文逗号，可用 `&sbquo`;)
```MARKDOWN
{% hideInline content,display,bg,color %}
```
* content: 文本内容

* display: 按钮显示的文字 (可选)

* bg: 按钮的背景颜色 (可选)

* color: 按钮文字的颜色 (可选)

> Demo
```MARKDOWN
哪个英文字母最酷？ {% hideInline 因为西装裤(C装酷),查看答案,#FF7242,#fff %}

门里站着一个人? {% hideInline 闪 %}
```
哪个英文字母最酷？ {% hideInline 因为西装裤(C装酷),查看答案,#FF7242,#fff %}

门里站着一个人? {% hideInline 闪 %}
<!-- endtab -->
<!-- tab Block -->
`block` 独立的 block 隐藏内容，可以隐藏很多内容，包括图片，代码块等等

( display 不能包含英文逗号，可用 `&sbquo`;)
```MARKDOWN
{% hideBlock display,bg,color %}
content
{% endhideBlock %}

* content: 文本内容
* display: 按钮显示的文字 (可选)
* bg: 按钮的背景颜色 (可选)
* color: 按钮文字的颜色 (可选)

```

> Demo
```MARKDOWN
查看答案
{% hideBlock 查看答案 %}
傻子，怎么可能有答案
{% endhideBlock %}
```
查看答案
{% hideBlock 查看答案 %}
傻子，怎么可能有答案
{% endhideBlock %}
<!-- endtab -->
<!-- tab Toggle -->
> 2.3.0 以上支持

如果你需要展示的内容太多，可以把它隐藏在收缩框里，需要时再把它展开。

( display 不能包含英文逗号，可用 `&sbquo`;)
```MARKDOWN
{% hideToggle display,bg,color %}
content
{% endhideToggle %}
```
{% hideToggle display,bg,color %}
content
{% endhideToggle %}

> Demo

```MARKDOWN
{% hideToggle Butterfly安装方法 %}
在你的博客根目录里

git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly

如果想要安装比较新的dev分支，可以

git clone -b dev https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly

{% endhideToggle %}
```
{% hideToggle Butterfly安装方法 %}
在你的博客根目录里

git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly

如果想要安装比较新的dev分支，可以

git clone -b dev https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly

{% endhideToggle %}
<!-- endtab -->
{% endtabs %}

## mermaid
{% note warning %}
mermaid 标籤不允许嵌套于一些隐藏属性的标籤外挂，例如: tag-hide 内的标籤外挂和 tabs 标籤外挂，这会导致 mermaid 图示无法正常显示，使用时请留意。

请不要压缩 **html** 代码，不然会导致 **mermaid** 显示异常
{% endnote %}

使用 mermaid 标籤可以绘製 Flowchart（流程图）、Sequence diagram（时序图 ）、Class Diagram（类别图）、State Diagram（状态图）、Gantt（甘特图）和 Pie Chart（圆形图），具体可以查看 [mermaid](https://mermaid-js.github.io/mermaid/#/) 文档

修改 `主题配置文件`
```YAML
mermaid:
  enable: true
  # built-in themes: default/forest/dark/neutral
  theme: default
```
写法：
```MARKDOWN
{% mermaid %}
内容
{% endmermaid %}
```
例如：

```MARKDOWN
{% mermaid %}
pie
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
{% endmermaid %}
```
{% asset_img hexo-theme-butterfly-docs-mermaid.png %}

Tabs
移植于 next 主题

使用方法
```MARKDOWN
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}

Unique name   : Unique name of tabs block tag without comma.
                Will be used in #id's as prefix for each tab with their index numbers.
                If there are whitespaces in name, for generate #id all whitespaces will replaced by dashes.
                Only for current url of post/page must be unique!
[index]       : Index number of active tab.
                If not specified, first tab (1) will be selected.
                If index is -1, no tab will be selected. It's will be something like spoiler.
                Optional parameter.
[Tab caption] : Caption of current tab.
                If not caption specified, unique name with tab index suffix will be used as caption of tab.
                If not caption specified, but specified icon, caption will empty.
                Optional parameter.
[@icon]       : FontAwesome icon name (full-name, look like 'fas fa-font')
                Can be specified with or without space; e.g. 'Tab caption @icon' similar to 'Tab caption@icon'.
                Optional parameter.
```

> Demo 1 - 预设选择第一个【默认】

```MARKDOWN
{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```
{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

> Demo 2 - 预设选择 tabs

```MARKDOWN
{% tabs test2, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```
{% tabs test2, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

> Demo 3 - 没有预设值
  
```MARKDOWN
{% tabs test3, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```

{% tabs test3, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

> Demo 4 - 自定义 Tab 名 + 只有 icon + icon 和 Tab 名
  
```MARKDOWN
{% tabs test4 %}
<!-- tab 第一个Tab -->
**tab名字为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}
```

{% tabs test4 %}
<!-- tab 第一个Tab -->
**tab名字为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}

## Button
> 3.0 以上适用
  
使用方法：

```MARKDOWN
{% btn [url],[text],[icon],[color] [style] [layout] [position] [size] %}

[url]         : 链接
[text]        : 按钮文字
[icon]        : [可选] 图标
[color]       : [可选] 按钮背景顔色(默认style时）
                      按钮字体和边框顔色(outline时)
                      default/blue/pink/red/purple/orange/green
[style]       : [可选] 按钮样式 默认实心
                      outline/留空
[layout]      : [可选] 按钮佈局 默认为line
                      block/留空
[position]    : [可选] 按钮位置 前提是设置了layout为block 默认为左边
                      center/right/留空
[size]        : [可选] 按钮大小
                      larger/留空
```

> Demo

```MARKDOWN
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,,outline %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,larger %}
```

This is my website, click the button {% btn 'http://www.jerryc.me',JerryC %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,,outline %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline %}
This is my website, click the button {% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,larger %}

```MARKDOWN
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,block %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,block center larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,block right outline larger %}
```

{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,block %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,block center larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,block right outline larger %}

more than one button in center
```MARKDOWN
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,blue larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,pink larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,red larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,purple larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,orange larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,green larger %}
```
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,blue larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,pink larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,red larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,purple larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,orange larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,green larger %}

```MARKDOWN
<div class="btn-center">
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline blue larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline pink larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline red larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline purple larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline orange larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline green larger %}
</div>
```
<div class="btn-center">
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline blue larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline pink larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline red larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline purple larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline orange larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,outline green larger %}
</div>