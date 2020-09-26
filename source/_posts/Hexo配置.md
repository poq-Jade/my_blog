---
title: Hexo配置
tags:
  - Hexo
abbrlink: e18ede91
date: 2020-09-16 11:37:12
---

您可以在 _config.yml 中修改大部分的配置。

# 网站

 参数	    |描述
:---------- |:-------
title       |网站标题
subtitle    |网站副标题
description |网站描述
keywords    |网站的关键词。支援多个关键词。
author      |您的名字
language    |网站使用的语言。对于简体中文用户来说，使用不同的主题可能需要设置成不同的值，请参考你的主题的文档自行设置，常见的有 zh-Hans和 zh-CN。
timezone    |网站时区。Hexo 默认使用您电脑的时区。请参考 时区列表 进行设置，如 America/New_York, Japan, 和 UTC 。一般的，对于中国大陆地区可以使用 Asia/Shanghai。

其中，description主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。author参数用于主题显示文章的作者。

# 网址
    
参数                        |描述                     |默认值
:---------------            |:------------------------|:-----
url                         |网站根目录               |网站根目录
root                        |网站根目录	
permalink                   |文章的 永久链接 格式     |:year/:month/:day/:title/
permalink_defaults          |永久链接中各部分的默认值	
pretty_urls                 |改写 permalink 的值来美化 URL
pretty_urls.trailing_index  |是否在永久链接中保留尾部的 index.html，设置为 false 时去除	    |true
pretty_urls.trailing_html   |是否在永久链接中保留尾部的 .html, 设置为 false 时去除 (对尾部的 index.html无效) |true
    
> ## 网站存放在子目录
> 如果您的网站存放在子目录中，例如 http://example.com/blog，则请将您的 url 设为 http://example.com/blog 并把 root 设为 /blog/。

例如:
```
# 比如，一个页面的永久链接是 http://example.com/foo/bar/index.html
pretty_urls:
  trailing_index: false
# 此时页面的永久链接会变为 http://example.com/foo/bar/
```

# 目录
参数            |描述         |默认值
:---------------|:------------|:-----
source_dir      |资源文件夹，这个文件夹用来存放内容。                  |source
public_dir      |公共文件夹，这个文件夹用于存放生成的站点文件。        |public
tag_dir         |标签文件夹                                            |tags
archive_dir     |归档文件夹                                            |archives
category_dir    |分类文件夹                                            |categories
code_dir        |Include code 文件夹，source_dir 下的子目录            |downloads/code
i18n_dir        |国际化（i18n）文件夹                                  |:lang
skip_render     |跳过指定文件的渲染。匹配到的文件将会被不做改动地复制到 public 目录中。您可使用 glob 表达式来匹配路径。	

例如：
```
skip_render: "mypage/**/*"
# 将会直接将 `source/mypage/index.html` 和 `source/mypage/code.js` 不做改动地输出到 'public' 目录
# 你也可以用这种方法来跳过对指定文章文件的渲染
skip_render: "_posts/test-post.md"
# 这将会忽略对 'test-post.md' 的渲染
```
> ## 提示
>如果您刚刚开始接触 Hexo，通常没有必要修改这一部分的值。

# 文章

参数              |描述                                         |默认值
:-----------------|:--------------------------------------------|:-----
new_post_name           |新文章的文件名称                                   |:title.md
default_layout          |预设布局                                           |post
auto_spacing            |在中文和英文之间加入空格                           |false
titlecase               |把标题转换为 title case                            |false
external_link           |在新标签中打开链接                                 |true
external_link.enable    |在新标签中打开链接	                                |true
external_link.field     |对整个网站（site）生效或仅对文章（post）生效	    |site
external_link.exclude   |需要排除的域名。主域名和子域名如 www 需分别配置    |[]
filename_case           |把文件名称转换为 (1) 小写或 (2) 大写               |0
render_drafts           |显示草稿                                           |false
post_asset_folder       |启动 Asset 文件夹                                  |false
relative_link           |把链接改为与根目录的相对位址                       |false
future                  |显示未来的文章                                     |true
highlight               |代码块的设置, see Highlight.js section for usage guide	
prismjs                 |代码块的设置, see PrismJS section for usage guide	

