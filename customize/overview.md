了解如何使用 Sass、全局选项、颜色系统等来主题化、自定义和扩展 Bootstrap。

[Sass](https://getbootstrap.com/docs/5.3/customize/sass/)

利用我们的 Sass 源代码文件来使用变量、映射(maps)、混合(mixins)和函数(function)。

[全局选项](https://getbootstrap.com/docs/5.3/customize/options/)

使用内置变量自定义 Bootstrap 以轻松切换全局 CSS 首选项。

[Color](https://getbootstrap.com/docs/5.3/customize/color/)

了解和定制支持整个工具包的颜色系统。

[颜色模式](https://getbootstrap.com/docs/5.3/customize/color-modes/)

探索我们的默认亮模式和新的暗模式，或创建自定义的颜色模式自己。

[组件](https://getbootstrap.com/docs/5.3/customize/components/)

了解我们如何使用基类和修饰类以构建几乎所有组件。

[CSS 变量](https://getbootstrap.com/docs/5.3/customize/css-variables/)

使用 Bootstrap 的 CSS 自定义属性进行快速和前瞻性的设计和开发。

[优化](https://getbootstrap.com/docs/5.3/customize/optimize/)

保持项目精简、响应迅速且可维护，以便提供最佳体验。


## 概述
有多种方法可以定制Bootstrap。您的最佳路径取决于您的项目、构建工具的复杂性、您正在使用的Bootstrap版本、浏览器支持等等。

我们首选的两种方法是:

- 通过包管理器使用Bootstrap，这样你就可以使用和扩展我们的源文件。
- 使用Bootstrap编译的发行文件或jsdeliver，这样你就可以添加或覆盖Bootstrap的样式。

虽然我们不能在这里详细介绍如何使用每个包管理器，但我们可以提供一些关于在您自己的Sass编译器中使用Bootstrap的指导。

对于那些想要使用分发文件的人，请查看入门页面，了解如何包含这些文件和一个示例HTML页面。然后，查阅文档，了解您想要使用的布局、组件和行为。

当你熟悉Bootstrap时，继续探索本节，了解更多关于如何利用我们的全局选项，使用和更改我们的颜色系统，如何构建我们的组件，如何使用我们不断增长的CSS自定义属性列表，以及如何在使用Bootstrap构建时优化代码的细节。

## csp和嵌入式svg

几个Bootstrap组件在我们的CSS中包含嵌入式svg，以便跨浏览器和设备一致且轻松地为组件设置样式。对于具有更严格CSP配置的组织，我们已经记录了嵌入式svg的所有实例(所有这些实例都通过背景图像应用)，因此您可以更彻底地检查您的选项。

*   [Accordion](https://getbootstrap.com/docs/5.3/components/accordion/)
*   [Carousel controls](https://getbootstrap.com/docs/5.3/components/carousel/#with-controls)
*   [Close button](https://getbootstrap.com/docs/5.3/components/close-button/) (used in alerts and modals)
*   [Form checkboxes and radio buttons](https://getbootstrap.com/docs/5.3/forms/checks-radios/)
*   [Form switches](https://getbootstrap.com/docs/5.3/forms/checks-radios/#switches)
*   [Form validation icons](https://getbootstrap.com/docs/5.3/forms/validation/#server-side)
*   [Navbar toggle buttons](https://getbootstrap.com/docs/5.3/components/navbar/#responsive-behaviors)
*   [Select menus](https://getbootstrap.com/docs/5.3/forms/select/)

根据社区对话，在您自己的代码库中解决这个问题的一些选项包括用本地托管资产替换url，删除图像并使用内联图像(并非在所有组件中都可能)，以及修改CSP。我们的建议是仔细检查您自己的安全策略，并在必要时决定最佳的前进路径。
