# 容器

容器是 Bootstrap 的基本构建块，它在给定的设备或视口中包含、填充和对齐您的内容。

## 工作原理

容器是 Bootstrap 中最基本的布局元素，在使用我们的默认网格系统时是必需的。 容器用于包含、填充和（有时）将内容居中。 虽然容器可以嵌套，但大多数布局不需要嵌套容器。

Bootstrap 包含三种不同的容器：

- `.container`，它在每个响应式断点处设置一个 `max-width`
- `.container-fluid`，所有断点宽度都为100%
- `.container-{breakpoint}`，即 `width: 100%` 直到指定断点

下表列出了 `max-width` 在每种容器( `.container` 和 `.container-fluid` )的比较。

在我们的[网格示例](https://getbootstrap.com/docs/5.1/examples/grid/#containers)中查看它们并进行比较。

|  | Extra small <br> <576px | Small <br> ≥576px | Medium <br> ≥768px | Large <br> ≥992px | X-Large <br> ≥1200px | XX-Large <br> ≥1400px |
| --- | --- | --- | --- | --- | --- | --- |
| `.container` | 100% | 540px | 720px | 960px | 1140px | 1320px |
| `.container-sm` | 100% | 540px | 720px | 960px | 1140px | 1320px |
| `.container-md` | 100% | 100% | 720px | 960px | 1140px | 1320px |
| `.container-lg` | 100% | 100% | 100% | 960px | 1140px | 1320px |
| `.container-xl` | 100% | 100% | 100% | 100% | 1140px | 1320px |
| `.container-xxl` | 100% | 100% | 100% | 100% | 100% | 1320px |
| `.container-fluid` | 100% | 100% | 100% | 100% | 100% | 100% |

## 默认容器

我们默认的 `.container` 类是一个响应式、固定宽度的容器，这意味着它的 `max-width` 在每个断点处都会发生变化。

```html
<div class="container">
  <!-- Content here -->
</div>
```

## 响应式容器

响应式容器允许您指定一个 100% 宽的类，直到达到指定的断点，之后我们为每个更高的断点应用对应的 `max-width`。 例如，`.container-sm` 的宽度为 100%，直到到达 `sm` 断点，它将随着到达 `md`，`lg`、`xl` 和 `xxl` 向上扩展。

```html
<div class="container-sm">100% wide until small breakpoint</div>
<div class="container-md">100% wide until medium breakpoint</div>
<div class="container-lg">100% wide until large breakpoint</div>
<div class="container-xl">100% wide until extra large breakpoint</div>
<div class="container-xxl">100% wide until extra extra large breakpoint</div>
```

## 流容器

将 `.container-fluid` 用于全宽容器。

```html
<div class="container-fluid">
  ...
</div>
```

## Sass

如上所示，Bootstrap 会生成一系列预定义的容器类来帮助您构建您想要的布局。 您可以通过修改支持它们的 Sass 映射（在 `_variables.scss` 中找到）来自定义这些预定义的容器类：

```scss
$container-max-widths: (
  sm: 540px,
  md: 720px,
  lg: 960px,
  xl: 1140px,
  xxl: 1320px
);
```

除了自定义 Sass，您还可以使用我们的 Sass mixin 创建自己的容器。

```scss
// Source mixin
@mixin make-container($padding-x: $container-padding-x) {
  width: 100%;
  padding-right: $padding-x;
  padding-left: $padding-x;
  margin-right: auto;
  margin-left: auto;
}

// Usage
.custom-container {
  @include make-container();
}
```