>
> ## 相对地址
> 默认情况下，Hexo 生成的超链接都是绝对地址。例如，如果您的网站域名
> 为 example.com,您有一篇文章名为 hello，那么绝对链接可能像这
> 样：http://example.com/hello.html，它是绝对于域名的。相对链接像这
> 样：/hello.html，也就是说，无论用什么域名访问该站点，都没有关系，
> 这在进行反向代理时可能用到。通常情况下，建议使用绝对地址。

# 分类 & 标签
|参数                 |描述             |默认值
:---------------------|:----------------|:----- 
|default_category       |默认分类               |uncategorized
|category_map           |分类别名	
|tag_map                |标签别名	

# 日期 / 时间格式
Hexo 使用 Moment.js 来解析和显示时间。

|参数             |描述             |默认值
:-----------------|:----------------|:-----
|date_format        |日期格式           |YYYY-MM-DD
|time_format        |时间格式           |HH:mm:ss
|updated_option     |当 Front Matter 中没有指定 updated 时 updated 的取值     |mtime

> # updated_option
> updated_option 控制了当 Front Matter 中没有指定 updated 时，updated 如何取值：
> mtime: 使用文件的最后修改时间。这是从 Hexo 3.0.0 开始的默认行为。
> date: 使用 date 作为 updated 的值。可被用于 Git 工作流之中，因为使用 Git 管理站点时，文件的最后修改日期常常会发生改变
>  empty: 直接删除 updated。使用这一选项可能会导致大部分主题和插件无法正常工作。
>  use_date_for_updated 选项已经被废弃，将会在下个重大版本发布时去除。请改为使用 updated_option: 'date'。

use_date_for_updated | 启用以后，如果 Front Matter 中没有指定 updated， post.updated 将会使用 date 的值而不是文件的
创建时间。在 Git 工作流中这个选项会很有用 | true

# 分页

参数           |描述                         |默认值
:--------------|:----------------------------|:-----
per_page       |每页显示的文章量 (0 = 关闭分页功能)      |10
pagination_dir |分页目录                                 |page

# 扩展
参数            |描述
:-------------  |:---
theme           |当前主题名称。值为false时禁用主题
theme_config    |主题的配置文件。在这里放置的配置会覆盖主题目录下的 _config.yml 中的配置
deploy          |部署部分的设置
meta_generator  |Meta generator 标签。 值为 false 时 Hexo 不会在头部插入该标签

## 包括或不包括目录和文件
在 Hexo 配置文件中，通过设置 include/exclude 可以让 Hexo 进行处理或忽略某些目录和文件夹。
你可以使用 glob 表达式 对目录和文件进行匹配。

include and exclude options only apply to the source/ folder, whereas ignore option applies to all folders.

参数          |描述
:-------------|:---
include     |Hexo 默认会忽略隐藏文件和文件夹（包括名称以下划线和 . 开头的文件和文件夹，Hexo 的 _posts 和 _data 等目录除外）。通过设置此字段将使 Hexo 处理他们并将它们复制到 source 目录下。
exclude     |Hexo 会忽略这些文件和目录
ignore      |Ignore files/folders

举例：

```angular2
# Include/Exclude Files/Folders
include:
  - ".nojekyll"
  # 包括 'source/css/_typing.css'
  - "css/_typing.css"
  # 包括 'source/_css/' 中的任何文件，但不包括子目录及其其中的文件。
  - "_css/*"
  # 包含 'source/_css/' 中的任何文件和子目录下的任何文件
  - "_css/**/*"

exclude:
  # 不包括 'source/js/test.js'
  - "js/test.js"
  # 不包括 'source/js/' 中的文件、但包括子目录下的所有目录和文件
  - "js/*"
  # 不包括 'source/js/' 中的文件和子目录下的任何文件
  - "js/**/*"
  # 不包括 'source/js/' 目录下的所有文件名以 'test' 开头的文件，但包括其它文件和子目录下的单文件
  - "js/test*"
  # 不包括 'source/js/' 及其子目录中任何以 'test' 开头的文件
  - "js/**/test*"
  # 不要用 exclude 来忽略 'source/_posts/' 中的文件。你应该使用 'skip_render'，或者在要忽略的文件的文件名之前加一个下划线 '_'
  # 在这里配置一个 - "_posts/hello-world.md" 是没有用的。

ignore:
  # Ignore any folder named 'foo'.
  - "**/foo"
  # Ignore 'foo' folder in 'themes/' only.
  - "**/themes/*/foo"
  # Same as above, but applies to every subfolders of 'themes/'.
  - "**/themes/**/foo"
```
列表中的每一项都必须用单引号或双引号包裹起来。

