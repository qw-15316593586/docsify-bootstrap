# Sass

定制Sass 源代码利用变量、映射(map)、混合(mixin) 和函数(function)来帮助您更快地构建和自定义您的项目。

## 文件结构

尽可能避免修改 Bootstrap 的核心文件。 对于 Sass ，有一个修改的变通方法：创建您自己的样式表， Bootstrap 导入，这样您就可以修改和扩展它了。 假设您使用的是像 npm 这样的包管理器，您将拥有一个如下所示的文件结构：

```
your-project/
├── scss
│   └── custom.scss
└── node_modules/
    └── bootstrap
        ├── js
        └── scss
```

如果您没有使用包管理器，并且已经下载了我们的源码文件，您将需要手动设置类似于该结构的东西，将 Bootstrap 的源文件与您自己的源文件分开。

```
your-project/
├── scss
│   └── custom.scss
└── bootstrap/
    ├── js
    └── scss
```

## 导入 

在您的 custom.scss 文件中，您需要导入 Bootstrap 的 Sass 源码文件。 你有两个选择：包括所有的 Bootstrap，或者选择你需要的部分。 我们鼓励后者，但请注意我们的组件之间存在一些要求和依赖关系。 您还需要为我们的插件添加一些 JavaScript。

```
// Custom.scss
// 选项A:包括所有的Bootstrap

// 这里包含重写的默认变量(尽管函数不可用)

@import "../../../node_modules/bootstrap/scss/bootstrap";

// 然后在这里添加额外的自定义代码
```


```
// Custom.scss
// 选项B:包括Bootstrap的部分内容

// 1. 首先包含函数(这样你就可以操作颜色，svg, calc等)
@import "../../../node_modules/bootstrap/scss/functions";

// 2. 这里包含重写的默认变量

// 3.包括所需的Bootstrap样式表的其余部分
@import "../../../node_modules/bootstrap/scss/variables";
@import "../../../node_modules/bootstrap/scss/mixins";
@import "../../../node_modules/bootstrap/scss/root";

// 4. 根据需要包括任何可选的Bootstrap CSS
@import "../../../node_modules/bootstrap/scss/utilities";
@import "../../../node_modules/bootstrap/scss/reboot";
@import "../../../node_modules/bootstrap/scss/type";
@import "../../../node_modules/bootstrap/scss/images";
@import "../../../node_modules/bootstrap/scss/containers";
@import "../../../node_modules/bootstrap/scss/grid";
@import "../../../node_modules/bootstrap/scss/helpers";

// 5. 可选地在' _utilities.scss '中最后包含utilities API以基于Sass映射生成类
@import "../../../node_modules/bootstrap/scss/utilities/api";

// 6. 在这里添加额外的自定义代码
```


## 变量默认值

Bootstrap 中的每个 Sass 变量的定义都包含 `!default` 标志，允许您在自己的 Sass 代码中覆盖变量的默认值，而无需修改 Bootstrap 的源代码。 根据需要复制和粘贴变量，修改它们的值，然后删除 `!default` 标志。

您将在 `scss/_variables.scss` 中找到完整的 Bootstrap 变量列表。 一些变量设置为 `null`，这些变量不会输出任何内容，除非被您自定义的代码覆盖。

> 只有在导入bootstrap文件之前声明变量时才会被重写

这是一个在通过 npm 导入和编译 Bootstrap 时更改 `<body>` 的 `background-color` 和 `color` 的示例：

```
// Required
@import "../../../node_modules/bootstrap/scss/functions";

// Default variable overrides
$body-bg: #000;
$body-color: #111;

// Required
@import "../../../node_modules/bootstrap/scss/variables";
@import "../../../node_modules/bootstrap/scss/variables-dark";
@import "../../../node_modules/bootstrap/scss/maps";
@import "../../../node_modules/bootstrap/scss/mixins";
@import "../../../node_modules/bootstrap/scss/root";

// Optional Bootstrap components here
@import "../../../node_modules/bootstrap/scss/reboot";
@import "../../../node_modules/bootstrap/scss/type";
// etc
```

