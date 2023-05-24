# 布局工具

为了更快的移动友好和响应式开发，Bootstrap包含了许多实用程序类，用于显示、隐藏、对齐和间距内容。

## 更改 display

使用我们的[显示工具](https://getbootstrap.com/docs/5.1/utilities/display/)来响应地切换显示属性的公共值。将其与我们的网格系统、内容或组件混合，在特定的视口中显示或隐藏它们。

## Flexbox 选项

Bootstrap是用flexbox构建的，但并不是每个元素的显示都被更改为`display: flex`，因为这会增加许多不必要的覆盖，并意外地改变关键的浏览器行为。[我们的大多数组件](https://getbootstrap.com/docs/5.1/components/alerts/)都是在启用flexx的情况下构建的。

如果你需要将`display: flex`添加到元素中，请使用`.d-flex`或其中一个响应式变体(例如，`.d-sm-flex`)。您将需要这个类或显示值来允许使用额外的[flexbox工具](https://getbootstrap.com/docs/5.1/utilities/flex/)来调整大小、对齐、间距等。

## Margin and padding

使用`margin`和`padding` [spacing工具](https://getbootstrap.com/docs/5.1/utilities/spacing/)来控制元素和组件的间距和大小。Bootstrap包含一个6级的间隔工具等级，基于默认`$spacer`变量的`1rem`值。为所有视口选择值(例如，`.me-3`在LTR中为`margin-right: 1rem`)，或者选择响应的变体来针对特定的视口(例如，`.me-md-3`在LTR中为`margin-right: 1rem` -从`md`断点开始)。


## Toggle 可见性

当不需要切换显示时，您可以使用我们的[可见性工具](https://getbootstrap.com/docs/5.1/utilities/visibility/)切换元素的可见性。不可见的元素仍然会影响页面的布局，但在视觉上对访问者是隐藏的。

