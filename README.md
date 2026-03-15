# Midori

Midori is a clean Hugo theme with a left navigation rail, optional table of contents, mobile app bar and drawer navigation, multilingual UI strings, and a lightweight reading-focused layout.

[简体中文说明](README.zh-CN.md)

## Features

- Clean three-column layout on desktop: navigation, content, TOC
- Mobile app bar with drawer-style navigation
- TOC rendered only when the current page has real heading links
- Back-to-top button
- Hugo i18n support for built-in UI text
- Language switcher that only appears when the current page has a translated counterpart
- Optional homepage page listing

## Requirements

- Hugo `>= 0.146.0`

## Install

Add the theme to your site:

```powershell
git submodule add https://github.com/Saiba-Midori-Projects/gohugo-theme-midori.git themes/midori
```

Then enable it in your site config:

```toml
theme = "midori"
```

If you clone the theme into a different folder name, `theme` must match that folder name.

## Quick Start

Example site config:

```toml
baseURL = "https://example.org/"
defaultContentLanguage = "zh-CN"
defaultContentLanguageInSubdir = false
theme = "midori"

[languages]
  [languages.zh-CN]
    languageCode = "zh-CN"
    languageName = "简体中文"
    title = "My Site"
    weight = 1

  [languages.en]
    languageCode = "en-US"
    languageName = "English"
    title = "My Site"
    weight = 2

[markup]
  [markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true
  [markup.tableOfContents]
    startLevel = 1
    endLevel = 3

[params]
  themeName = "Midori"
  version = "0.1.1"
  homeListPages = false
  # homeListSections = ["posts"]
```

## Custom Parameters

The theme currently reads these custom parameters from `params`:

```toml
[params]
  themeName = "Midori"
  version = "0.1.1"
  favicon = "/favicon.ico"
  backgroundImage = "images/default_bg.png"
  homeListPages = false
  # homeListSections = ["posts"]

  [params.author]
    name = "Your Name"
    email = "you@example.com"
```

- `params.backgroundImage`: page background image, used by the main layout. Relative static paths such as `images/bg.png` work well.
- `params.favicon`: favicon URL. If omitted, the theme falls back to `/favicon.ico`.
- `params.author.name`: author name shown in the footer copyright area.
- `params.author.email`: author email used for the footer mail link.
- `params.themeName`: theme name shown in the browser console badge.
- `params.version`: theme version shown in the browser console badge.
- `params.homeListPages`: enables homepage page listing mode.
- `params.homeListSections`: limits homepage listing to specific sections when `homeListPages = true`.

## Navigation

You can manage the left navigation in either of these ways.

Use `menus.main` in site config:

```toml
[menus]
  [[menus.main]]
    identifier = "menu.home"
    name = "Home"
    pageRef = "/"
    weight = 10

  [[menus.main]]
    identifier = "menu.about"
    name = "About"
    pageRef = "/about"
    weight = 20
```

Or define menu membership in page front matter:

```toml
+++
title = "About"
[menus]
  [menus.main]
    weight = 20
+++
```

If a menu entry has an `identifier`, the theme will try to translate it through Hugo `i18n`.

## Multilingual Support

Built-in UI text is translated through Hugo `i18n`. The theme already includes:

- `i18n/zh-CN.toml`
- `i18n/en.toml`

The language switcher is shown only when:

- the current regular page has a translated version
- or the home page has actual translated home content files such as `content/_index.en.md`

For example:

```text
content/_index.md
content/_index.en.md
content/about.md
content/about.en.md
```

If `about.en.md` does not exist, the switcher will be hidden on `/about/`.

## TOC Behavior

- TOC is shown only when Hugo generates actual heading links for the page
- the mobile TOC toggle is also hidden when there is no real TOC
- TOC levels follow your Hugo config, for example:

```toml
[markup.tableOfContents]
  startLevel = 1
  endLevel = 3
```

## Homepage Listing

By default, the home page renders only its own content.

To turn the home page into a blog-like list:

```toml
[params]
  homeListPages = true
```

To limit the list to specific sections:

```toml
[params]
  homeListPages = true
  homeListSections = ["posts"]
```

## Theme Development

This repository keeps demo content in `exampleSite/content`.

For local theme development, run this from the theme repository root:

```powershell
hugo server -D
```

The root `hugo.toml` already points `contentDir` to `exampleSite/content`, so you do not need a long `--source` command for normal development.

Generated demo output is ignored via:

- `exampleSite/public/`
- `exampleSite/.hugo_build.lock`

## Repository Layout

```text
assets/           CSS and JavaScript
exampleSite/      Demo content and demo site config
i18n/             UI translations
layouts/          Theme templates and partials
static/           Static assets
```

## License

[MIT](LICENSE)
