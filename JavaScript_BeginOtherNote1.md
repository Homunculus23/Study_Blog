# JavaScript Begin Other Note 1 JS 函数的执行时机

在 JS 中有一个奇特的`setTimeout()`，将它放在下面的函数中，能让结果变得很有趣：

```JS
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```

不了解`setTimeout()`的人，可能会认为上述函数的运行结果是 0、1、2、3、4、5，实际上它会打印出 6 个 6。

## 1.为什么上面的代码会打印出 6 个 6？

因为`setTimeout()`的逻辑是，执行完当前的所有代码后，立即执行`setTimeout()`里的代码。

而在文章开头的代码中，所谓“当前的所有代码”，就包含了整个 for 循环。即当 for 循环结束后`setTimeout()`里的代码才会被执行。

在 for 循环结束后，`setTimeout()`执行前，内存中有些什么呢？由于 for 循环执行了 6 次（i 为 0~5 总共 6 次），此时积累了 6 个等待执行的`setTimeout()`，同时还有值为 6 的 i。

终于轮到 6 个`setTimeout()`执行，它们把此时值为 6 的 i ，依次用`console.log(i)`打印了出来，于是，我们就看到了 6 个 6。

## 2.课后问题：还有什么其他方法可以打印出 0、1、2、3、4、5？

第一种方法是课堂上讲的 for let 配合：

```JS
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```

第二种方法，是利用**立即执行函数**的局部变量 j，来单独接受每个循环里 i 的值，然后令`setTimeout()`依次打印出 j。

```JS
let i = 0
for(i = 0; i!=6; i++){
  !function(){
    var j = i
    setTimeout(()=>{
      console.log(j)
    },0)
  }()
}
```

当然，我还无法理解原理，为什么立即执行函数跟内置`let i = 0`的效果一样？它们之间有什么关系？可惜，我没有时间深究。

第三种方法，是将`i++`的流程移动到`setTimeout()`里面，但是需要在 for 循环结束后将 i 重置为 0：

```JS
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i++)
  },0)
}
i = 0
```

第三种方法缺乏泛用性。
