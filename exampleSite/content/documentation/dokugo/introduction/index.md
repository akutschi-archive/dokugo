---
author: DoKugo
title: Introduction
description: Introduction & Quick Start
date: 2021-04-12
categories:
    - dokugo
categories_weight: 1
tags:
    - themes
    - documentation
    - hugo
draft: false
---

A simple theme for technical documentation purposes.

![Screenshot](screenshot.png)

## Features

- LaTeX with MathJax
- Mermaid - generation of diagrams and flowcharts
- Breadcrumbs
- Table of Contents for articles

## Preview Theme with `exampleSite` Content

As you already did, just visit https://akutschi.github.io/dokugo. 

If you want to test this theme locally for playing around, just clone this repository with

```bash
git clone git@github.com:akutschi/dokugo.git
```

and then

```bash
cd exampleSite
hugo server --themesDir ../../
```

Browse site on [http://localhost:1313/dokugo](http://localhost:1313/dokugo).

## How To

### Install and Deploy Manually

Basically you have to do this:

```bash
hugo new site <sitename>
cd <sitename>
git init
git submodule add git@github.com:akutschi/dokugo.git themes/dokugo
```

Add some content and run

```bash
$ hugo 
```

The created `public` folder contains the static website. Just copy this to the server that publishes your page.

A more detailed explanation how to install and deploy can be found [here]({{< ref "../installation/index.md" >}}).

### Install and Deploy with GitHub Actions and Pages

In principal the same as in the previous section but we do not run `hugo` manually to create and publish the site.
Instead we use [GitHub Actions](https://docs.github.com/en/actions) and publish on [GitHub Pages](https://docs.github.com/en/pages).
We just have to add two folders and one file to achieve this.

The procedure can be found [here]({{< ref "../installation_github/index.md" >}}).

### Install and Deploy with GitLab CI/CD and Pages

This is even simpler than the deployment with GitHub. 
It's just one file in the project root to run [GitLab CI/CD](https://docs.gitlab.com/ee/ci/) and deploy on [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/).

The documentation can be found [here]({{< ref "../installation_gitlab/index.md" >}}).
### Configure

The configuration is done in your config file `config.toml` or `config.yaml`/`config.json` of your site.
At least choose the DoKugo theme in your config file.

```bash
theme: "dokugo"
```

An example of a config file can be found in the `exampleSite` directory. 
Just copy the content or even the whole file into the root directory of your site.

Details about the configuration can be found [here]({{< ref "../configuration/index.md" >}}).

### Create and Manage Content

Basically put your content as `markdown` files into the `content` folder. You can also create there subfolders to structure your publications. 

[Here]({{< ref "../content/index.md" >}}) are more details.

