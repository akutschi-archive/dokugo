**The GitHub repository is just a mirror. The [original code](https://gitlab.com/akutschi/dokugo/) is maintained at [GitLab](https://gitlab.com/)**

# DoKugo

A simple theme for technical documentation purposes.

# Features

- LaTeX with MathJax
- Mermaid - generation of diagrams and flowcharts

# Getting started

## Requirement

Hugo minimum version: `0.69`

## Download

With git installed you can simply clone this repository into your themes folder:

```
cd themes
git clone git@gitlab.com:akutschi/dokugo.git
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
git clone git@gitlab.com:akutschi/dokugo.git
```

and then

```
cd exampleSite
hugo --themesDir ../../
```

Browse site on http://localhost:1313

# License

DoKugo is licensed under the [GPLv3 license](https://gitlab.com/akutschi/dokugo/blob/master/LICENSE).

# Author

[akutschi](https://gitlab.com/akutschi)

Copyright (c) 2020 akutschi


