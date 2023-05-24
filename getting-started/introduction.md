
# 开始使用Bootstrap

Bootstrap是一个功能强大、功能丰富的前端工具包。在几分钟内构建任何东西的原型到产品。

## 快速启动

通过CDN包括Bootstrap的生产的CSS和JavaScript开始，而不需要任何构建步骤。在这个[Bootstrap CodePen](https://codepen.io/team/bootstrap/pen/qBamdLj)演示中看看它的实际情况。

1. 在项目根目录下创建一个新的`index.html`文件。包括`<meta name="viewport">`标签，以及在移动设备中适当的响应行为。

    ```
    <!doctype html>
    <html lang="en">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Bootstrap demo</title>
    </head>
    <body>
        <h1>Hello, world!</h1>
    </body>
    </html>
    ```
    
2. 包括Bootstrap的CSS和JS。在CSS的`<head>`中放置`<link>`标签，在结束的`</body>`之前放置`<script>`标签，用于JavaScript包(包括用于定位下拉菜单、弹出窗口和工具提示的Popper)。

    ```
    <!doctype html>
    <html lang="en">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Bootstrap demo</title>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
    </head>
    <body>
        <h1>Hello, world!</h1>
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js" integrity="sha384-/mhDoLbDldZc3qpsJHpLogda//BVZbgYuw6kof4u2FrCedxOtgRZDTHgHUhOCVim" crossorigin="anonymous"></script>
    </body>
    </html>
    ```

    你也可以分别包括`Popper`和我们的JS。如果您不打算使用下拉菜单、弹出窗口或工具提示，可以通过不包括Popper来节省一些字
    节。

    ```
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js" integrity="sha384-oBqDVmMz9ATKxIep9tiCxS/Z9fNfEXiDAYTujMAeBAsjFuCZSmKbSSUnQlmh/jp3" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.min.js" integrity="sha384-ep+dxp/oz2RKF89ALMPGc7Z89QFa32C8Uv1A3TcEK8sMzXVysblLA3+eJWTzPJzT" crossorigin="anonymous"></script>
    ```

3. 你好,世界!在您选择的浏览器中打开该页面，以查看您的bootstrap页面。现在，您可以通过创建自己的布局，添加数十个[组件](https://v5.bootcss.com/docs/components/buttons/)并使用我们的[官方示例](https://v5.bootcss.com/docs/examples/)来开始使用Bootstrap构建。

## CDN links

作为参考，这里是我们的主要CDN链接。

| Description | URL |
| --- | --- |
| CSS | `https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css` |
| JS | `https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js` |

您还可以使用CDN获取目录页中列出的[任何其他构建](https://v5.bootcss.com/docs/getting-started/contents/)。

## 下一步

- 阅读更多关于Bootstrap使用的一些重要全局环境设置的信息。
- 在我们的内容部分阅读Bootstrap中包含的内容以及下面需要JavaScript的组件列表。
- 需要更多的动力吗?考虑使用Bootstrap构建，通过包管理器包含源文件。
- 希望使用Bootstrap作为一个模块与`<script type="module">`?请参考我们使用Bootstrap作为模块一节。

## JS组件

想知道哪些组件需要JavaScript和Popper吗?单击下面的显示组件链接。如果您不确定一般的页面结构，请继续阅读示例页面模板。

显示需要JavaScript的组件
- Alerts提醒
- 用于切换状态和复选框/单选的按钮
- 用于所有幻灯片行为、控件和指示器的旋转木马
- 折叠以切换内容的可见性
- 用于显示和定位的下拉菜单(也需要Popper)
- 用于显示、定位和滚动行为的模态
- Navbar用于扩展我们的Collapse和Offcanvas插件来实现响应行为
- 使用Tab插件切换内容窗格的导航
- 用于显示、定位和滚动行为的画布
- Scrollspy用于滚动行为和导航


## 重要的全局变量

Bootstrap使用了一些重要的全局样式和设置，所有这些都几乎完全面向跨浏览器样式的规范化。让我们开始吧。

### HTML5 doctype

Bootstrap需要使用HTML5文档类型。没有它，你会看到一些时髦和不完整的造型

```
<!doctype html>
<html lang="en">
  ...
</html>
```

### 响应式元标签

Bootstrap首先针对移动设备开发，这是一种策略，我们首先针对移动设备优化代码，然后根据需要使用CSS媒体查询扩展组件。为了确保所有设备的正确渲染和触摸缩放，在`<head>`中添加响应式视口元标签。

`<meta name="viewport" content="width=device-width, initial-scale=1">`

您可以在快速入门中看到一个[实际的示例](https://v5.bootcss.com/docs/getting-started/introduction/#quick-start)。

### 盒模型

为了在CSS中更直接地调整大小，我们将全局`box-sizing`值从`content-box`切换到`border-box`。这确保了`padding`不会影响元素的最终计算宽度，但它可能会导致一些第三方软件(如谷歌Maps和谷歌Custom Search Engine)出现问题。

在极少数情况下，您需要重写它，使用如下内容:

```
.selector-for-some-widget {
  box-sizing: content-box;
}
```

在上面的代码片段中，嵌套元素(包括通过`::before`和`::after`生成的内容)都将继承为`.selector-for-some-widget`指定的`box-sizing`。

了解更多关于[框模型和大小的CSS技巧](https://css-tricks.com/box-sizing/)。

### Reboot

为了改进跨浏览器呈现，我们使用Reboot来纠正浏览器和设备之间的不一致，同时为常见的HTML元素提供稍微固执的重置。

## 社区

保持对Bootstrap开发的最新了解，并通过这些有用的资源与社区联系。