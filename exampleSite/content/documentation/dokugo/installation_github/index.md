---
author: DoKugo
title: Installation and Deployment with GitHub
description: Installation and deployment with GitHub Actions and Pages
date: 2021-04-13
categories:
    - dokugo
categories_weight: 3
tags:
    - themes
    - documentation
    - hugo
    - installation
    - github
draft: false
---

In principal the same as in the [manual installation and deployment]({{< ref "../installation/index.md" >}}) but we do not run `hugo` manually to create and publish the site.
Instead we use [GitHub Actions](https://docs.github.com/en/actions) and publish on [GitHub Pages](https://docs.github.com/en/pages).

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

Since we want to use GitHub Pages for hosting our site in conjunction with GitHub Actions we have to create the file `.github/workflows/deploy.yml`. 
The directory structure is the - shortened - following one:

```bash
$ tree demodokugo/ -a
demodokugo/
├── archetypes
│   └── default.md
├── config.toml
├── content
.
.
.
├── .github
│   └── workflows
│       └── deploy.yml      <----- Configuration file for GitHub Actions
├── .gitmodules
├── layouts
├── public
.
.
.
```

Now we have an empty GitHub Actions configuration file.
Copy and paste the code into the `deploy.yml` file:


```yaml
name: build & deploy

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true

      - name: Build
        run: hugo

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

Now you can commit and push everything to your GitHub repository.
The steps are:

```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin git@github.com:username/repository.git
git push -u origin main
```

The last step will send everything to the GitHub repository.
When go to GitHub and open `Actions` then you will see that the `build & deploy` process is started.
After a successful finish the site will be available under the address https://username.github.io/repository.

Please obey the [guidelines](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) for using GitHub Pages.
The main points are:

- GitHub Pages is subject to the [GitHub Terms of Service](https://docs.github.com/en/articles/github-terms-of-service)
- Maximum size 1 GB
- Soft bandwidth limit of 100GB per month
- Soft limit of 10 builds per hour
- Prohibited to use as free webhosting service to run an
    - online business,
    - e-commerce site, 
    - or any other website that is primarily directed at either facilitating commercial transactions or providing commercial software as a service (SaaS)
- List of prohibited uses: [GitHub's Additional Product Terms for GitHub Pages](https://docs.github.com/en/github/site-policy/github-additional-product-terms#4-pages)

> If some of these rules are too restrictive you might look at [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/).
> Except the prohibited uses [they are more relaxed](https://forum.gitlab.com/t/what-are-the-restrictions-for-gitlab-pages-sites/15067/6) when it's about using Pages.
> Especially the rules about commercial usage are less restrictive and the maximum size is 10 GB.
> Additionally they do not enforce a bandwidth limit nor a limit on builds per hour.
> 
> [Here]({{< ref "../installation_gitlab/index.md" >}}) you find the description to use GitLab Pages for your site.
