---
author: DoKugo
title: Installation and Manual Deployment
description: Simple installation with manual deployment
date: 2021-04-13
categories:
    - dokugo
categories_weight: 2
tags:
    - themes
    - documentation
    - hugo
    - installation
draft: false
---

This guide will help you to install Hugo and DoKugo. 
You will be pointed to the documents to configure and create content for your site.
Finally you create the static site and deploy it to your webhoster.

## Requirements

### Hugo 

The required minimum Hugo version can be found on the [DoKugo](https://github.com/akutschi/dokugo) site.
To install Hugo, head to the [release site](https://github.com/gohugoio/hugo/releases) and download the release for your Operating System and architecture.
Hugo Extended is not required, but doesn't harm.

If your are using Linux, it might be sufficient to install the version in your default repositories.
In Ubuntu just use:

```bash
$ sudo apt install hugo
```

To check if the installation was successful with `hugo version`, you should get the following output:

```bash
$ hugo version
Hugo Static Site Generator v0.80.0-792EF0F4/extended linux/amd64 BuildDate: 2020-12-31T13:46:18Z
```

### Git

The next requirement is Git.
Just go to the [Git site](https://git-scm.com/downloads) and follow the instructions, they are straightforward. 

In the case of Linux the usage of the package manager is in most cases recommended. 
If you are using Ubuntu use:

```bash
$ sudo apt install git
```

Check your installation with `git version`.
You should get the following result:

```bash
$ git version
git version 2.25.1
```

## Install DoKugo

Basically you have to do this:

```bash
hugo new site demodokugo
cd demodokugo
git init
git submodule add git@github.com:akutschi/dokugo.git themes/dokugo
```

With these first command `hugo new site demodokugo` you created a new site with the following directory structure:

```bash
$ tree demodokugo/
demodokugo/
├── archetypes
│   └── default.md
├── config.toml      <----- The configuration file
├── content          <----- Here goes your own content
├── data
├── layouts
├── static
└── themes
```

With `cd demodokugo` you change the directory and `git init` initializes Git.
The last command downloads and adds the DoKugo theme to your site.
Running this command will have the following output:

```bash 
$ git submodule add git@github.com:akutschi/dokugo.git themes/dokugo
Cloning into '/home/arthurk/Documents/demodokugo/themes/dokugo'...
remote: Enumerating objects: 463, done.
remote: Counting objects: 100% (463/463), done.
remote: Compressing objects: 100% (203/203), done.
remote: Total 1095 (delta 251), reused 395 (delta 213), pack-reused 632
Receiving objects: 100% (1095/1095), 320.29 KiB | 4.39 MiB/s, done.
Resolving deltas: 100% (562/562), done.
```

And the directory structure will look like the following one:

```bash
$ tree demodokugo/ -d
demodokugo/
├── archetypes
├── content
├── data
├── layouts
├── static
└── themes
    └── dokugo          <----- The submodule with the theme
        ├── archetypes
        ├── exampleSite
        │   └── content
        │       ├── blog
        │       ├── documentation
        │       │   └── dokugo
        │       │       └── introduction
        │       └── projects
        ├── layouts
        │   ├── _default
        │   ├── partials
        │   └── shortcodes
        └── static
            ├── css
            ├── favicon
            └── js
```

## Configuration

It's time now to [configure]({{< ref "../configuration/index.md" >}}) your site.

We go the quick route.
Just copy and paste the following into your `config.toml` in the root directory of your website:

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

A more detailed explanation about the configuration can be found [here]({{< ref "../configuration/index.md" >}}).

## Content

Now, add some [content]({{< ref "../configuration/index.md" >}}) and when you think you're ready you can check with the command `hugo server`:

```bash
$ hugo server
Start building sites … 

                   | EN  
-------------------+-----
  Pages            |  7  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  9  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 5 ms
Watching for changes in /home/hugo/Documents/demodokugo/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /home/hugo/Documents/demodokugo/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

This will start a small webserver and when you open [http://localhost:1313/](http://localhost:1313/) in your web browser then you can see your website. 
Changes will be shown immediately.

## Deployment

Now, when you think you're ready to publish something just run `hugo`:

```bash
$ hugo 
Start building sites … 

                   | EN  
-------------------+-----
  Pages            |  7  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  9  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 14 ms
```

This command will create the `public` folder inside your project root. 

```bash
$ tree demodokugo/ -L 1
demodokugo/
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── public      <----- Your generated content
├── resources
├── static
└── themes
```

There are now dozen of possibilities how to publish the site and it is impossible to cover them all.
Best of all, head to your webhoster and check their documentation how to upload your website to the webserver.
Sometimes there is a web interface where you can drag and drop your files to publish them.

Basically, copy the content of the `public` directory to the server that publishes your page.
