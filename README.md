# CSScomb Config Custom

这是我自己定制并将持续维护的 CSScomb 配置。  
这份配置主要包含两部分规则：

* 通用规则
* 排序规则

自定制配置的原因：  
CSScomb 内置了三种规则：`csscomb`、`yandex`和`zen`，但在使用这些内置规则的过程中遇到了两个问题：

1. 不方便根据项目需要和个人/团队编程习惯针对性修改个别规则。
2. 内置的属性排序规则过旧，包含过多已弃用或已很少用的属性而缺少新的常用的属性。而且规则里针对`浏览器引擎`的属性几乎都是不必要的，因为现在的项目通常会在打包构建时使用相应的工具自动按需添加 prefix 来实现浏览器兼容，所以已经很少需要直接在代码中手写大量针对浏览器引擎的样式。

通过自定制配置，能有效解决上面两个问题，更方便地针对性修改和调整规则，并提高运行 CSScomb 时的性能。其中所使用的属性排序规则基于 CSScomb 的 [zen](https://github.com/csscomb/csscomb.js/blob/dev/config/zen.json) 规则和 [stylelint-config-rational-order](https://github.com/constverum/stylelint-config-rational-order)，我对它们做了综合整理，删除了已弃用或几乎不会再使用的属性，增加了一些常用的新的属性。

## 了解 CSScomb

[GitHub Repositories](https://github.com/csscomb)

## 编辑器设置

以 VSCode 为例：

* 首先，在 VSCode 中安装 [CSScomb 插件](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-csscomb)
* 然后，在 VSCode 的快捷键设置里为它添加快捷键，例如：

  ```json
  {
    "command": "csscomb.execute",
    "key": "shift+alt+c",
    "when": "editorTextFocus&&!editorReadonly"
  }
  ```

* 项目级使用配置：下载 `.csscomb.json` 后放置在项目的根目录
* 全局使用配置：下载 `.csscomb.json` 后放置在系统里合适的位置，然后在 VSCode 的 `settings.json` 文件中增加下面内容：

  ```js
  "csscomb.preset": "C:\\Users\\<username>\\.csscomb.json" // 文件路径因人而异
  ```

* 最后，在 VSCode 中执行命令 `CSScomb:Format styles` 或使用快捷键来格式化样式代码
