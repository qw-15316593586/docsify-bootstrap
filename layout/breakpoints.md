# 断点

断点是可自定义的宽度，它决定了在 Bootstrap 中响应式布局不同的设备或视口大小的布局行为。

## 核心概念

- **断点是响应式设计的基石。** 使用它们来控制您的布局何时需要适应特定的视口或设备尺寸。

- **使用媒体查询通过断点架构您的 CSS。** 媒体查询是 CSS 的一项功能，可让您根据一组浏览器和操作系统参数有条件地应用样式。 我们最常在媒体查询中使用 min-width。

- **我们的目标是移动优先和响应式设计。** Bootstrap 的 CSS 旨在应用最少的样式来使布局在最小的断点处工作，然后对样式进行分层以针对更大的设备调整该设计。 这样可以优化您的 CSS，缩短渲染时间，并为您的访问者提供出色的体验。

## 可用的断点

Bootstrap 包含六个默认断点，有时称为网格层(grid tiers)，用于响应式构建。 如果您使用我们的 Sass 源码文件，可以自定义这些断点。

| Breakpoint        | Class infix | Dimensions |
| ----------------- | ----------- | ---------- |
| X-Small           | _None_      | <576px     |
| Small             | `sm`        | ≥576px     |
| Medium            | `md`        | ≥768px     |
| Large             | `lg`        | ≥992px     |
| Extra large       | `xl`        | ≥1200px    |
| Extra extra large | `xxl`       | ≥1400px    |

选择能够舒适地容纳您的容器的断点。断点也代表了常见设备的尺寸或视口的尺寸——它们并不专门针对某个用例或设备。 这些断点分隔形成的尺寸范围为几乎任何设备提供了强大而一致的基础。

这些断点可以通过 Sass 自定义——你可以在我们的 `_variables.scss` 样式表的 Sass 映射中找到它们。

```
$grid-breakpoints: (
    xs: 0,
    sm: 576px,
    md: 768px,
    lg: 992px,
    xl: 1200px,
    xxl: 1400px
  );
```

有关如何修改Sass映射和变量的更多信息和示例，[请参阅Grid文档中的Sass部分](https://getbootstrap.com/docs/5.1/layout/grid/#sass)。


## 媒体查询

由于 Bootstrap 是为移动优先而开发的，因此我们使用了几个[媒体查询](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) 为我们的布局和界面创建合理的断点。 这些断点主要基于最小视口宽度，并允许我们随着视口的变化放大元素。

### 最小宽度

Bootstrap 主要使用以下媒体查询范围或断点，在我们的 Sass 源码中供我们的布局(layout)、网格系统(grid system)和组件(component)使用。


```scss
// Source mixins

// No media query necessary for xs breakpoint as it's effectively `@media (min-width: 0) { ... }`
@include media-breakpoint-up(sm) { ... }
@include media-breakpoint-up(md) { ... }
@include media-breakpoint-up(lg) { ... }
@include media-breakpoint-up(xl) { ... }
@include media-breakpoint-up(xxl) { ... }

// Usage

// Example: Hide starting at `min-width: 0`, and then show at the `sm` breakpoint
.custom-class {
  display: none;
}
@include media-breakpoint-up(sm) {
  .custom-class {
    display: block;
  }
}
```

这些 Sass mixin 使用 Sass 变量中声明的值，在我们编译的 CSS 中进行转换。 例如：

```scss
// X-Small devices (portrait phones, less than 576px)
// No media query for `xs` since this is the default in Bootstrap

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) { ... }

// X-Large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }

// XX-Large devices (larger desktops, 1400px and up)
@media (min-width: 1400px) { ... }
  
```

### 最大宽度

我们偶尔会使用相反方向的媒体查询（给定的屏幕尺寸或更小）：

```scss
// No media query necessary for xs breakpoint as it's effectively `@media (max-width: 0) { ... }`
  @include media-breakpoint-down(sm) { ... }
  @include media-breakpoint-down(md) { ... }
  @include media-breakpoint-down(lg) { ... }
  @include media-breakpoint-down(xl) { ... }
  @include media-breakpoint-down(xxl) { ... }
  
  // Example: Style from medium breakpoint and down
  @include media-breakpoint-down(md) {
    .custom-class {
      display: block;
    }
}
  
```

这些 mixin 采用前面声明的断点，从中减去 `.02px`，并将它们用作我们的 `max-width` 值。 例如：

```scss
// `xs` returns only a ruleset and no media query
// ... { ... }
  
// `sm` applies to x-small devices (portrait phones, less than 576px)
@media (max-width: 575.98px) { ... }

// `md` applies to small devices (landscape phones, less than 768px)
@media (max-width: 767.98px) { ... }

// `lg` applies to medium devices (tablets, less than 992px)
@media (max-width: 991.98px) { ... }

// `xl` applies to large devices (desktops, less than 1200px)
@media (max-width: 1199.98px) { ... }

// `xxl` applies to x-large devices (large desktops, less than 1400px)
@media (max-width: 1399.98px) { ... }
  
```

> **为什么要减去 .02px？** 浏览器目前不支持 范围上下文查询，因此我们要通过使用具有更高精度的值解决 min- 和 max- 前缀 和具有小数宽度的视口（例如，在高 dpi 设备上的某些条件下可能会出现）的局限隆。

### 单断点

媒体查询使用最小和最大断点宽度来定位单个屏幕尺寸范围。

```scss
@include media-breakpoint-only(xs) { ... }
@include media-breakpoint-only(sm) { ... }
@include media-breakpoint-only(md) { ... }
@include media-breakpoint-only(lg) { ... }
@include media-breakpoint-only(xl) { ... }
@include media-breakpoint-only(xxl) { ... }
```

例如`@include media-breakpoint-only(md) { ... }`将得到如下结果：

`@media (min-width: 768px) and (max-width: 991.98px) { ... }`


### 范围断点

同样，媒体查询可能跨越多个宽度断点：

`@include media-breakpoint-between(md, xl) { ... }`

其结果为：

```scss
// Example
// 从中型设备到超大型设备应用样式
@media (min-width: 768px) and (max-width: 1199.98px) { ... }
```