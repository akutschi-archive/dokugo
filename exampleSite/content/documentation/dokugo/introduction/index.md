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

Just visit https://akutschi.github.io/dokugo to preview this theme. 
But if you want to test this theme locally for playing around, just clone this repository with

```bash
git clone git@github.com:akutschi/dokugo.git
```

and then

```bash
cd exampleSite
hugo server --themesDir ../../
```

The output of the command above shows you the address, but usually you can find the page at [http://localhost:1313/dokugo](http://localhost:1313/dokugo).

## How To

### Install

Basically you have to do this:

```bash
mkdir -p <SITENAME>/content
cd <sitename>
git init
git submodule add git@github.com:akutschi/dokugo.git themes/dokugo
```

Configure, add some content and run

```bash
$ hugo 
```

The created `public` folder contains the static website. Just copy this to the server that publishes your page.

A more detailed explanation how to install this theme can be found [here]({{< ref "../installation/index.md" >}}).

### Configure

The configuration is done in your config file `config.toml`, `config.yaml` or `config.json` of your site.
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

### Deploy Manually

The description of the manual deployment can be found [here]({{< ref "../deployment_manual/index.md" >}}).

### Deploy with GitHub Actions and Pages

In principal the same as in the previous section but we do not run `hugo` manually to create and publish the site.
Instead we use [GitHub Actions](https://docs.github.com/en/actions) and publish on [GitHub Pages](https://docs.github.com/en/pages).
We just have to add two folders and one file to achieve this.

The procedure can be found [here]({{< ref "../deployment_github/index.md" >}}).

### Deploy with GitLab CI/CD and Pages

This is even simpler than the deployment with GitHub. 
It's just one file in the project root to run [GitLab CI/CD](https://docs.gitlab.com/ee/ci/) and deploy on [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/).

The documentation can be found [here]({{< ref "../deployment_gitlab/index.md" >}}).

