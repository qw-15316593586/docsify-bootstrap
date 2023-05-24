# 优化

让您的项目保持精简、响应迅速且可维护，这样您就可以提供最佳体验并专注于更重要的工作。

## 了解 Sass 引入

在使用 Sass 时，优化 Bootstrap 仅通过 `@import` 引入您需要的组件。 您最大的优化可能来自 `bootstrap.scss` 的 `Layout & Components` 部分。

```
// Configuration
@import "functions";
@import "variables";
@import "mixins";
@import "utilities";

// Layout & components
@import "root";
@import "reboot";
@import "type";
@import "images";
@import "containers";
@import "grid";
@import "tables";
@import "forms";
@import "buttons";
@import "transitions";
@import "dropdown";
@import "button-group";
@import "nav";
@import "navbar";
@import "card";
@import "accordion";
@import "breadcrumb";
@import "pagination";
@import "badge";
@import "alert";
@import "progress";
@import "list-group";
@import "close";
@import "toasts";
@import "modal";
@import "tooltip";
@import "popover";
@import "carousel";
@import "spinners";
@import "offcanvas";
@import "placeholders";

// Helpers
@import "helpers";

// Utilities
@import "utilities/api";
```

如果您不使用组件，请将其注释掉或完全删除。 例如，如果您不使用轮播(carousel)，请删除该引入以使编译后的 CSS 节省一些文件大小。 请记住，Sass 引入之间存在一些依赖关系，这可能会使删除引入变得更加困难。

## 了解 JavaScript

Bootstrap 的 JavaScript 包括我们的主要分发(dist)文件（`bootstrap.js` 和 `bootstrap.min.js`）中的每个组件，甚至我们的主要依赖项（Popper）与我们的打包文件（`bootstrap.bundle.js` 和 `bootstrap.bundle.min.js`）也包含所有组件。 当您通过 Sass 进行自定义时，请务必删除相关的 JavaScript。

例如，假设您使用自己的 JavaScript 打包器，如 Webpack 或 Rollup，您只需引入您计划使用的 JavaScript。 在下面的示例中，我们展示了如何仅包含我们的模态框(modal) JavaScript：

```
// Import just what we need

// import 'bootstrap/js/dist/alert';
// import 'bootstrap/js/dist/button';
// import 'bootstrap/js/dist/carousel';
// import 'bootstrap/js/dist/collapse';
// import 'bootstrap/js/dist/dropdown';
import 'bootstrap/js/dist/modal';
// import 'bootstrap/js/dist/offcanvas';
// import 'bootstrap/js/dist/popover';
// import 'bootstrap/js/dist/scrollspy';
// import 'bootstrap/js/dist/tab';
// import 'bootstrap/js/dist/toast';
// import 'bootstrap/js/dist/tooltip';
```

这样，您就不会包含任何您不打算使用的如按钮、轮播(carousels)和工具(tooltips)提示等组件的 JavaScript。 如果您要引入下拉菜单(dropdowns)、工具提示(tooltips)或弹出框(popovers)，请务必在 `package.json` 文件中列出 Popper 依赖项。

`bootstrap/js/dist` 中的文件使用默认导出，因此如果您想使用其中之一，您必须执行以下操作：

```
import Modal from 'bootstrap/js/dist/modal'

const modal = new Modal(document.getElementById('myModal'))
```

## Autoprefixer .browserslistrc

Bootstrap 依赖 Autoprefixer 自动将浏览器前缀添加到某些 CSS 属性。 前缀由我们的 `.browserslistrc` 文件指定，该文件位于 Bootstrap 仓库的根目录中。 自定义此浏览器列表并重新编译 Sass 将自动从编译的 CSS 中删除一些 CSS，如果该浏览器或版本存在唯一的前缀。


## 删除未使用的 CSS

需要有关此部分的帮助，请考虑打开 PR。 谢谢！

虽然我们没有 Bootstrap 使用 PurgeCSS 的示例，但社区已经编写了一些有用的文章和演练。 以下是一些选项：

- [https://medium.com/dwarves-foundation/remove-unused-css-styles-from-bootstrap-using-purgecss-88395a2c5772](https://medium.com/dwarves-foundation/remove-unused-css-styles-from-bootstrap-using-purgecss-88395a2c5772)
- [https://lukelowrey.com/automatically-removeunused-css-from-bootstrap-or-other-frameworks/](https://lukelowrey.com/automatically-removeunused-css-from-bootstrap-or-other-frameworks/)

最后，这篇关于未使用 CSS 的 [CSS 技巧文章](https://css-tricks.com/how-do-you-remove-unused-css-from-a-site/)展示了如何 使用 PurgeCSS 和其他类似工具。

## 压缩和 gzip

只要有可能，请务必压缩您提供给访问者的所有代码。 如果您使用的是 Bootstrap 分发文件，请尝试使用压缩版本（由 `.min.css` 和 `.min.js` 后辍名表示）。 如果您使用自己的构建系统从源代码构建 Bootstrap，请确保为 HTML、CSS 和 JS 实现自己的压缩器。

## 没有换行的文件

虽然缩小和使用压缩似乎已经足够了，但去掉您的文件的换行也是使您的网站得到充分优化和足够快的一大步。

如果您在 Google Chrome 中使用 [Lighthouse](https://developers.google.com/web/tools/lighthouse/) 插件，那么您可能偶然发现了 FCP。 [The First Contentful Paint](https://web.dev/fcp/) 指标衡量从页面开始加载到页面内容的任何部分呈现在屏幕上的时间。

您可以通过推迟非关键的 JavaScript 或 CSS 来改进 FCP。 这意味着什么？ 简单地说，不需要在页面的第一次绘制中出现的 JavaScript 或样式表应该使用 `async` 或 `defer` 属性进行标记。

这可以确保稍后加载不太重要的资源并且不会阻塞第一次绘制。 另一方面，关键资源可以作为内联脚本或样式包含在内。

如果您想了解更多关于此的信息，已经有很多关于它的精彩文章：

- [https://web.dev/render-blocking-resources/](https://web.dev/render-blocking-resources/)
- [https://web.dev/defer-non-critical-css/](https://web.dev/defer-non-critical-css/)

## 启用 HTTPS

您的网站应该只能在生产环境中通过 HTTPS 连接访问。 HTTPS 提高了所有网站的安全性、隐私性和可用性，并且[不存在非敏感网络流量](https://https.cio.gov/everything/)之类的东西。 将您的网站配置为仅通过 HTTPS 提供服务的步骤因您的架构和网络托管服务提供商而异，因此超出了这些文档的范围。

通过 HTTPS 提供服务的站点还应该通过 HTTPS 连接访问所有样式表、脚本和其他资产。 否则，您将向用户发送[混合活动内容](https://developer.mozilla.org/en-US/docs/Web/Security/Mixed_content)，从而导致潜在的漏洞 更改依赖项可能会破坏站点。 这可能会导致安全问题和向用户显示的浏览器内警告。 无论您是从 CDN 获取 Bootstrap 还是自己提供服务，请确保仅通过 HTTPS 连接访问它。