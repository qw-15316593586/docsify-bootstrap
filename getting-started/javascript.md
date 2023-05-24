# JavaScript

使用我们可选的JavaScript插件将Bootstrap带入生活。了解每个插件，我们的数据和编程API选项，以及更多。

## 单独加载或一次性加载所有

插件可以单独包含(使用Bootstrap的单独`js/dist/*.js`)，也可以一次性使用`Bootstrap .js`或缩小的`Bootstrap .min.js`(不要同时包含两者)。

如果你使用打包器(Webpack, Parcel, Vite…)，你可以使用UMD准备好的`/js/dist/*.js`文件。

## JavaScript框架的使用

虽然Bootstrap CSS可以与任何框架一起使用，但Bootstrap JavaScript与JavaScript框架(如React、Vue和Angular)并不完全兼容，这些框架都假定完全了解DOM。Bootstrap和框架都可能试图改变相同的DOM元素，从而导致诸如下拉菜单被卡在“打开”位置的错误。

对于那些使用这种类型框架的人来说，更好的选择是使用特定于框架的包，而不是Bootstrap JavaScript。以下是一些最受欢迎的选择:

*   React: [React Bootstrap](https://react-bootstrap.github.io/)
*   Vue: [BootstrapVue](https://bootstrap-vue.org/) (currently only supports Vue 2 and Bootstrap 4)
*   Angular: [ng-bootstrap](https://ng-bootstrap.github.io/)

## 使用Bootstrap作为模块

> 你自己试试吧!从[twbs/examples](https://github.com/twbs/examples/tree/main/sass-js-esm)存储库下载将Bootstrap用作ES模块的源代码和工作演示。您也可以在[StackBlitz](https://stackblitz.com/github/twbs/examples/tree/main/sass-js-esm?file=index.html)中打开示例。


我们提供了一个版本的Bootstrap构建为`ESM` (`Bootstrap.esm.js`和`Bootstrap.esm.min.js`)，它允许你在浏览器中使用Bootstrap作为一个模块，如果你的目标浏览器支持它。

```
<script type="module">
  import { Toast } from 'bootstrap.esm.min.js'

  Array.from(document.querySelectorAll('.toast'))
    .forEach(toastNode => new Toast(toastNode))
</script>
```

## 依赖关系

## 数据属性

## 选择器

## 事件

## 编程API

### 构造函数中的CSS选择器

### 异步函数和转换

#### 化学处理法

### 默认设置

## 方法和属性

## 洗手液

## 可选使用jQuery

### 无冲突

### jQuery事件

## 禁用JavaScript