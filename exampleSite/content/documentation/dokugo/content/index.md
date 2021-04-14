---
author: DoKugo
title: Content Creation and Organization
description: Create and organize content in Hugo and DoKugo
date: 2021-04-14
categories:
    - dokugo
categories_weight: 4
tags:
    - themes
    - documentation
    - themes
    - hugo
    - content
draft: false
---

## Default Folders

The basic idea is that your `content` folder has three subfolders, the section folders:

- `blog` for blog articles,
- `documentation` for the content of several topics and
- `projects` for the description of projects.

Each folder can contain other folders.
For example, the project folder can have folders for a Raspberry Pi cluster project, a home cinema project and an art project.
Each project folder can contain multiple articles written in Markdown.

### _index.md File

The `_index.md` file is crucial for the structure of the site.
This file adds front matter and content to the list pages. 
Every section folder that contains an `_index.md` file will list all articles and and other sections that are direct beneath it. 

```yaml
---
title: This is an awesome theme
categories_weight: 1
---
```

The official documentation has more information on this [topic](https://gohugo.io/content-management/organization/#index-pages-_indexmd).

### Other Folders 

If you decide that you don't want to have the above mentioned section folders, but 

- `blog`,
- `pianos`,
- `travel` and
- `gardening`

then go ahead an create these folders in the content folder. 
But remember to create and to edit the `_index.md` in each folder.

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
When you open this file you will see just the so called front matter:

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