**只有在导入bootstrap文件之前声明变量时才会被重写**

```
$body-bg: #eeeeee;
$body-color: #568956;
@import "../../../node_modules/bootstrap/scss/bootstrap";
```

## 映射(Maps)和循环(loops)

### 修改映射

$theme-colors映射中的所有变量都被定义为独立变量。要修改$theme-colors映射中的现有颜色，请在自定义Sass文件中添加以下内容:

```
$primary: #987;
$danger: #564;
$secondary: #6989;
$success: #758789;
$info: #698654;
$warning: #235;
$light: #987789;
$dark: #8789;
```

稍后，这些变量在 Bootstrap 的 `$theme-colors` 映射中设置：

```
$theme-colors: (
    "primary": $primary,
    "danger": $danger,
    "secondary": $secondary,
    "success": $success,
    "info": $info,
    "warning": $warning,
    "light": $light,
    "dark": $dark
);

```

### 添加到映射中

想要将新颜色添加到 `$theme-colors` 或任何其他映射中。需要使用自定义值创建新的 Sass 映射并将其与原始映射合并， 在这里，我们将创建一个新的 `$custom-colors` 映射并将其与 `$theme-colors` 合并。

```
// Create your own map
$custom-colors: (
    "custom-color": #900
);

// Merge the maps
$theme-colors: map-merge($theme-colors, $custom-colors);
```

### 从映射中删除

要从 $theme-colors 或任何其他映射中删除颜色，请使用 `map-remove`。 

```
$theme-colors: map-remove($theme-colors, "info", "light", "dark");
```

## 必须键

Bootstrap 假设 Sass 映射中存在一些特定的键，因为我们自己使用并扩展了这些键。 当您自定义包含的映射时，您可能会遇到使用特定 Sass 映射键的错误。

例如，我们使用 `$theme-colors` 中的 `primary`、`success` 和` danger` 键作为链接、按钮、表格状态。 替换这些键的值应该没有问题，但删除它们可能会导致 Sass 编译问题。 在这些情况下，您需要修改使用这些值的 Sass 代码。


## 函数(Functions)

### 颜色

除了我们拥有的 Sass 映射，主题颜色也可以用作独立变量，例如 $primary 。


您可以使用 Bootstrap 的 `tint-color()` 和 `shade-color()` 函数使颜色变亮或变暗。 这些函数会将颜色与黑色或白色混合，不像 Sass 的原生 `lighten()` 和 `darken()` 函数会以固定的量改变亮度，而这通常不会得到期望的效果。

```
// Tint a color: mix a color with white
@function tint-color($color, $weight) {
    @return mix(white, $color, $weight);
}

// Shade a color: mix a color with black
@function shade-color($color, $weight) {
    @return mix(black, $color, $weight);
}

// Shade the color if the weight is positive, else tint it
@function shift-color($color, $weight) {
    @return if($weight > 0, shade-color($color, $weight), tint-color($color, -$weight));
}

$gray-100: #ec0a7b;

.custom-element {
    color: $gray-100;
    background-color: $dark;
}

<!-- 在实践中，您会调用该函数并传入颜色和重量参数。 -->

.custom-element-1 {
    color: tint-color($primary, 20%);
}

.custom-element-2 {
    color: shade-color($danger, 50%);
}
```

### 颜色对比度 

`color: color-contrast(#000);` 有问题,属性值无效

### 转义 SVG

我们使用 `escape-svg` 函数来转义 SVG 背景图像的 `<`、`>` 和 `#` 字符。 使用 `escape-svg` 函数时，必须引用数据 URI。


### add、subtract函数

我们使用 `add` 和 `subtract` 函数来包装 CSS `calc` 函数。 这些函数的主要目的是避免在将“无单位”`0` 值传递到 `calc` 表达式时出错。 尽管在数学上是正确的，像 `calc(10px - 0)` 这样的表达式将在所有浏览器中返回错误。


