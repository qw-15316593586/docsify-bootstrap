# 网格系统

使用我们强大的移动优先 flexbox 网格来构建各种形状和大小的布局，这要归功于 12 列系统、6 个默认响应层、Sass 变量和 mixin 以及数十个预定义类。

## 示例

Bootstrap 的网格系统使用一系列容器、行和列来布局和对齐内容。 它是用 [flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox) 构建的，并且完全支持响应式。 以下是网格系统如何工作的示例和深入解释。

> 新手或不熟悉 flexbox？ [阅读 CSS 技巧 —— flexbox 指南](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#flexbox-background)，了解 flexbox 的背景、术语、指南和代码片段。


<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row">
    <div class="col">
      Column
    </div>
    <div class="col">
      Column
    </div>
    <div class="col">
      Column
    </div>
  </div>
</div>
</div>

```html
<div class="container">
  <div class="row">
    <div class="col">
      Column
    </div>
    <div class="col">
      Column
    </div>
    <div class="col">
      Column
    </div>
  </div>
</div>
```

上面的示例使用我们预定义的网格类在所有设备和视口中创建了三个等宽的列。 这些列设置为父元素的父 `.container` 类，以在的页面中居中显示。

## 工作原理

分开来说，网格系统实现了如下的特性：

- **我们的网格支持[六个响应式断点](https://getbootstrap.com/docs/5.1/layout/breakpoints/)**。断点基于`min-width`媒体查询 ，这意味着它们会影响该断点及其上方的所有断点（例如，`.col-sm-4` 适用于 `sm`、`md`、 `lg`、`xl` 和 `xxl`）。 也就是说，您可以通过每个断点控制容器和列的大小和行为。

- **容器居中并水平填充您的内容。** 使用 `.container` 获得响应式像素宽度，`.container-fluid` 获得跨所有视口和设备 `width: 100%` ，或用于流体和像素宽度组合的响应容器（例如，`.container-md`）。

- **行是列的包装。**每一列都有水平的`padding`（称为gutter）来控制它们之间的空间。 然后在具有负边距的行上抵消此 `padding` 以确保列中的内容在视觉上对齐到左侧。 行还支持修饰符类以[统一应用列大小](https://getbootstrap.com/docs/5.1/layout/grid/#row-columns)和[gutter类](https://getbootstrap.com/docs/5.1/layout/gutters/)来改变 内容的间距。

- **列非常灵活。**每行有 12 个模板列，允许您创建跨越任意数量列的不同元素组合。 列类指示要跨越的模板列的数量（例如，`col-4` 跨越四个）。 `width` 以百分比设置，因此它始终拥有相同的相对大小。

- **沟槽(Gutters)也是响应式的和可定制性的。** [Gutter 类](https://getbootstrap.com/docs/5.1/layout/gutters/)在所有断点中都可用，大小与我们的 [边距和内边距](https://getbootstrap.com/docs/5.1/utilities/spacing/)相同。 使用 `.gx-*` 类更改水平Gutter，使用 `.gy-*` 更改垂直Gutter，或使用 `.g-*` 类更改所有Gutter。 .`g-0` 也可用于删除 Gutter。

- **Sass 变量、映射和混合(mixins)为网格提供支持。**如果您不想在 Bootstrap 中使用预定义的网格类，您可以使用我们的[网格 Sass 源码](https://getbootstrap.com/docs/5.1/layout/grid/#sass) 创建自己的更有语义的标记。 我们还引入了一些 CSS 自定义属性来使用这些 Sass 变量，从而为您提供更大的灵活性。

请注意 flexbox 的限制和 [bug](https://github.com/philipwalton/flexbugs)，例如 [无法将某些 HTML 元素用作弹性(flex)容器](https://github.com/philipwalton/flexbugs#flexbug-9)。


## 选项

Bootstrap 的网格系统可以适应所有六个默认断点，以及您自定义的任何断点。 六个默认网格层级如下：

- 非常小 (xs)
- 小 (sm)
- 中 (md)
- 大 (lg)
- 非常大 (xl)
- 非常非常大 (xxl)

如上所述，每个断点都有自己的容器、唯一的类前缀和修饰符。 以下是网格在这些断点之间的变化方式：

|  | xs <br> <576px | sm <br> ≥576px | md <br> ≥768px | lg <br> ≥992px | xl <br> ≥1200px | xxl <br> ≥1400px |
| --- | --- | --- | --- | --- | --- | --- |
| Container `max-width` | None (auto) | 540px | 720px | 960px | 1140px | 1320px |
| Class prefix | `.col-` | `.col-sm-` | `.col-md-` | `.col-lg-` | `.col-xl-` | `.col-xxl-` |
| \# of columns | 12 |
| Gutter width | 1.5rem (.75rem on left and right) |
| Custom gutters | [Yes](/docs/5.1/layout/gutters/) |
| Nestable | [Yes](#nesting) |
| Column ordering | [Yes](/docs/5.1/layout/columns/#reordering) |

## 自动布局列

利用指定断点的列类来轻松调整列大小，而无需像 `.col-sm-6` 这样的明确编号的类。

### 等宽

例如，这里有两个网格布局适用于每个设备和视口，从 xs 到 xxl。 为您需要的每个断点添加任意数量的无单位类，并且每列的宽度都相同。

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row">
    <div class="col">
      1 of 2
    </div>
    <div class="col">
      2 of 2
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col">
      2 of 3
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
</div>
</div>


```html
<div class="container">
  <div class="row">
    <div class="col">
      1 of 2
    </div>
    <div class="col">
      2 of 2
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col">
      2 of 3
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
</div>
```


### 设置其中一列的宽度

flexbox 网格列的自动布局还意味着您可以设置一列的宽度并让同级列自动调整其大小。 您可以使用预定义的网格类（如下所示）、网格混合或内联宽度。 请注意，无论中心列的宽度如何，其他列都会调整大小。


<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-6">
      2 of 3 (wider)
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-5">
      2 of 3 (wider)
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
</div>
</div>


```
<div class="container">
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-6">
      2 of 3 (wider)
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-5">
      2 of 3 (wider)
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
</div>
```

### 可变宽度内容

使用 `col-{breakpoint}-auto `类根据其内容的自然宽度调整列的大小。

<div class="bd-example bd-example-row">
<div class="container">
  <div class="row justify-content-md-center">
    <div class="col col-lg-2">
      1 of 3
    </div>
    <div class="col-md-auto">
      Variable width content
    </div>
    <div class="col col-lg-2">
      3 of 3
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-md-auto">
      Variable width content
    </div>
    <div class="col col-lg-2">
      3 of 3
    </div>
  </div>
</div>
</div>


```
<div class="container">
  <div class="row justify-content-md-center">
    <div class="col col-lg-2">
      1 of 3
    </div>
    <div class="col-md-auto">
      Variable width content
    </div>
    <div class="col col-lg-2">
      3 of 3
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-md-auto">
      Variable width content
    </div>
    <div class="col col-lg-2">
      3 of 3
    </div>
  </div>
</div>
```


## 响应式类

Bootstrap 的网格包括六个层次的预定义类，用于构建复杂的响应式布局。 在您认为合适的超小型、小型、中型、大型或超大型设备上自定义列的大小。

### 所有断点

从最小设备到最大设备都相同的网格，请使用 `.col` 和 `.col-*` 类。 当你需要一个特定大小的列时，指定一个类编号； 否则，请使用 `.col`。


<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row">
    <div class="col">col</div>
    <div class="col">col</div>
    <div class="col">col</div>
    <div class="col">col</div>
  </div>
  <div class="row">
    <div class="col-8">col-8</div>
    <div class="col-4">col-4</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row">
    <div class="col">col</div>
    <div class="col">col</div>
    <div class="col">col</div>
    <div class="col">col</div>
  </div>
  <div class="row">
    <div class="col-8">col-8</div>
    <div class="col-4">col-4</div>
  </div>
</div>
```

### 水平堆砌

使用 `.col-sm-*` 这组类(也可以是其它同一组的类)，您可以创建一个基本的网格系统，该系统在小断点 (`sm`) 处开始堆叠并变为水平。

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row">
    <div class="col-sm-8">col-sm-8</div>
    <div class="col-sm-4">col-sm-4</div>
  </div>
  <div class="row">
    <div class="col-sm">col-sm</div>
    <div class="col-sm">col-sm</div>
    <div class="col-sm">col-sm</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row">
    <div class="col-sm-8">col-sm-8</div>
    <div class="col-sm-4">col-sm-4</div>
  </div>
  <div class="row">
    <div class="col-sm">col-sm</div>
    <div class="col-sm">col-sm</div>
    <div class="col-sm">col-sm</div>
  </div>
</div>
```

### 混合使用

不希望在某些网格层次中简单地堆叠您的列？ 根据需要为每一层次使用不同类的组合。 请参阅下面的示例，以更好地了解它是如何工作的。

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <!-- Stack the columns on mobile by making one full-width and the other half-width -->
  <div class="row">
    <div class="col-md-8">.col-md-8</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>

  <!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
  <div class="row">
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>

  <!-- Columns are always 50% wide, on mobile and desktop -->
  <div class="row">
    <div class="col-6">.col-6</div>
    <div class="col-6">.col-6</div>
  </div>
</div>
</div>

```
<div class="container">
  <!-- Stack the columns on mobile by making one full-width and the other half-width -->
  <div class="row">
    <div class="col-md-8">.col-md-8</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>

  <!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
  <div class="row">
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
    <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  </div>

  <!-- Columns are always 50% wide, on mobile and desktop -->
  <div class="row">
    <div class="col-6">.col-6</div>
    <div class="col-6">.col-6</div>
  </div>
</div>
```

### 行列类

行列类就是使用响应式 `.row-cols-*` 类快速设置能最好呈现您的内容和布局的列数。 普通的 `.col-*` 类设置在列上（例如，`.col-md-4`），而行列类是设置在父`.row`上。 作为快捷方式， 使用 `.row-cols-auto` 您可以为列指定其自然宽度。

使用这些行列类快速创建基本的网格布局或控制您的卡片布局。

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row row-cols-2">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row row-cols-2">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
```

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row row-cols-3">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row row-cols-3">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
```

<div class="bd-example bd-example-row">
<div class="container">
  <div class="row row-cols-auto">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row row-cols-auto">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
```

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row row-cols-4">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row row-cols-4">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
```

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row row-cols-4">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col-6">Column</div>
    <div class="col">Column</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row row-cols-4">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col-6">Column</div>
    <div class="col">Column</div>
  </div>
</div>
```

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row row-cols-1 row-cols-sm-2 row-cols-md-4">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
</div>

```
<div class="container">
  <div class="row row-cols-1 row-cols-sm-2 row-cols-md-4">
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
    <div class="col">Column</div>
  </div>
</div>
```

你也可以使用 Sass mixin，`row-cols()`：

```
.element {
  // 从三列开始
  @include row-cols(3);

  // 从中等断点开始的五列
  @include media-breakpoint-up(md) {
    @include row-cols(5);
  }
}
```

## 嵌套

要在默认网格中嵌套您的内容，请在现有 `.col-sm-*` 中添加新的 `.row` 和一组 `.col-sm-*` 列。 嵌套行应包括一组不超过 12 列的列（不需要使用所有 12 个可用列）。

<div class="bd-example bd-example-row" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="container">
  <div class="row">
    <div class="col-sm-3">
      Level 1: .col-sm-3
    </div>
    <div class="col-sm-9">
      <div class="row">
        <div class="col-8 col-sm-6">
          Level 2: .col-8 .col-sm-6
        </div>
        <div class="col-4 col-sm-6">
          Level 2: .col-4 .col-sm-6
        </div>
      </div>
    </div>
  </div>
</div>
</div>

```html
<div class="container">
  <div class="row">
    <div class="col-sm-3">
      Level 1: .col-sm-3
    </div>
    <div class="col-sm-9">
      <div class="row">
        <div class="col-8 col-sm-6">
          Level 2: .col-8 .col-sm-6
        </div>
        <div class="col-4 col-sm-6">
          Level 2: .col-4 .col-sm-6
        </div>
      </div>
    </div>
  </div>
</div>
```

## Sass

使用 Bootstrap 的 Sass 源码时，您可以选择使用 Sass 变量和 mixin 来创建自定义、语义化和响应式的页面布局。 我们预定义的网格类使用这些相同的变量和 mixin 来提供一整套现成的类，以实现快速的响应式布局。


### 变量

变量和映射确定列数、沟槽(gutter)宽度和开始浮动列的媒体查询点。 我们使用这些来生成上面记录的预定义网格类，以及下面列出的自定义 mixins。

```scss
$grid-columns:      12;
$grid-gutter-width: 1.5rem;
```

```scss
$grid-breakpoints: (
  xs: 0,
  sm: 576px,
  md: 768px,
  lg: 992px,
  xl: 1200px,
  xxl: 1400px
);
```

```scss
$container-max-widths: (
  sm: 540px,
  md: 720px,
  lg: 960px,
  xl: 1140px,
  xxl: 1320px
);
```

### Mixins

Mixin 与网格变量结合使用，为各个网格列生成语义化的 CSS。

```scss
//Creates a wrapper for a series of columns
@include make-row();

// Make the element grid-ready (applying everything but the width)
@include make-col-ready();

// Without optional size values, the mixin will create equal columns (similar to using .col)
@include make-col();
@include make-col($size, $columns: $grid-columns);

// Offset with margins
@include make-col-offset($size, $columns: $grid-columns);

```

### 示例用法

您可以将变量修改为您自己的自定义值，或者仅使用带有默认值的 mixin。 这是使用默认设置创建两列布局的示例，其间有间隙。

```scss
.example-container {
  @include make-container();
  // Make sure to define this width after the mixin to override
  // `width: 100%` generated by `make-container()`
  width: 800px;
}

.example-row {
  @include make-row();
}

.example-content-main {
  @include make-col-ready();

  @include media-breakpoint-up(sm) {
    @include make-col(6);
  }
  @include media-breakpoint-up(lg) {
    @include make-col(8);
  }
}

.example-content-secondary {
  @include make-col-ready();

  @include media-breakpoint-up(sm) {
    @include make-col(6);
  }
  @include media-breakpoint-up(lg) {
    @include make-col(4);
  }
}
```

<div class="bd-example" style="border-color: rgba(0, 0, 0, 0.35);">
<div class="example-container">
  <div class="example-row">
    <div class="example-content-main">Main content</div>
    <div class="example-content-secondary">Secondary content</div>
  </div>
</div>
</div>

```html
<div class="example-container">
  <div class="example-row">
    <div class="example-content-main">Main content</div>
    <div class="example-content-secondary">Secondary content</div>
  </div>
</div>
```

## 自定义网格

使用我们内置的网格 Sass 变量和映射，可以完全自定义预定义的网格类。 更改层数、媒体查询维度和容器宽度，然后重新编译。

### 列和沟槽

网格列的数量可以通过 Sass 变量进行修改。 $grid-columns 用于生成每个单独列的宽度（百分比），而 $grid-gutter-width 设置列间距的宽度。

```scss
$grid-columns: 12 !default;
$grid-gutter-width: 1.5rem !default;
```

### 网格层

除了列本身之外，您还可以自定义网格层的数量。 如果您只需要四个网格层，您可以将 `$grid-breakpoints` 和 `$container-max-widths` 更新为如下内容：

```scss
$grid-breakpoints: (
  xs: 0,
  sm: 480px,
  md: 768px,
  lg: 1024px
);

$container-max-widths: (
  sm: 420px,
  md: 720px,
  lg: 960px
);
```

在对 Sass 变量或映射进行任何更改时，您需要保存更改并重新编译。 这样做将输出一组全新的预定义网格类，用于列宽、偏移和排序。 响应式可见性实用程序也将更新为使用自定义断点。 确保使用 `px` 设置网格值（不是 `rem`、`em` 或 `%`）。