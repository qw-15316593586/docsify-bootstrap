# 可访问性

简要概述Bootstrap在创建可访问内容方面的功能和限制。

Bootstrap提供了一个易于使用的现成样式、布局工具和交互式组件框架，允许开发人员创建具有视觉吸引力、功能丰富和开箱即用的网站和应用程序。

## 概述和限制

使用 Bootstrap 所构建的任何项目的总体无障碍程度大部分取决于作者所使用的标记（markup）、附加的样式以及脚本。但是，如果这些都得到了正确的实施，则完全可以基于 Bootstrap 创建符合 [WCAG 2.1](https://www.w3.org/TR/WCAG/) (A/AA/AAA)、[Section 508](https://www.section508.gov/) 以及类似无障碍标准和要求的网站及应用程序。

### 结构化的标记

Bootstrap 的样式和布局能够适用于广泛的标记（markup）结构。本文档旨在为开发者提供最佳实践示例，以演示 Bootstrap 的用法并配以示例来说明语义化标记（markup），同时包含了对潜在的无障碍方面的问题的解决方法。

### 交互式组件

Bootstrap 的交互式组件（例如模态对话框、下拉菜单和自定义工具提示）都被设计为支持使用触控、鼠标和键盘的用户。通过使用相关的 [WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/) 中定义的角色（roles）和属性（attributes），这些组件还能够被使用辅助技术（例如屏幕阅读器）的用户所立即并操控。

由于 Bootstrap 的组件被专门设计地相当通用，因此，开发者需要添加额外的 ARIA 中定义的角色（roles）和属性（attributes）以及 JavaScript 代码，以便更准确地传达组件的确切性质和功能。这些通常在文档中有标注。

### 颜色对比

Bootstrap 调色板中的某些颜色的组合（被用在整个框架中，例如按钮变体、警告框变体、表单校验指示器等）在浅色背景下使用时，可能导致颜色对比度的 不足 （低于 WCAG 2.1 规定的文本颜色对比度为 4.5:1 和 WCAG 2.1 规定的非文本颜色对比度为 3:1 的建议值）。 我们鼓励开发者对具体颜色的使用进行测试，并在必要时手动修改/扩充这些默认的颜色，以确保有足够的颜色对比度。

### 视觉隐藏内容

对于在视觉上应该隐藏的、但仍然可以通过类似屏幕阅读器等辅助技术访问的内容，可以使用 `.visually-hidden` 类来设置样式。这在需要向非视觉用户传达额外视觉信息或线索（例如通过颜色来表达的含义）的情况下非常有用。

```
<p class="text-danger">
  <span class="visually-hidden">Danger: </span>
  This action is not reversible
</p>
```

对于需要在视觉上隐藏的交互式组件，例如传统的 “skip” 链接，请使用 `.visually-hidden-focusable` 类。这将确保该组件在获得焦点后（对于视觉良好但使用键盘的用户）是可见的。注意，与之前版本中的的 `.sr-only` 和 `.sr-only-focusable` 类不同的是，Bootstrap 5 中的 `.visually-hidden-focusable` 是一个独立的类，不能与 `.visually-hidden` 类一起使用。


### 动画减弱 

Bootstrap 包含了对 `prefers-reduced-motion` 媒体功能 的支持。在允许用户设置动画减弱（reduced motion）的浏览器/环境中，Bootstrap 中的大多数 CSS 过渡效果（例如，当模态对话框打开或关闭时，或者旋转木马（carousels）中的滑动动画）将被禁用，而有意义的动画效果（例如 spinners）将被减速。

在支持设置 `prefers-reduced-motion` 的浏览器上，如果用户 没有 明确表示它们希望动画减弱（即，设置为 `prefers-reduced-motion: no-preference`），Bootstrap 将使用 `scroll-behavior` 属性实现平滑滚动。

## 额外的资源