# 浏览器和移动设备的支持情况

了解 Bootstrap 所支持的新和旧的浏览器和设备，以及每种浏览器和设备的已知问题和 bug。

## 支持的浏览器

Bootstrap 支持所有主流浏览器和平台的 最新、稳定版本。

对于其它使用了最新版本的 WebKit、Blink 或 Gecko 内核的浏览器，或者直接或间接调用了平台的 web view API，都不是明确被支持的。但是，Bootstrap 应该（大多数情况下）在这些浏览器中是能够正常显示和运行的。下面列出了更具体地支持情况。

你可以在 [.browserslistrc 文件](https://github.com/twbs/bootstrap/blob/v5.3.0-alpha1/.browserslistrc) 中找到 Bootstrap 所支持地浏览器及版本列表：

```
# https://github.com/browserslist/browserslist#readme

>= 0.5%
last 2 major versions
not dead
Chrome >= 60
Firefox >= 60
Firefox ESR
iOS >= 12
Safari >= 12
not Explorer <= 11
```

我们使用 [Autoprefixer](https://github.com/postcss/autoprefixer) 来自动添加特定于浏览器厂商地 CSS 属性前缀，并使用 [Browserslist](https://github.com/browserslist/browserslist) 来对浏览器地版本进行管理。请查阅这些工具各自地文档，以了解如何将这些工具集成到你的项目中。

### 移动设备

一般来说，Bootstrap 支持每个主要平台上的默认浏览器的最新版本。请主要，基于代理（proxy）模式的浏览器（例如 Opera Mini、Opera Mobile’s Turbo mode、UC Browser Mini、Amazon Silk，这些浏览器自身并不具备完整的页面渲染能力）是不被支持的。

|  | Chrome | Firefox | Safari | Android Browser & WebView |
| --- | --- | --- | --- | --- |
| **Android** | Supported | Supported | — | v6.0+ |
| **iOS** | Supported | Supported | Supported | — |


### 桌面浏览器

同样，大多数桌面浏览器的最新版本是被支持的。

|  | Chrome | Firefox | Microsoft Edge | Opera | Safari |
| --- | --- | --- | --- | --- | --- |
| **Mac** | Supported | Supported | Supported | Supported | Supported |
| **Windows** | Supported | Supported | Supported | Supported | — |

对于 Firefox 浏览器，除了最新的常规稳定版本外，我们还支持最新的 [Extended Support Release (ESR)](https://www.mozilla.org/en-US/firefox/enterprise/) 版本。

虽然 Bootstrap 在 Chromium、Linux 版 Chrome、Linux 版 Firefox 上也表现地很不错，但这些浏览器或版本是不被 Bootstrap 官方支持的。

## IE 浏览器

Bootstrap v5 版本不支持 IE 浏览器！ 如果你需要支持 IE，请使用 Bootstrap v4 版本。

## 手机上的模态框和下拉菜单

### 溢出和滚动


### iOS文本框和滚动

### 导航条下拉


## 浏览器缩放


## 验证器