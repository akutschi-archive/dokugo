# DoKugo

![build](https://github.com/akutschi/dokugo/actions/workflows/deploy-hugo-pages.yml/badge.svg)
![license](https://img.shields.io/github/license/akutschi/dokugo)

A simple theme for technical documentation purposes.

![Screenshot](./exampleSite/content/documentation/dokugo/introduction/screenshot.png)

# Features

- LaTeX with MathJax
- Mermaid - generation of diagrams and flowcharts
- Breadcrumbs
- Table of Contents for articles

# Getting started

## Requirement

Hugo minimum version: `0.69`

## Download

With git installed you can simply clone this repository into your themes folder:

```
cd themes
git clone git@github.com:akutschi/dokugo.git
```

For more information read [the Hugo documentation](https://gohugo.io/themes/installing-and-using-themes/).

## Configure

You may specify options in your config file config.toml or config.yaml/config.json of your site to make use of this theme's features. At least choose this theme in your config file.

```
theme: "dokugo"
```

An example of a config file can be found in the `exampleSite` directory.

## Preview theme with exampleSite content

To test this theme just clone this repository with

```
git clone git@github.com:akutschi/dokugo.git
```

and then

```
cd exampleSite
hugo server --themesDir ../../
```

Browse site on http://localhost:1313

# Contribution 

Problems? Feature requests? Improvements? 

Probably, since this theme is currently optimized for my own personal use.
Nevertheless, feel free to open tickets for issues or merge requests. 
I am willing to discuss and consider every request. 
Thank you.

# License

DoKugo is licensed under the [GPLv3 license](https://github.com/akutschi/dokugo/blob/master/LICENSE).

# Author

[akutschi](https://github.com/akutschi)

Copyright (c) 2021 akutschi

