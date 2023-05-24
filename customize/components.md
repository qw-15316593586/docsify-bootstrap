# 组件

了解我们如何以及为什么构建几乎所有响应式组件，使用基类和修饰类。

## 基类

Bootstrap 的组件主要是使用基本修饰符命名法构建的。 我们将尽可能多的共享属性分组到一个基类中，例如 `.btn`，然后将每个变体的单独样式分组到修饰符类中，例如 `.btn-primary` 或 `.btn-success`。

为了构建我们的修饰符类，我们使用 Sass 的 `@each` 循环来迭代 Sass 映射。 这对于通过我们的 $theme-colors 生成组件的变体以及为每个断点创建响应式变体特别有用。 当您自定义这些 Sass 映射并重新编译时，您将自动看到您的更改反映在这些循环中。

查看[我们的 Sass 映射和循环文档](https://getbootstrap.com/docs/5.1/customize/sass/#maps-and-loops)，了解如何自定义这些循环并将 Bootstrap 的基本修饰符方法扩展到您自己的 代码。

## 修饰符

Bootstrap 的许多组件都是使用基本修饰符类方法构建的。 这意味着大部分样式都包含在基类中（例如，`.btn`），而样式变化仅限于修饰符类（例如，`.btn-danger`）。 这些修饰符类是从 `$theme-colors` 映射构建的，以自定义修饰符类的数量和名称。

以下是我们如何循环 `$theme-colors` 映射以生成对 `.alert` 和 `.list-group` 组件的修饰符的两个示例。

```
// 生成上下文修饰符类，用于为alert着色。

@each $state, $value in $theme-colors {
  $alert-background: shift-color($value, $alert-bg-scale);
  $alert-border: shift-color($value, $alert-border-scale);
  $alert-color: shift-color($value, $alert-color-scale);
  @if (contrast-ratio($alert-background, $alert-color) < $min-contrast-ratio) {
    $alert-color: mix($value, color-contrast($alert-background), abs($alert-color-scale));
  }
  .alert-#{$state} {
    @include alert-variant($alert-background, $alert-border, $alert-color);
  }
}
```

```
// 列出组上下文变体
// 添加修饰符类以更改单个项目的文本和背景颜色。从组织结构上讲，这必须在“:hover”状态之后。

@each $state, $value in $theme-colors {
  $list-group-variant-bg: shift-color($value, $list-group-item-bg-scale);
  $list-group-variant-color: shift-color($value, $list-group-item-color-scale);
  @if (contrast-ratio($list-group-variant-bg, $list-group-variant-color) < $min-contrast-ratio) {
    $list-group-variant-color: mix($value, color-contrast($list-group-variant-bg), abs($list-group-item-color-scale));
  }

  @include list-group-item-variant($state, $list-group-variant-bg, $list-group-variant-color);
}
```

## 响应式

这些 Sass 循环也不限于颜色映射。 您还可以生成组件的响应式变体。 以我们的响应式下拉列表的对齐为例，我们将 Sass 映射 `$grid-breakpoints` 使用 `@each` 循环与媒体查询混合。


```
// 我们故意硬编码' bs- '前缀，因为我们在JS中检查这个自定义属性来确定Popper的定位

@each $breakpoint in map-keys($grid-breakpoints) {
  @include media-breakpoint-up($breakpoint) {
    $infix: breakpoint-infix($breakpoint, $grid-breakpoints);

    .dropdown-menu#{$infix}-start {
      --bs-position: start;

      &[data-bs-popper] {
        right: auto;
        left: 0;
      }
    }

    .dropdown-menu#{$infix}-end {
      --bs-position: end;

      &[data-bs-popper] {
        right: 0;
        left: auto;
      }
    }
  }
}
```

如果您修改 `$grid-breakpoints`，您的更改将应用于遍历该映射的所有循环。

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

如果您修改 `$grid-breakpoints`，您的更改将应用于遍历该映射的所有循环。

## 创建你自己的

我们鼓励您在使用 Bootstrap 构建以创建自己的组件时采用这些准则。 我们已经将这种方法扩展到我们的文档和示例中的自定义组件。 像我们的标注的组件就像我们提供的带有基类和修饰符类的组件一样构建。

> 这是一个标注。我们为我们的文档定制了它，这样我们给你的信息就会脱颖而出。它通过修饰符类有三种变体。

`<div class="callout">...</div>`

在您的 CSS 中，您将拥有类似以下的内容，其中大部分样式是通过 `.callout` 完成的。 然后，通过修饰符类控制每个变体之间的独特样式。

```
// Base class
.callout {
    padding: 1.25rem;
    margin-top: 1.25rem;
    margin-bottom: 1.25rem;
    border: 1px solid #e9ecef;
    border-left-width: .25rem;
    border-radius: .25rem;
}

// Modifier classes
.callout-info {
    border-left-color: #5bc0de;
}
.callout-warning {
    border-left-color: #f0ad4e;
}
.callout-danger {
    border-left-color: #d9534f;
}
```

对于标注，独特的样式只是 `border-left-color`。 当您将该基类与其中一个修饰符类结合使用时，您将获得完整的组件系列：