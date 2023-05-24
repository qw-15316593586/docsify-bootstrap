# CSS变量

使用 Bootstrap 的 CSS 自定义属性进行快速和前瞻性的设计和开发。

Bootstrap 在其已编译的 CSS 中包含了许多 [CSS 自定义属性（变量）](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)，用于实时修改它们的值而，无需重新编译 Sass。 当在浏览器的检查器、代码沙箱或通用原型设计中工作时，这些提供了对常用值的轻松访问，例如我们的主题颜色、断点和主要字体堆栈。

我们所有的自定义属性都以 `bs-` 为前缀，以避免与第三方 CSS 冲突。

## 根变量

以下是我们引入的变量（注意 `:root` 是必需的），可以在加载 Bootstrap 的 CSS 的任何地方访问。 它们位于我们的 `_root.scss` 文件中，并包含在我们编译的 dist 文件中。

```        
:root {
  --bs-blue: #0d6efd;
  --bs-indigo: #6610f2;
  --bs-purple: #6f42c1;
  --bs-pink: #d63384;
  --bs-red: #dc3545;
  --bs-orange: #fd7e14;
  --bs-yellow: #ffc107;
  --bs-green: #198754;
  --bs-teal: #20c997;
  --bs-cyan: #0dcaf0;
  --bs-white: #fff;
  --bs-gray: #6c757d;
  --bs-gray-dark: #343a40;
  --bs-gray-100: #f8f9fa;
  --bs-gray-200: #e9ecef;
  --bs-gray-300: #dee2e6;
  --bs-gray-400: #ced4da;
  --bs-gray-500: #adb5bd;
  --bs-gray-600: #6c757d;
  --bs-gray-700: #495057;
  --bs-gray-800: #343a40;
  --bs-gray-900: #212529;
  --bs-primary: #0d6efd;
  --bs-secondary: #6c757d;
  --bs-success: #198754;
  --bs-info: #0dcaf0;
  --bs-warning: #ffc107;
  --bs-danger: #dc3545;
  --bs-light: #f8f9fa;
  --bs-dark: #212529;
  --bs-primary-rgb: 13, 110, 253;
  --bs-secondary-rgb: 108, 117, 125;
  --bs-success-rgb: 25, 135, 84;
  --bs-info-rgb: 13, 202, 240;
  --bs-warning-rgb: 255, 193, 7;
  --bs-danger-rgb: 220, 53, 69;
  --bs-light-rgb: 248, 249, 250;
  --bs-dark-rgb: 33, 37, 41;
  --bs-white-rgb: 255, 255, 255;
  --bs-black-rgb: 0, 0, 0;
  --bs-body-color-rgb: 33, 37, 41;
  --bs-body-bg-rgb: 255, 255, 255;
  --bs-font-sans-serif: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", "Liberation Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --bs-font-monospace: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
  --bs-gradient: linear-gradient(180deg, rgba(255, 255, 255, 0.15), rgba(255, 255, 255, 0));
  --bs-body-font-family: var(--bs-font-sans-serif);
  --bs-body-font-size: 1rem;
  --bs-body-font-weight: 400;
  --bs-body-line-height: 1.5;
  --bs-body-color: #212529;
  --bs-body-bg: #fff;
}
```

## 组件变量

我们也开始使用自定义属性作为各种组件的局部变量。 这样我们可以减少编译的 CSS，确保样式不会在嵌套表等地方继承，并允许在 Sass 编译后对 Bootstrap 组件进行一些基本的重新设置和扩展。

查看我们的表格文档，[了解我们如何使用 CSS 变量](https://getbootstrap.com/docs/5.1/content/tables/#how-do-the-variants-and-accented-tables-work)。

我们还在我们的网格中使用 CSS 变量——主要用于沟槽(gutters)——未来会有更多的组件使用。

## 示例

CSS 变量提供了与 Sass 变量类似的灵活性，但在提供给浏览器之前不需要编译。 例如，这里我们使用 CSS 变量重置页面的字体和链接样式。

```
body {
    font: 1rem/1.5 var(--bs-font-sans-serif);
}
a {
    color: var(--bs-blue);
}  
```

## 网格断点

虽然我们将网格断点引入为 CSS 变量（xs 除外），但请注意 CSS 变量在媒体查询中不起作用。 这是 CSS 规范中变量的设计，但在未来几年可能会随着对 env() 变量的支持而改变。 查看此 [Stack Overflow 答案](https://stackoverflow.com/a/47212942) 以获得一些有用的链接。 同时，您可以在其他 CSS 情况以及 JavaScript 中使用这些变量。