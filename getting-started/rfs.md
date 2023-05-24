# RFS

Bootstrap的大小调整引擎响应性地缩放常见的CSS属性，以便更好地利用视口和设备之间的可用空间。

Bootstrap的副项目RFS是一个单位大小调整引擎，最初是为了调整字体大小而开发的(因此它是Responsive font size的缩写)。现在，RFS能够用单位值重新缩放大多数CSS属性，比如 `margin`, `padding`, `border-radius`，甚至是 `box-shadow`。

## 什么是 RFS？

该机制根据浏览器视口的尺寸自动计算适当的值。它将被编译成`calc()`函数，其中混合了`rem`和viewport单元，以启用响应性缩放行为。

## 使用 RFS

这些mixins包含在Bootstrap中，一旦你包含了Bootstrap的scss就可以使用。如果需要，RFS也可以[独立安装](https://github.com/twbs/rfs/tree/v9.0.6#installation)。

### 使用mixins

`rfs()` mixin有以下简称:`font-size`、`margin`、`margin-top`、`margin-right`、`margin-bottom`、`margin-left`、`padding`、`padding-top`、`padding-right`、`padding-bottom`和`padding-left`。请参阅下面的示例获取源Sass和编译后的CSS。

### 使用函数

## 扩展的文档