```
$border-radius: 4rem;
$border-width: 2rem;

.element-radius {
    //$border-radius - $border-width 使用变量加减算法就错误
    border-radius: calc(4rem - 2rem);
}
```

## Mixins

我们的 · 目录有大量的 mixin，它们支撑着 Bootstrap 的各个部分，也可以在您自己的项目中使用。

### Color schemes

`prefers-color-scheme` 媒体查询的 mixin 可用于支持 `light`、`dark` 和自定义颜色方案。

```
@mixin color-scheme($name) {
  @media (prefers-color-scheme: #{$name}) {
    @content;
  }
}

.custom-element {
  @include color-scheme(dark) {
    // Insert dark mode styles here
  }

  @include color-scheme(custom-named-scheme) {
    // Insert custom color scheme styles here
  }
}
```

## 实例

`sass -w scss:css`监听scss目录中自定义的`custom.scss`文件，将自动生成`css/custom.css`文件，导入到项目中的html文件即可使用

```
// 似乎只有在导入bootstrap之前声明时才会被重写

$body-bg: #eeeeee;
$body-color: #568956;

$primary: #987;
$danger: #564;
$secondary: #6989;
$success: #758789;
$info: #698654;
$warning: #235;
$light: #987789;
$dark: #8789;

$theme-colors: (
    "primary": $primary,
    "danger": $danger,
    "secondary": $secondary,
    "success": $success,
    "info": $info,
    "warning": $warning,
    "light": $light,
    "dark": $dark
);

// Create your own map
$custom-colors: (
    "custom-color": #900
);

// Merge the maps
$theme-colors: map-merge($theme-colors, $custom-colors);
$theme-colors: map-remove($theme-colors, "info", "light", "dark");

$form-range-thumb-width: 2rem;
$form-range-thumb-height: 2rem;
$font-family-base: 'Manrope';

// Tint a color: mix a color with white
@function tint-color($color, $weight) {
    @return mix(white, $color, $weight);
}

// Shade a color: mix a color with black
@function shade-color($color, $weight) {
    @return mix(black, $color, $weight);
}

// Shade the color if the weight is positive, else tint it
@function shift-color($color, $weight) {
    @return if($weight > 0, shade-color($color, $weight), tint-color($color, -$weight));
}

$gray-100: #ec0a7b;

.custom-element {
    color: $gray-100;
    background-color: $dark;
}

.custom-element-1 {
    color: tint-color($primary, 20%);
}

.custom-element-2 {
    color: shade-color($danger, 50%);
}

$border-radius: 4rem;
$border-width: 2rem;

.element-radius {
    //$border-radius - $border-width 使用变量就错误
    border-radius: calc(4rem - 2rem);
}

@import "../../../node_modules/bootstrap/scss/bootstrap";
```

使用定制后的css样式文件

```
<!doctype html>
<html lang="zh-CN">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="sass/css/custom.css" rel="stylesheet">
    <title>Hello, world!</title>
</head>

<body>
    <div class="text-bg-primary p-3">Primary with contrasting color</div>
    <div class="text-bg-secondary p-3">Secondary with contrasting color</div>
    <div class="text-bg-success p-3">Success with contrasting color</div>
    <div class="text-bg-danger p-3">Danger with contrasting color</div>
    <div class="text-bg-warning p-3">Warning with contrasting color</div>
    <div class="text-bg-info p-3">Info with contrasting color</div>
    <div class="text-bg-light p-3">Light with contrasting color</div>
    <div class="text-bg-dark p-3">Dark with contrasting color</div>
    <div class="text-bg-custom-color p-3">Dark with contrasting color</div>
    <p class="custom-element">custom-element</p>
    <p class="custom-element-1">custom-element-1</p>
    <p class="custom-element-2">custom-element-2</p>
    <br>
    <img src="images/avatar.png" class="element-radius" alt="...">
    <br>
    <h1>Hello, world!</h1>
    <br> 
    <script src="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/5.2.3/js/bootstrap.bundle.min.js"></script>
</body>

</html>
```

