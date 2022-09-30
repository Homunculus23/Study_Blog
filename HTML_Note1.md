# HTML 入门笔记 1

## 1.HTML 历史概览及网站勘误

1990 年左右，Tim Berners-Lee 发明了 WWW，同时发明了 HTML、HTTP、URL。
<br>李爵士自己写了第一个浏览器、第一个服务器，用自己写的浏览器访问了自己写的服务器。
<br>HTML 的全名是“超文本标记语言”（HyperText Markup Language）。最初的 HTML 只有 18 个标签，而最新的 HTML 已经有 110 个标签。
<br>无论是 w3school 还是 w3cschool （包括 2006 年设立的 W3C 中国办事处/中国区总部机构）都不是 W3C设立的官方组织。这些网站对 W3C 官方标准的解答经常有误或迟滞，至今最好的相关网站是 MDN。
<br>W3C 的全球官网是 w3.org，中国区官网为 chinaw3c.org。

## 2.HTML 基本组成

一个最简单的 HTML 网页如下：

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8" />
    <title>这是个空网页</title>
  </head>
  <body>
    里面什么也没有
  </body>
</html>
```

网页通常由标签、元素和属性组成，一个可运行的网页至少需要以下结构。
<br> `<!doctype>`是网页的第一个标签，表示文档类型，告诉浏览器如何解析网页。html 5 标准格式为：`<!DOCTYPE html>`。
<br> `<html>`是网页的顶层容器，即标签树结构的顶层节点，也称为根元素（root element），其他元素都是它的子元素。一个网页只能有一个`<html>`标签。该标签的 lang 属性，表示网页内容默认的语言。"zh-CN"是中文简体。
<br> `<head>`是一个容器标签，用于放置网页的元信息。它的内容不会出现在网页上，而是为网页渲染提供额外信息。
<br> `<meta>`用于设置或说明网页的元数据，必须放在`<head>`里面。一个`<meta>`标签就是一项元数据，网页可以有多个`<meta>`。`<meta>`标签约定放在`<head>`内容的最前面。
<br> `<title>`用于指定网页的标题，会显示在浏览器窗口的标题栏。
<br> `<body>`是一个容器标签，用于放置网页的主体内容。浏览器显示的页面内容，都放置在它的内部。它是`<html>`里的第二个子元素，紧跟在`<head>`后面。

## 3.常用表示章节的标签

- h1、h2...h6：用于包裹标题。
- header：顶部。
- main：主要内容。
- footer：底部。
- aside：旁支内容。
- section：用于包裹章节。
- article：一整篇文章。
- p：段落。
- div：划分块级元素，无语义。

## 4.全局属性

- class：类元素。如果不同元素的 class 属性值相同，就表示它们是一类的。class 属性可重复。
- id：与 class 用法完全相同，但 id 属性原则上不可重复。（比较坑的是，重复了也不报错，所以尽可能不要用。）
- contenteditable：用于更改用户修改内容的权限，默认状态不可编辑。
- hidden：用于隐藏页面元素。
- style：指定当前元素的 css 样式。
- tabindex：指定 Tab 键可选的页面元素，并进行排序。
- title：网页标题。

## 5.常用内容标签

- ol+li：顺序列表+列表的一项。
- ul+li：无序列表+列表的一项。
- dl+dt+dd：描述列表+描述对象+描述内容。
- pre：保留空格/回车/tab。
- code：编程用等宽字体（一般被包裹在 pre 内）。
- hr：分割线。
- br：回车。
- a：href 链接网址，target 指定打开窗口。
- em：强调（默认斜体）。
- strong：强调（默认粗体）。
- quote：引用（行结构）。
- blockquote：引用（块结构）。
