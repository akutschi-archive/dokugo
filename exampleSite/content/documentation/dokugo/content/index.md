---
author: DoKugo
title: Content Creation and Organization
description: Create and organize content in Hugo and DoKugo
date: 2021-04-12
categories:
    - dokugo
categories_weight: 6
tags:
    - themes
    - documentation
    - themes
    - hugo
    - content
draft: false
---

## Default Folders

The basic idea is that your `content` folder has three subfolders:

- `blog` for blog articles,
- `documentation` for the content of several topics and
- `projects` for the description of projects.

Each folder itself can contain other folders.
For example, the project folder can have folders for a Raspberry Pi cluster project, a home cinema project and an art project.
Each project folder can contain multiple articles written in Markdown.

### Other Folders 

If you decide that you don't want to have the above mentioned folders, but 

- `blog`,
- `pianos`,
- `travel` and
- `gardening`

then go ahead an create these folders in the content folder. 
It might be necessary to delete `default.md` in your `archetypes` folder.
This folder can be found in the root directory of your page.
The reason for this deletion is that the default archetype does not contain all data that are required for this theme.

Additionally you have to [modify the menu]({{< ref "../configuration/index.md#menu" >}}) in the `config.toml`.
A menu in the `config.toml` that replaces the default one with the new folders could look like the following:

```yaml
[menu]
  [[menu.main]]
    name = "Blog"
    url = "/blog/"
    weight = 1
  [[menu.main]]
    name = "Pianos"
    url = "/pianos/"
    weight = 2
   [[menu.main]]
    name = "Travel"
    url = "/travel/"
    weight = 3
  [[menu.main]]
    name = "Gardening"
    url = "/gardening/"
    weight = 4
```

## Articles

The official [documentation](https://gohugo.io/content-management/organization/) has a lot of information how to organize your content. 

Recommended is the use of page bundles.
Page bundles are folders that contain an `index.md` and all page related content like images, pdf documents and other files.
To create a new page as page bundle use the following command:

```bash
hugo new blog/dokugo-is-awesome/index.md
```

This command will create the `blog` folder if not already created and a folder with the name `dokugo-is-awesome`.
The latter folder has a file `index.md` where the article will be written. 
When you open this file you will see just the so called frontmatter:

```md
---
title: "Dokugo Is Awesome"
date: 2021-04-13T22:11:28-04:00
categories:
    - blog
categories_weight: 0
tags:
    - news
draft: true
---

Content
```

You can change and add more categories as well as more tags. 
The weight of the articles can also be adjusted.
A lower weight moves the article more to the top or to the left and a higher weight moves the article to the bottom or to the right.


Read the [documentation]({{< ref "../../" >}}) to learn how to write in Markdown.
Especially the article about the [Markdown syntax]({{< ref "../../markdown-syntax.md" >}}) is very helpful to start writing in Markdown.
It's very easy and straightforward.