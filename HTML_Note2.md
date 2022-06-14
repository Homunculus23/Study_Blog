# HTML 入门笔记 2 常用标签

## 1.a 标签的用法

`<a>`标签的作用是链接，常用于跳转到外部页面、内部锚点、邮箱和电话等。它可以是文字，也可以是图片等元素。
<br> `<a>` 标签一般有 4 个属性，分别是：href、target、download、rel。

- href：用于指向跳转的目标，有四种取值，分别是网址、路径、伪协议和 id。
- target：用于指定链接打开的位置，其中 \_self 是默认在当前窗口打开，\_blank 是创建一个新窗口打开，其他方式用得较少。\_top 和 \_parent 需要配合 iframe ，target 也可以自主命名。
- download：html 5 的新属性，用于下载网页或文件，但很多较旧的浏览器都不支持该属性。
- rel：一般固定用法是`rel=noopener`，与 target 或 JS 代码搭配使用，用于避免安全风险和一些 bug。

  以下是使用`<a>`标签的一个例子：

  ```
  <a href="//biying.com" target="xxx">超链接必应</a>
  <a href="//baidu.com" target="yyy">超链接百度</a>
  <div>
      <iframe src="" name="xxx"></iframe>
      <iframe src="" name="yyy"></iframe>
  </div>
  ```

## 2.table 标签的用法

`<table>`是一个块级容器标签，所有表格内容都要放在这个标签里面。
其中的常用子标签如下：

- thead、tbody、tfoot：都是 table 的一级子标签，分别表示表头、表体和表尾。这三个元素都是可选的。如果使用了`<thead>`，那么`<tbody>`和`<tfoot>`一定在`<thead>`的后面。如果使用了`<tbody>`，那么`<tfoot>`一定在`<tbody>`后面。
- tr：用于定义表格的一行。
- th、td：用于定义表格的单元格，分别表示标题单元格和数据单元格。

以下是使用 table 标签的一个例子：

```
<table>
        <thead>
            <tr>
                <th>英语</th>
                <th>翻译</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>hyper</td>
                <td>超级</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <td>空</td>
                <td>空</td>
            </tr>
        </tfoot>
 </table>
```

## 3.img 标签的用法

`<img>`标签用于发出 get 请求，展示一张图片。它是单独使用的，没有闭合标签，可以与前后文字放在同一行。
其中的常用属性如下：

- src：图片路径。
- alt：图片加载失败的说明。
- height/width：高/宽。当你只写高度时，宽度会自适应，反之亦然。一般情况下，为了避免图片变形，最好一个图片只用一个 width。
- onload/onerror：加载成功/失败。配合 function 使用，主要用于在图片加载失败时进行挽救，把默认的裂图替换成更美观的图。
- max-width:100% ：响应式，使图片贴合应用窗口尺寸，一般用于手机页面。

以下是使用 img 标签的一个例子：

```
<img id="xxx" src="Victoire.jpg" alt="维克托瓦尔礼服" width="800">
    <script>
        xxx.onload = function () {
            console.log('图片加载成功');
        }
        xxx.onerror = function () {
            console.log('图片加载失败');
            xxx.src = '/404.jpg';
        }
    </script>
```

## 4.form 标签

form 用来定义一个表单，发送 get/post 请求，然后刷新页面。其中的常用属性有 action、method、autocomplete、target、required 等，其中的常用标签有：input、button、textarea、select 等。

## 5.其他感想

第 10 课的内容真的非常丰富，在今天的讲课中还有很多内容无法在博客中提及，我的笔记已经尽可能的去繁就简，但是依然达到了 3000 多字，并且还伴有大量的图片。
<br>在查看网道 html 的时候，我更是看到许多上课时，方老师从来没有说过的标签和属性，更加感到学海无涯，也感到如果没有人指导，没有合理的课程安排，学习相关课程会遇到多大困难，会付出多少额外的精力。
