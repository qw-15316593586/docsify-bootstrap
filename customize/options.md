# 选项 

快速自定义Bootstrap内置变量，轻松切换全局CSS首选项来控制样式和行为。

使用我们内置的自定义变量文件自定义Bootstrap，并使用新的`$enable-*` Sass变量轻松切换全局CSS首选项。覆盖变量的值，并根据需要使用`npm run test`重新编译。

您可以在Bootstrap的`scss/_variables.css`中找到并自定义这些关键全局选项的变量。

| Variable | Values | Description |
| --- | --- | --- |
| `$spacer` | `1rem` (default), or any value > 0 | Specifies the default spacer value to programmatically generate our [spacer utilities](/docs/5.3/utilities/spacing/). |
| `$enable-dark-mode` | `true` (default) or `false` | Enables built-in [dark mode support](/docs/5.3/customize/color-modes/#dark-mode) across the project and its components. |
| `$enable-rounded` | `true` (default) or `false` | Enables predefined `border-radius` styles on various components. |
| `$enable-shadows` | `true` or `false` (default) | Enables predefined decorative `box-shadow` styles on various components. Does not affect `box-shadow`s used for focus states. |
| `$enable-gradients` | `true` or `false` (default) | Enables predefined gradients via `background-image` styles on various components. |
| `$enable-transitions` | `true` (default) or `false` | Enables predefined `transition`s on various components. |
| `$enable-reduced-motion` | `true` (default) or `false` | Enables the [`prefers-reduced-motion` media query](/docs/5.3/getting-started/accessibility/#reduced-motion), which suppresses certain animations/transitions based on the users’ browser/operating system preferences. |
| `$enable-grid-classes` | `true` (default) or `false` | Enables the generation of CSS classes for the grid system (e.g. `.row`, `.col-md-1`, etc.). |
| `$enable-container-classes` | `true` (default) or `false` | Enables the generation of CSS classes for layout containers. (New in v5.2.0) |
| `$enable-caret` | `true` (default) or `false` | Enables pseudo element caret on `.dropdown-toggle`. |
| `$enable-button-pointers` | `true` (default) or `false` | Add “hand” cursor to non-disabled button elements. |
| `$enable-rfs` | `true` (default) or `false` | Globally enables [RFS](/docs/5.3/getting-started/rfs/). |
| `$enable-validation-icons` | `true` (default) or `false` | Enables `background-image` icons within textual inputs and some custom forms for validation states. |
| `$enable-negative-margins` | `true` or `false` (default) | Enables the generation of [negative margin utilities](/docs/5.3/utilities/spacing/#negative-margin). |
| `$enable-deprecation-messages` | `true` (default) or `false` | Set to `false` to hide warnings when using any of the deprecated mixins and functions that are planned to be removed in `v6`. |
| `$enable-important-utilities` | `true` (default) or `false` | Enables the `!important` suffix in utility classes. |
| `$enable-smooth-scroll` | `true` (default) or `false` | Applies `scroll-behavior: smooth` globally, except for users asking for reduced motion through [`prefers-reduced-motion` media query](/docs/5.3/getting-started/accessibility/#reduced-motion) |