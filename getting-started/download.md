
# 下载 Bootstrap

下载 Bootstrap 以获得编译后的 CSS 和 JavaScript 文件、源码，或者通过你所喜欢的软件包管理器，例如 npm、RubyGems 等，将 Bootstrap 添加到你的项目中。

## 经过编译的 CSS 和 JS

下载 Bootstrap v5.3.0-alpha1 版本经过编译并立即可用的文件，以便直接用于你的项目。下载的文件包括：

- 编译并压缩过的 CSS 集成包（[参见 CSS 文件比较](https://getbootstrap.com/docs/5.3/getting-started/contents/#css-files)）
- 编译并压缩过的 JavaScript 插件（[参见 JS 文件比较](https://getbootstrap.com/docs/5.3/getting-started/contents/#js-files)）
- 
不包括文档、源文件或任何可选的 JavaScript 依赖项（例如 Popper）。

[下载](https://github.com/twbs/bootstrap/releases/download/v5.3.0-alpha3/bootstrap-5.3.0-alpha3-dist.zip
)

## 源文件


下载 Bootstrap 的 Sass、JavaScript 和文档源码，并使用你自己的电脑进行编译。此方式需要一些额外的工具：

- [Sass 编译器](https://getbootstrap.com/docs/5.3/getting-started/contribute/#sass) 用于将 Sass 源文件编译为 CSS 文件
- [Autoprefixer](https://github.com/postcss/autoprefixer) 用于为某些 CSS 属性添加特定于厂商的属性前缀
- 
Bootstrap 自带的全套 [构建工具](https://getbootstrap.com/docs/5.3/getting-started/contribute/#tooling-setup) 已包含在源码中，它们被用来开发 Bootstrap 及其文档，但很可能不适合用到你自己的项目中。

[下载源码](https://github.com/twbs/bootstrap/archive/v5.3.0-alpha3.zip)

## 示例

如果你想下载并查看我们提供的 [示例](https://getbootstrap.com/docs/5.3/examples/) 文件，你可以通过以下链接获取经过构建的示例文件。

[下载示例](https://github.com/twbs/bootstrap/releases/download/v5.3.0-alpha1/bootstrap-5.3.0-alpha1-examples.zip)


## 使用 jsDelivr 免费 CDN

使用 jsDelivr 的话可以跳过下载文件的操作，直接在你的项目中使用 Bootstrap 编译过的 CSS 和 JS 文件。

```
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js" integrity="sha384-/mhDoLbDldZc3qpsJHpLogda//BVZbgYuw6kof4u2FrCedxOtgRZDTHgHUhOCVim" crossorigin="anonymous"></script>
```

如果你使用的是经过编译的 JavaScript 文件，并且希望单独引入 Popper，那么最好是在 Popper 之后引入 Bootstrap 的 JS 文件。

```
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js" integrity="sha384-oBqDVmMz9ATKxIep9tiCxS/Z9fNfEXiDAYTujMAeBAsjFuCZSmKbSSUnQlmh/jp3" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.min.js" integrity="sha384-ep+dxp/oz2RKF89ALMPGc7Z89QFa32C8Uv1A3TcEK8sMzXVysblLA3+eJWTzPJzT" crossorigin="anonymous"></script>
```

## 软件包管理器

通过一些常用的软件包管理器可以将 Bootstrap 的 源文件 添加到任何项目中。无论使用的是哪个软件包管理器，Bootstrap 都 依赖 [Sass 编译器](https://getbootstrap.com/docs/5.3/getting-started/contribute/#sass) 和 [Autoprefixer](https://github.com/postcss/autoprefixer) 以保证编译出的文件与官方的一致。

## npm

在你的 Node.js 项目中安装 Bootstrap 的 npm 软件包：

`npm install bootstrap@5.3.0-alpha1`

`const bootstrap = require('bootstrap')` 或 `import bootstrap from 'bootstrap'` 会将所有 Bootstrap 的插件加载到一个 bootstrap 对象上。 bootstrap 模块本身导出（export）所有插件。Bootstrap 的所有 jQuery 插件都放在软件包顶级目录下的 `/js/dist/*.js` 中，每个插件都可以独立加载。

Bootstrap 的 `package.json` 文件中包含以下一些元数据信息：

- sass - path to Bootstrap’s main Sass source file
- style - path to Bootstrap’s non-minified CSS that’s been compiled using the default settings (no customization)

> Bootstrap吧!前往[Sass & JS示例](https://github.com/twbs/examples/tree/main/sass-js)模板库，看看如何在你自己的npm项目中构建和自定义Bootstrap。包括Sass编译器、自动修复器、样式标记、PurgeCSS和引导图标。

### yarn

在你的 Node.js 项目中安装 Bootstrap 的 [yarn 软件包](https://yarnpkg.com/en/package/bootstrap)：

`yarn add bootstrap@5.3.0-alpha1`

### RubyGems

在 Gemfile 中添加如下代码行，然后利用 [Bundler](https://bundler.io/) (recommended) 和 [RubyGems](https://rubygems.org/) 在你的 Ruby 项目中安装 Bootstrap：

`gem 'bootstrap', '~> 5.3.0.alpha3'`

或者，如果你没有使用Bundler，你可以运行下面的命令来安装gem:

`gem install bootstrap -v 5.3.0.alpha3`

有关详细信息，[请参见 Bootstrap 的 gem 软件包的 README 文件](https://github.com/twbs/bootstrap-rubygem/blob/master/README.md)。

### Composer

你还可以利用 Composer 来安装并管理 Bootstrap 的 Sass 和 JavaScript 文件：

`composer require twbs/bootstrap:5.3.0-alpha1`


### NuGet

如果你是 .NET 开发者，你还可以利用 NuGet 来安装并管理 Bootstrap 的 [CSS](https://www.nuget.org/packages/bootstrap/) 或 [Sass](https://www.nuget.org/packages/bootstrap.sass/) 以及 JavaScript 文件。如果是新项目，建议使用 [libman](https://docs.microsoft.com/en-us/aspnet/core/client-side/libman/) 或其它方式，因为 NuGet 并不是为管理前端资源而设计的。

`Install-Package bootstrap`

`Install-Package bootstrap.sass`