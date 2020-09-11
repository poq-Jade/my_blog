title: Markdown 样式示例（一）
author: John Doe
date: 2020-09-08 17:05:22
tags:
	- Markdown
---
参考地址：
[Markdown](https://www.w3cschool.cn/markdownyfsm/markdownyfsm-markdownjmyf.html)
[Butterfly](https://demo.jerryc.me/posts/89757140/)

# 标题
```MARKDOWN
# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternatively, for H1 and H2, an underline-ish style:

Alt-H1
======

Alt-H2
------
```
# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternatively, for H1 and H2, an underline-ish style:

Alt-H1
======

Alt-H2
------

## Emphasis
```MARKDOWN
Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~

```
Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~

# Lists（列表）
```MARKDOWN
1. First ordered list item
2. Another item
  * Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.

   You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

   To have a line break without a paragraph, you will need to use two trailing spaces.  
   Note that this line is separate, but within the same paragraph.  
   (This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
- Paragraph In unordered list

  For example like this.

Common Paragraph with some text.
And more text.

```
1. First ordered list item
2. Another item
  * Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.

   You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

   To have a line break without a paragraph, you will need to use two trailing spaces.  
   Note that this line is separate, but within the same paragraph.  
   (This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
- Paragraph In unordered list

  For example like this.

Common Paragraph with some text.
And more text.

# Inline HTML（内嵌Html）
```MARKDOWN
<p>To reboot your computer, press <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>del</kbd>.</p>
```
To reboot your computer, press ctrl+alt+del.

```MARKDOWN
<dl>
    <dt>Definition list</dt>
    <dd>Is something people use sometimes.</dd>

    <dt>Markdown in HTML</dt>
    <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```

# Images（图片）
```MARKDOWN
hover to see the title text:

Inline-style:

![alt text](https://hexo.io/icon/favicon-196x196.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://hexo.io/icon/favicon-196x196.png "Logo Title Text 2"
```
hover to see the title text:

Inline-style:

![alt text](https://hexo.io/icon/favicon-196x196.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://hexo.io/icon/favicon-196x196.png "Logo Title Text 2"

# Code and Syntax Highlighting(代码和语法突出显示)
Inline code has back-ticks around it.
```JAVASCRIPT
var s = "JavaScript syntax highlighting";
alert(s);
```
```PYTHON
s = "Python syntax highlighting"
print s
```
```
No language indicated, so no syntax highlighting.
But let's throw in a <b>tag</b>.
```
```HTML
<!DOCTYPE html>
<html>
    <head>
        <mate charest="utf-8" />
        <meta name="keywords" content="Editor.md, Markdown, Editor" />
        <title>Hello world!</title>
        <style type="text/css">
            body{font-size:14px;color:#444;font-family: "Microsoft Yahei", Tahoma, "Hiragino Sans GB", Arial;background:#fff;}
            ul{list-style: none;}
            img{border:none;vertical-align: middle;}
        </style>
    </head>
    <body>
        <h1 class="text-xxl">Hello world!</h1>
        <p class="text-green">Plain text</p>
    </body>
</html>
```
# Tables(表格)
```
|                |ASCII                          |HTML                         |
|----------------|-------------------------------|-----------------------------|
|Single backticks|`'Isn't this fun?'`            |'Isn't this fun?'            |
|Quotes          |`"Isn't this fun?"`            |"Isn't this fun?"            |
|Dashes          |`-- is en-dash, --- is em-dash`|-- is en-dash, --- is em-dash|
```
|                |ASCII                          |HTML                         |
|----------------|-------------------------------|-----------------------------|
|Single backticks|`'Isn't this fun?'`            |'Isn't this fun?'            |
|Quotes          |`"Isn't this fun?"`            |"Isn't this fun?"            |
|Dashes          |`-- is en-dash, --- is em-dash`|-- is en-dash, --- is em-dash|

## 冒号可用于对齐列
```MARKDOWN
| 表格        | 对齐方式			  |		    |
| ------------|:-------------------------:|----------------:|
| 列3是       | 右对齐			  |		    |
| 列2是       | 居中 			  |		    |
| 列1是       | 默认 			  |		    |
```
| 表格        | 对齐方式			  |		    |
| ------------|:-------------------------:|----------------:|
| 列3是       | 右对齐			  |		    |
| 列2是       | 居中 			  |		    |
| 列1是       | 默认 			  |		    |

## 外边框的`|`是线可选的，可以不使用外边框
```
Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
```
Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

你可以在[这里](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)找到更多关于LaTeX 数学表达式的信息。

# Blockquotes (区块引用)
```
> Blockquotes are very handy in email to emulate reply text.
This line is part of the same quote.
This line is part of the same quote.
```
> Blockquotes are very handy in email to emulate reply text.
This line is part of the same quote.
This line is part of the same quote.
a
a
a

# Horizontal Rule (分割线)
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

```
* * *

***

*****

- - -

---------------------------------------
```
* * *

***

*****

- - -

---------------------------------------

# Line Breaks（换行符）
```
Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.
```
Here's a line for us to start with.


This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.

```MARKDOWN
This is a regular paragraph.

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

This is another regular paragraph.
```
This is a regular paragraph.

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

This is another regular paragraph.