include 和 exclude 并不适用于 themes/ 目录下的文件。如果需要忽略 themes/ 目录下的部分文件或文件夹，
可以使用 ignore 或在文件名之前添加下划线 _。

## 使用代替配置文件
可以在 hexo-cli 中使用 --config 参数来指定自定义配置文件的路径。你可以使用一个 YAML 或 JSON 文件的路径，
也可以使用逗号分隔（无空格）的多个 YAML 或 JSON 文件的路径。例如：

```angular2
# use 'custom.yml' in place of '_config.yml'
$ hexo server --config custom.yml

# use 'custom.yml' & 'custom2.json', prioritizing 'custom3.yml', then 'custom2.json'
$ hexo generate --config custom.yml,custom2.json,custom3.yml
```
当你指定了多个配置文件以后，Hexo 会按顺序将这部分配置文件合并成一个 _multiconfig.yml。如果遇到重复的配置，
排在后面的文件的配置会覆盖排在前面的文件的配置。这个原则适用于任意数量、任意深度的 YAML 和 JSON 文件。

例如，使用 --options 指定了两个自定义配置文件：

```angular2
$ hexo generate --config custom.yml,custom2.json
```
如果 custom.yml 中指定了 foo: bar，在 custom2.json 中指定了 "foo": "dinosaur"，
那么在 _multiconfig.yml 中你会得到 foo: dinosaur。

## 使用代替主题配置文件
通常情况下，Hexo 主题是一个独立的项目，并拥有一个独立的 _config.yml 配置文件。
除了自行维护独立的主题配置文件，你也可以在其它地方对主题进行配置。

独立的 _config.[theme].yml 文件
> 该特性自 Hexo 5.0.0 起提供

独立的主题配置文件应放置于站点根目录下，支持 yml 或 json 格式。需要配置站点 _config.yml 文件中的 theme 以供 
Hexo 寻找 _config.[theme].yml 文件。

```
# _config.yml
theme: "my-theme" 
```
```
# _config.my-theme.yml
bio: "My awesome bio"
foo:
  bar: 'a' 
```
``` 
# themes/my-theme/_config.yml
bio: "Some generic bio"
logo: "a-cool-image.png"
  foo:
    baz: 'b'
```
最终主题配置的输出是：
```
{
  bio: "My awesome bio",
  logo: "a-cool-image.png",
  foo: {
    bar: "a",
    baz: "b"
  }
} 
```
> 建议你将所有的主题配置集中在一处。如果你不得不在多处配置你的主题，那么这些信息对你将会
> 非常有用：Hexo 在合并主题配置时，Hexo 配置文件中的 theme_config 的优先级最高，其次是 _config.[theme].yml 文件，最后是位于主题目录下的 _config.yml 文件。

