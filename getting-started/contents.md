# 内容 

了解Bootstrap中包含的内容，包括我们的编译和源代码风格。

## 编译后的Bootstrap 

下载后，解压缩文件夹，你会看到这样的内容:

```
bootstrap/
├── css/
│   ├── bootstrap-grid.css
│   ├── bootstrap-grid.css.map
│   ├── bootstrap-grid.min.css
│   ├── bootstrap-grid.min.css.map
│   ├── bootstrap-grid.rtl.css
│   ├── bootstrap-grid.rtl.css.map
│   ├── bootstrap-grid.rtl.min.css
│   ├── bootstrap-grid.rtl.min.css.map
│   ├── bootstrap-reboot.css
│   ├── bootstrap-reboot.css.map
│   ├── bootstrap-reboot.min.css
│   ├── bootstrap-reboot.min.css.map
│   ├── bootstrap-reboot.rtl.css
│   ├── bootstrap-reboot.rtl.css.map
│   ├── bootstrap-reboot.rtl.min.css
│   ├── bootstrap-reboot.rtl.min.css.map
│   ├── bootstrap-utilities.css
│   ├── bootstrap-utilities.css.map
│   ├── bootstrap-utilities.min.css
│   ├── bootstrap-utilities.min.css.map
│   ├── bootstrap-utilities.rtl.css
│   ├── bootstrap-utilities.rtl.css.map
│   ├── bootstrap-utilities.rtl.min.css
│   ├── bootstrap-utilities.rtl.min.css.map
│   ├── bootstrap.css
│   ├── bootstrap.css.map
│   ├── bootstrap.min.css
│   ├── bootstrap.min.css.map
│   ├── bootstrap.rtl.css
│   ├── bootstrap.rtl.css.map
│   ├── bootstrap.rtl.min.css
│   └── bootstrap.rtl.min.css.map
└── js/
    ├── bootstrap.bundle.js
    ├── bootstrap.bundle.js.map
    ├── bootstrap.bundle.min.js
    ├── bootstrap.bundle.min.js.map
    ├── bootstrap.esm.js
    ├── bootstrap.esm.js.map
    ├── bootstrap.esm.min.js
    ├── bootstrap.esm.min.js.map
    ├── bootstrap.js
    ├── bootstrap.js.map
    ├── bootstrap.min.js
    └── bootstrap.min.js.map
```

这是Bootstrap最基本的形式:编译文件，几乎可以在任何web项目中快速插入使用。我们提供编译的CSS和JS (`bootstrap.*`)，以及编译和缩小的CSS和JS (`bootstrap.min.*`)。[源映射](https://developers.google.com/web/tools/chrome-devtools/javascript/source-maps)(`bootstrap.*.map`)可用于某些浏览器的开发人员工具。捆绑的JS文件(`bootstrap.bundle.js`和最小化的`bootstrap.bundle.min.js`)包括[Popper](https://popper.js.org/)。

### CSS文件

Bootstrap包含一些选项，用于包含我们编译的部分或全部CSS。

| CSS files | Layout | Content | Components | Utilities |
| --- | --- | --- | --- | --- |
| `bootstrap.css` <br> `bootstrap.min.css` <br> `bootstrap.rtl.css` <br> `bootstrap.rtl.min.css` | Included | Included | Included | Included |
| `bootstrap-grid.css` <br> `bootstrap-grid.rtl.css` <br> `bootstrap-grid.min.css` <br> `bootstrap-grid.rtl.min.css` | [Only grid system](/docs/layout/grid/) | — | — | [Only flex utilities](/docs/utilities/flex/) |
| `bootstrap-utilities.css` <br> `bootstrap-utilities.rtl.css` <br> `bootstrap-utilities.min.css`  <br>`bootstrap-utilities.rtl.min.css` | — | — | — | Included |
| `bootstrap-reboot.css` <br> `bootstrap-reboot.rtl.css` <br> `bootstrap-reboot.min.css`  <br>`bootstrap-reboot.rtl.min.css` | — | [Only Reboot](/docs/content/reboot/) | — | — |

### JS文件

类似地，我们可以选择包含部分或全部编译后的JavaScript。

| JS Files | Popper |
| --- | --- |
| `bootstrap.bundle.js` <br> `bootstrap.bundle.min.js`   | Included |
| `bootstrap.js` <br> `bootstrap.min.js`  | – |

## Bootstrap 源代码

Bootstrap源代码下载包括编译后的CSS和JavaScript资源，以及源Sass、JavaScript和文档。更具体地说，它包括以下内容和更多内容:

```
bootstrap/
├── dist/
│   ├── css/
│   └── js/
├── site/
│   └──content/
│      └── docs/
│          └── 5.3/
│              └── examples/
├── js/
└── scss/
```

`scss/`和`js/`是CSS和JavaScript的源代码。`dist/`文件夹包含上面编译后的下载部分中列出的所有内容。`site/content/docs/`文件夹包含我们托管文档的源代码，包括我们使用Bootstrap的实例。

除此之外，任何其他包含的文件都提供了对包、许可信息和开发的支持。