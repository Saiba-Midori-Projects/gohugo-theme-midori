# gohugo-theme-midori
Midori: A simple Hugo theme.

---

Midori 是一个简洁、清爽的 Hugo 主题，基于 Hugo Pipes 提供 CSS/JS 构建与指纹（生产环境）能力，适合博客与文档型站点。

## 安装
您可以通过如下方式安装 Midori 主题：

1. 作为子模块安装：
  ```bash
  git submodule add https://github.com/Saiba-Midori-Projects/gohugo-theme-midori.git themes/midori
  ```
2. 在站点配置中启用：
  ```toml
  theme = "midori"
  ```

## 快速开始
* 启动开发服务器：
  ```bash
  hugo server
  ```
* 用于生产构建：
  ```bash
  HUGO_ENV=production hugo
  ```

## 站点配置示例
在 `hugo.toml` 中：

```toml
baseURL = "https://example.org/"
languageCode = "zh-CN"
title = "Hugo Theme - Midori"

[menus]
  [[menus.main]]
    name = "Home"
    pageRef = "/"
    weight = 10

  [[menus.main]]
    name = "Posts"
    pageRef = "/posts"
    weight = 20

  [[menus.main]]
    name = "Tags"
    pageRef = "/tags"
    weight = 30

[params]
  themeName = "Midori"
  version = "0.1.1"
  backgroundImage = "images/default_bg.png" # 可替换为你自己的背景图
  [params.author]
    name = "KFACBT"
    email = "gytxtx@outlook.com"

disableKinds = ["RSS"] # 如需 Tags，请勿禁用 taxonomy/term
```

## 可用参数
* `params.themeName`：主题名（用于控制台输出）
* `params.version`：主题版本（用于控制台输出）
* `params.backgroundImage`：页面背景图（默认 `static/images/default_bg.png`）
* `params.author.name` / `params.author.email`：作者信息
* `favicon`：在 `static/favicon.ico` 下提供即可自动生效

## 布局与资源
本主题基于默认 Hugo 主题模板修改，结构如下：

* 模板入口：`layouts/_default/baseof.html`
* CSS：`assets/css/main.css`
* JS：`assets/js/main.js`

## 兼容
最低 Hugo 版本：`0.146.0`（不需要 extended）

## 许可
MIT License，详情见 [LICENSE](https://github.com/Saiba-Midori-Projects/gohugo-theme-midori/blob/main/LICENSE)。

## 其他
若有其他问题，欢迎提交 Issue 或 Pull Request 反馈。

