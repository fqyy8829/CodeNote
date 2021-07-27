[toc]

&emsp;&emsp;HTML的全称是<font color=orange> **Hyper Text Markup Language（超文本标记语言）** </font>，HTML只是一种标记语言，简单地说，HTML文件就是<font color=orange> **普通文本 + HTML标记（也称为HTML标签）** </font>，不同的HTML标记能表示不同的效果。

# HTML5 的优势

<font color=skyblue>**1. 解决了跨浏览器问题**</font>

&emsp;&emsp;在 HTML5 之前，各大浏览器对 HTML 、JavaScript 的支持很不统一，这样就造成同一个页面在不同浏览器中的表现不同。HTML5 的目标就是详细分析各个浏览器所具有的的功能，并以此为基础制订一个通用规范，并要求各浏览器能支持这个通用标准。如果各大浏览器都能统一遵守 HTML5 规范，以后开发 HTML + CSS + JavaScript 页面就会变得更加轻松。

<font color=skyblue>**2. 部分代替了原来的JavaScript**</font>

&emsp;&emsp;HTML5 新增了一些非常实用的功能，这些功能可以部分替换 JavaScript ，只需要通过为标签添加一些属性即可。比如打开页面后立即让某个单行文本获得输入焦点，在 HTML5 之前需要使用 JavaScript 来实现：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <input type="text" id="text">
    <script>
        document.getElementById('text').focus();
    </script>
</body>
</html>
```

&emsp;&emsp;而在 HTML5 中，只需要通过一个属性即可：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <input type="text" id="text" autofocus>
</body>
</html>
```

<font color=skyblue>**3. 更明确的语义支持**</font>

&emsp;&emsp;在 HTML5 以前，如果要表达一个文档结构，可能只能通过 div 元素来实现：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <div id="header"></div>
    <div id="nav"></div>
    <div id="article">
        <div id="section"></div>
    </div>
    <div id="aside"></div>
    <div id="footer"></div>
</body>
</html>
```

&emsp;&emsp;HTML5 则为上面的页面布局提供了更明确的语义元素：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <header></header>
    <nav></nav>
    <article>
        <section></section>
    </article>
    <aside></aside>
    <footer></footer>
</body>
</html>
```

<font color=skyblue>**4. 增强了Web应用程序的功能**</font>

&emsp;&emsp;一直以来都是客户端从服务器下载 HTML 页面数据，浏览器负责呈现这些 HTML 页面数据。出于对客户机安全性的考虑，以前的 HTML 在安全性方面确实做得足够安全。当 HTML 页面做得太安全之后，开发就需要通过 JavaScript 等其他方法来增加 HTML 的功能。为了弥补这种不足，HTML5 规范增加了不少新的 API ，如 HTML5 新增的本地存储 API 、文件访问 API 等极大地增强了 Web 应用程序的功能。

# HTML5 的基本结构和语法变化

&emsp;&emsp;HTML5 并不是对 HTML4 、 XHTML 的革命，也就是说按 HTML4 、 XHTML 开发的 HTML 网页同样可用。 HTML5 完全遵守以下3点规则：

+ <font color=orange>**兼容性：**</font> HTML5 在老版本的浏览器上也可以正常运行
+ <font color=orange>**实用性：**</font> HTML5 内部并没有特别复杂的功能，它只封装了那些常用的简单功能
+ <font color=orange>**非革命性的发展：**</font> HTML5 并不是革命性的发展，它只是一种 "妥协式" 的规范

##  HTML5 的基本结构

&emsp;&emsp;HTML5 并不是规范优先的设计，它照顾了互联网上大量不规范的 HTML 页面，一份基本的 HTML5 文档结构如下：

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>页面标题</title>
</head>
<body>
    页面内容部分
</body>
</html>
```

## 标签不再区分大小写

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>页面标题</title>
</head>
<body>
    <P>一段文本</P>
    <p>一段文本</p>
</body>
</html>
```

> <font color=red> **注意：** </font> 不要在 &lt;html&gt; 和 &lt;head&gt; 标签之间、 &lt;/head&gt; 和 &lt;body&gt; 之间和 &lt;/body&gt; 和 &lt;/html&gt; 之间插入任何内容。

## 元素可以省略结束标签

&emsp;&emsp;HTML5 中的省略标签可以分为如下3种情况：

<font color=skyblue>**1. 空元素语法的元素**</font>

&emsp;&emsp;空元素语法的元素有：<font color=orange> **area、base、br、col、command、embed、hr、img、input、keygen、link、mata、param、source和wbr** </font>。这些空元素不允许将开始标签和结束标签分开定义，如下面的写法是错误的：

```html
<img src="a.gif"></img>
```

&emsp;&emsp;img 元素应该是空元素，因此它的写法：

```html
<img src="a.gif" />
<!-- HTML5也可以写成下面形式 -->
<img src="a.gif" >
```

<font color=skyblue>**2. 可以省略结束标签的元素**</font>

&emsp;&emsp;可以省略结束标签的元素有：<font color=orange> **colgroup、dt、dd、li、optgroup、option、p、rt、rp、thead、tbody、tfoot、tr、td和th** </font>：

```html
<p> 一段文本
```

<font color=skyblue>**3. 可以省略全部标签的元素**</font>

&emsp;&emsp;可以省略全部标签的元素有：<font color=orange> **html、head、body、colgroup、tbody** </font>：

```html
<!DOCTYPE html>
<title>title</title>
<p>
<ol>
<li>aaaaa
<li>aaaaa
<li>aaaaa
<img src="a.png" alt="a">
</ol>
```

## 支持 boolean 值的属性

&emsp;&emsp;HTML5 允许部分 "标志性" 的属性可以省略属性值，如下面的几个语句的效果是一样的：

```html
<input checked="true" type="checkbox" />
<input checked="checked" type="checkbox" />
<input checked="" type="checkbox" />
<input checked type="checkbox" />
```

&emsp;&emsp;如果完全省略这些属性，那么该属性的属性值相当于 false ，下面的表格中列出了 HTML5 允许省略属性值的属性：

HTML5 | XHTML
-|-
checked | checked="checked"
readonly | readonly="readonly"
disabled | disabled="disabled"
selected | selected="selected"
defer | defer="defer"
ismap | ismap="ismap"
nohref | nohref="nohref"
noshade | noshade="noshade"
nowrap | nowrap="nowrap"
multiple | multiple="multiple"
noresize | noresize="noresize"

## 允许属性值不使用引号

&emsp;&emsp;HTML5 允许直接给出属性值，即使不放在引号中也是正确的：

```html
<img src=a.png alt=测试>
```

> <font color=red>**注意：**</font>如果某个属性的属性值包含空格等容易引起浏览器混淆的属性值，那么建议还是把引号加上。
