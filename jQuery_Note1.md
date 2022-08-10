# jQuery Note 1 初见 jQuery

write less, do more.

这句话现在还是在 jQuery 官网首页最醒目的地方，这凸显出了 jQuery 最大的优点：

简单易用，节省时间。

我在初步学习后认为，这是 jQuery 盛行 16 年不衰的根本原因。

## 1.选择网页元素

jQuery 核心思想：提供一个函数，接受一个选择器，获取到所有相关元素，但是不会返回这些元素本身，而是返回一个可以操作相关元素的对象。

```JS
$(document) //选择整个文档对象
$('#myId') //选择ID为myId的网页元素
$('div.myClass') // 选择class为myClass的div元素
$('input[name=first]') // 选择name属性等于first的input元素
$('a:first') //选择网页中第一个a元素
$('tr:odd') //选择表格的奇数行
$('#myForm :input') // 选择表单中的input元素
$('div:visible') //选择可见的div元素
$('div:gt(2)') // 选择所有的div元素，除了前三个
$('div:animated') // 选择当前处于动画状态的div元素
```

jQuery 内部的所有参数都形成闭包，人们无法直接操作 jQuery 的内部数据，以此来达成封装的效果。

我刚开始学的时候疑惑过，为什么选择器不是类似于`jQuery('.test')`的格式？原来，为了进一步简化操作，jQuery 甚至选择了在使用中“消灭自己”——他们是通过将 window.jQuery 赋给 window.$做到的：

```JS
window.$ = window.jQuery = function(...){...}
```

## 2.链式

每一步的 jQuery 操作，返回的都是一个 jQuery 对象，所以不同操作可以连在一起，一次性进行多项操作，这就是链式：

```JS
$('#test')
    .addClass('red')
    .find('.child')
    .addClass('blue')
```

jQuery 为了方便进行连续操作，甚至还提供了一个`.end()`，使得操作对象可以后退：

```JS
$('#test')
    .addClass('red')
    .find('.child')
    .addClass('blue')
    .end()
    .each((div) => console.log(div))
```

此外，在 jQuery 中还有很多出色的技巧，比如被返回给使用者的对象，是一个匿名对象。类似的东西太多，我暂时就不一一说明了。

至此做一个小结：**所谓的 jQuery 风格，就是基于实用，将可以省略的中间变量、中间代码全部省略，只留下必要的信息**。

## 3.一些常用方法及其格式

暂时没有统计事件操作和特殊效果。

### 3.1 增/删

```JS
//增
$('<div><span>1</span></div>')  //创建div
    .appendTo(document.body)    //插入body中
```

```JS
//删
$('.red').empty() //移除 .red 的所有子元素
$('.red').remove()  //移除 .red
```

### 3.2 改(读)

jQuery 基于重载的思想，为改写的方法实现了多重功能。同样是包装函数，传了需要改的参数，就是改写；没有传需要改的参数，就是读。

```JS
//?代表区分改/读的参数
$('.red').text(?)   //改/读.red的文本内容
$('.red').html(?)   //改/读HTMl内容
$('.red').attr('title',?)   //改/读title属性
$('.red').css(?)    //改/读style
$('.red').addClass({background:'blue'})  //改写style
$('.red').on('click', fn)   //为.red添加click监听，并绑定fn操作
$('.red').off('click', fn)  //为.red移除click监听和绑定的fn操作
```

### 3.3 查

```JS
$('.red').find('.red')  //查找 .red 里的 .red 元素
$('.red').parent()  //获取父元素
$('.red').children()    //获取子元素
$('.red').siblings()    //获取兄弟元素
$('.red').index()   //获取自身所在的下标
$('.red').next()    //获取下一个元素
$('.red').prev()    //获取上一个元素
$('.red').each(fn)  //遍历 .red ，并对每个元素执行fn
```

### 3.4 移动元素

```JS
$('.red').insertAfter($('.blue'));  //将.red元素移动到.blue后面
$('.red').after($('.blue'));    //将.red元素移动到.blue前面
```