# _confiig.yml 配置文件
```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site                    # 网站设置
title: Hexo               # 网站标题
subtitle: ''              # 网站副标题
description: ''           # 网站描述
keywords:                 # 网站的关键词。支援多个关键词。
author: John Doe          # 您的名字
language: zh-CN           # 网站使用的语言
timezone: ''              # 网站时区。Hexo 默认使用您电脑的时区。时区列表。比如说：America/New_York, Japan, 和 UTC 。

url: http://example.com                     # 网址
root: /                                     # 网站根目录

permalink: :year/:month/:day/:title/        # 文章的 永久链接 格式
permalink_defaults:                         # 永久链接中各部分的默认值

pretty_urls:                   # 改写 permalink 的值来美化 URL
  trailing_index: true         # 是否在永久链接中保留尾部的 index.html，设置为 false 时去除	
  trailing_html: true          # 是否在永久链接中保留尾部的 .html, 设置为 false 时去除 (对尾部的 index.html无效)	

# Directory                     # 目录
source_dir: source              # 资源文件夹，这个文件夹用来存放内容。	
public_dir: public              # 公共文件夹，这个文件夹用于存放生成的站点文件。	
tag_dir: tags                   # 标签文件夹	
archive_dir: archives           # 归档文件夹	
category_dir: categories        # 分类文件夹	
code_dir: downloads/code        # Include code 文件夹，source_dir 下的子目录	
i18n_dir: :lang                 # 国际化（i18n）文件夹
	
skip_render:                    # 跳过指定文件的渲染。匹配到的文件将会被不做改动地复制到 public 目录中。
                                # 您可使用 glob 表达式来匹配路径。	

# Writing                       # 文章
new_post_name: :title.md        # 新文章的文件名称	
default_layout: post            # 预设布局	
auto_spacing: false             # 在中文和英文之间加入空格	
titlecase: false                # 把标题转换为 title case	
external_link:                  # 在新标签中打开链接	
  enable: true                  # 在新标签中打开链接	
  field: site                   # 对整个网站（site）生效或仅对文章（post）生效	
  exclude: ''                   # 需要排除的域名。主域名和子域名如 www 需分别配置	
filename_case: 0                # 把文件名称转换为 (1) 小写或 (2) 大写	
render_drafts: false            # 显示草稿	
post_asset_folder: true         # 启动 Asset 文件夹
marked:
  prependRoot: true
  postAsset: true
relative_link: false            # 把链接改为与根目录的相对位址	
future: true                    # 显示未来的文章	
highlight:                      # 代码块的设置, 详情：https://hexo.io/docs/syntax-highlight#PrismJS
  enable: true
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:                        # 代码块的设置, 详情：https://hexo.io/docs/syntax-highlight#PrismJS
  enable: false
  preprocess: true
  line_number: true
  tab_replace: ''

# 主页设置    貌似是 hexo-generator-index插件的配置
index_generator:
  path: ''                  # 博客索引页的根路径
  per_page: 10              # 每页数量
  order_by: -date           # 按日期排序

# 分类 & 标签
default_category: uncategorized         # 默认分类	
category_map:                           # 分类别名	
    Hexo: hexo                          # 原分类名： 别名
tag_map:                                # 标签别名	
    Hexo: hexo                          # 原标签名： 别名 
    
# Metadata elements                     # 没明白是啥，应该是html的相关插件设置
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true

# 日期 / 时间格式
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD             # 日期格式	
time_format: HH:mm:ss               # 时间格式	
## updated_option supports 'mtime', 'date', 'empty'     
updated_option: 'mtime'             # 当 Front Matter 中没有指定 updated 时 updated 的取值
                                    # 简单来说就是当文章中没有指定的时间时，默认使用的时间选择方式

# 分页
## Set per_page to 0 to disable pagination
per_page: 10                # 每页显示的文章量 (0 = 关闭分页功能)
pagination_dir: page        # 分页目录	

# 包括或不包括目录和文件
## include:/exclude: options only apply to the 'source/' folder
include:                    # Hexo 默认会忽略隐藏文件和文件夹
                            #（包括名称以下划线和 . 开头的文件和文件夹，Hexo 的 _posts 
                            # 和 _data 等目录除外）。通过设置此字段将使 Hexo 处理他们并将它们复制到 source 目录下。
exclude:                    # Hexo 会忽略这些文件和目录
ignore:                     # 用于忽略 themes/ 目录下的部分文件或文件夹（include和exclude不适用于themes文件夹）

# 扩展
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: Butterfly            # 当前主题名称。值为false时禁用主题

# 部署设置
## 文档: https://hexo.io/docs/one-command-deployment
## 中文文档：https://hexo.io/zh-cn/docs/one-command-deployment
deploy:
  type: git     # 部署类型
  repo: git@github.com:poq-Jade/hexo.github.io.git      # 库（Repository）地址
  branch: master                                        # 分支名称	

```