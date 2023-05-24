# 颜色

Bootstrap由一个广泛的颜色系统支持，该系统可以为我们的样式和组件设置主题。这可以为任何项目提供更全面的定制和扩展。

### 主题颜色


我们使用所有颜色的子集来创建一个较小的调色板来生成配色方案，也可以作为Sass变量和Bootstrap的`scss/_variables.css`文件中的Sass映射。

```html
<div class="row">

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-primary text-white">Primary</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-secondary text-white">Secondary</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-success text-white">Success</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-danger text-white">Danger</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-warning text-dark">Warning</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-info text-dark">Info</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-light text-dark">Light</div>
    </div>

    <div class="col-md-4">
      <div class="p-3 mb-3 bg-dark text-white">Dark</div>
    </div>

</div>
```

所有这些颜色都可以作为Sass映射的$theme-colors使用。

```
$theme-colors: (
  "primary":    $primary,
  "secondary":  $secondary,
  "success":    $success,
  "info":       $info,
  "warning":    $warning,
  "danger":     $danger,
  "light":      $light,
  "dark":       $dark
);
```

查看我们的[Sass映射和循环文档](https://getbootstrap.com/docs/5.1/customize/sass/#maps-and-loops)，了解如何修改这些颜色。


### 所有的颜色


所有的Bootstrap颜色都可以作为Sass变量和Sass映射在`scss/_variables.scss`文件。为了避免增加文件大小，我们没有为每个变量创建文本或背景颜色类。相反，我们选择这些颜色的一个子集作为[主题调色板](https://getbootstrap.com/docs/5.1/customize/color/#theme-colors)。

在自定义颜色时，一定要监控对比度。如下图所示，我们为每种主要颜色添加了三种对比度——一种是样品当前的颜色，一种是与白色的对比，一种是与黑色的对比。

### Sass调色

Sass不能以编程方式生成变量，所以我们自己手动为每种色调和阴影创建变量。我们指定中点值(例如，`$blue-500`)，并使用自定义颜色函数通过Sass的`mix()`颜色函数使颜色变浅(变亮)或变暗(变暗)。

使用`mix()`与使用`lighter()`和`darken()`不同，前者将指定的颜色与白色或黑色混合，而后者仅调整每种颜色的明度值。结果是一个更完整的颜色套件，如这个[CodePen演示所示](https://codepen.io/emdeoh/pen/zYOQOPB)。

我们的`tint-color()`和`shade-color()`函数将`mix()`与`$theme-color-interval`变量一起使用，该变量为我们生成的每种混合颜色指定一个步进百分比值。请参阅`scss/_functions.scss`和`scss/_variables.scss`件的完整源代码。

## Sass颜色映射

Bootstrap 的 Sass 源码文件包括三个映射，可帮助您快速轻松地遍历颜色列表及其十六进制值。

- `$colors` 列出我们所有可用的基本 (`500`) 颜色
- `$theme-colors` 列出所有按语义命名的主题颜色（如下所示）
- `$grays` 列出所有灰色的色调和阴影
在 `scss/_variables.scss` 中，您会找到 Bootstrap 的颜色变量和 Sass 映射。 这是 `$colors` Sass 映射的示例：

```
$colors: (
  "blue":       $blue,
  "indigo":     $indigo,
  "purple":     $purple,
  "pink":       $pink,
  "red":        $red,
  "orange":     $orange,
  "yellow":     $yellow,
  "green":      $green,
  "teal":       $teal,
  "cyan":       $cyan,
  "white":      $white,
  "gray":       $gray-600,
  "gray-dark":  $gray-800
);
```

在 映射中添加、删除或修改值以更新使用它们的许多其他组件。 不幸的是，目前并不是每个组件都使用这个 Sass 映射。 未来的更新将努力改进这一点。 在那之前，计划使用 `${color}` 变量和这个 Sass 映射。

### 例子

以下是在 Sass 中使用它们的方法：

```
.alpha { color: $purple; }
.beta {
  color: $yellow-300;
  background-color: $indigo-900;
}
```

[Color](https://getbootstrap.com/docs/5.1/utilities/colors/) 和 [background](https://getbootstrap.com/docs/5.1/utilities/background/) 实用程序类也可用于设置 color 和 background-color 使用 500 颜色值。

## 生成工具

Bootstrap 不包含每个颜色变量的 `color` 和 `background-color` 实用程序，但您可以使用我们的 [实用程序 API](https://getbootstrap.com/docs/5.1/utilities/api/) 和我们在 v5.1.0 中添加的扩展 Sass 映射。

1. 首先，请确保您已经导入了我们的函数、变量、mixin 和实用程序。
2. 使用我们的 `map-merge-multiple()` 函数将多个 Sass 映射快速合并到一个新映射中。
3. 合并这个新的组合映射以扩展任何具有 `{color}-{level}` 类名的实用程序。

这是一个使用上述步骤生成文本颜色实用程序（例如，`.text-purple-500`）的示例。

```
@import "bootstrap/scss/functions";
@import "bootstrap/scss/variables";
@import "bootstrap/scss/mixins";
@import "bootstrap/scss/utilities";

$all-colors: map-merge-multiple($blues, $indigos, $purples, $pinks, $reds, $oranges, $yellows, $greens, $teals, $cyans);

$utilities: map-merge(
  $utilities,
  (
    "color": map-merge(
      map-get($utilities, "color"),
      (
        values: map-merge(
          map-get(map-get($utilities, "color"), "values"),
          (
            $all-colors
          ),
        ),
      ),
    ),
  )
);

@import "bootstrap/scss/utilities/api";
```

这将为每种颜色和级别生成新的 `.text-{color}-{level}` 实用程序。 您也可以对任何其他实用程序和资源执行相同的操作。
