---
author: DoKugo
title: Configuration
description: Configure Hugo and DoKugo
date: 2021-04-12
categories:
    - dokugo
categories_weight: 5
tags:
    - themes
    - documentation
    - hugo
    - configuration
draft: false
---

Now it's time to configure your site. 
The configuration is done in the `config.toml` file.
This file is located in the root of your Hugo project.
After running `hugo new site demodokugo` your directory and file structure should look like the following one:

```bash
$ tree demodokugo/
demodokugo/
├── archetypes
│   └── default.md
├── config.toml      <----- The configuration file
├── content
├── data
├── layouts
├── static
└── themes
```

## Overview

The whole `config.toml` file is the following one: 

```yaml
baseURL = "https://www.example.com"
languageCode = "en-us"
title = "DemoDoKugo"
theme = "dokugo"
enableEmoji = true  


[taxonomies]
  tag = "tags"
  category = "categories"

[params]
  homeText = "Simplicity!"
  dateFormat = "2006-01-02"

[params.footer]
  footerText = "This is a very simple and clean theme for documentation purposes. Main goal is a layout that does not distract the reader and can be navigated easily."  
  github = "https://github.com/username/repository"
  gitlab = "https://gitlab.com/username/repository"
  # This line enables (true) or disables (false) the "Powered by Hugo. Theme DoKugo." line.
  poweredByLine = true 

[markup]
  [markup.highlight]
    lineNos = false
    lineNumbersInTable = true
    style = "solarized-dark"
  [markup.tableOfContents]
    endLevel = 6
    ordered = false
    startLevel = 2

[menu]
  [[menu.main]]
    name = "Blog"
    url = "/blog/"
    weight = 1
  [[menu.main]]
    name = "Projects"
    url = "/projects/"
    weight = 2
   [[menu.main]]
    name = "Documentation"
    url = "/documentation/"
    weight = 3
```

Now we go through the configuration file section by section.

### General

All options for this section can be found in the [Hugo documentation](https://gohugo.io/getting-started/configuration/).

Here we use just a few, but feel free to use as much as you need.

- `baseURL`
    - This is the address where the site will be available. If you are using GitLab Pages then it must be something like `https://username.gitlab.io` or `https://username.gitlab.io/repository`.
- `languageCode`
    - This is the default language for the site. 
    - Currently, this theme does not support multi-language sites.
- `title`
    - The title of the page.
- `theme`
    - Here you can set the theme. 
    - Since you are reading this documentation the theme is `dokugo`.
- `enableEmoji`
    - The setting enables emoticons.

### Taxonomies

Taxonomies allow grouping of content. 
The [Hugo documentation](hhttps://gohugo.io/content-management/taxonomies#configure-taxonomies) shows how taxonomies can be configured.

Here only `tags` and `category` are used for grouping. Usually you can ignore this section.

### Params

Values in this section will populate the `.Site.Params` variable and can be used in templates.
### Params.Footer

This section lists the parameters that will be used in the site footer. 

- `footerText`
    - The text appears that will be shown in the about section of the footer.
- `github` and `gitlab`
    - Links to GitHub and GitLab.
    - The icons only appear when the parameters are defined.
    - There can be added more like Twitter or LinkedIn, just request your service via [ticket](https://github.com/akutschi/dokugo/issues/new).
- `poweredByLine`
    - This shows `Powered by Hugo. Theme DoKugo.
    - **Would be nice if this setting stays unchanged**, but it's your choice.
    - Set to false if want to get rid of this line.
### Markup

This section is about how to handle Markdown and other markup related stuff. 
See [Hugo documentation](https://gohugo.io/getting-started/configuration-markup).
#### Markup.Highlight

This section affects the [syntax highlighting](https://gohugo.io/getting-started/configuration-markup#highlight). 

- `lineNos`
    - This disables the line numbers.
    - Enable with `true`.
- `lineNumbersInTable`
    - This defined how line numbers are shown.
- `style`
    - This is the theme of the syntax highlighting.
    - Here is a [Gallery](https://xyproto.github.io/splash/docs/all.html) of themes for syntax highlighting.
#### Markup.TableOfContents

This setting influences the table of content.

- `endLevel`
    - This sets the end where rendering of the ToC stops.
- `ordered`
    - Whether or not to generate an ordered list instead of an unordered list.
- `startLevel`
    - This sets the beginning where rendering of the ToC starts.
### Menu

Here you can modify the menus.

#### Menu.Main

In the moment there is just one menu.
The one at the top of the site.
The current configuration represents in the moment the subfolders in the `content` directory.
Go [here](({{< ref "../content/index.md" >}})) for more details and how to create and manage content.

If you want to add a menu entry at the top just add the following snippet below the `[menu]` section.

```yaml
[[menu.main]]
    name = "Blog"
    url = "/blog/"
    weight = 1
```

- `name`
    - The name of the entry that will also be shown in the menu.
- `url`
    - The relative path, seen from the `content` folder.
- `weight`
    - The position of the entry.
    - Lower values go to the left/top, higher values to the right/bottom.
