# DoKugo

![build](https://github.com/akutschi/dokugo/actions/workflows/deploy-hugo-pages.yml/badge.svg)
![license](https://img.shields.io/github/license/akutschi/dokugo)

A simple theme for technical documentation purposes.

![Screenshot](./exampleSite/content/documentation/dokugo/introduction/screenshot.png)

## Features

- LaTeX with MathJax
- Mermaid - generation of diagrams and flowcharts
- Breadcrumbs
- Table of Contents for articles

## Preview Theme with `exampleSite` Content

If you want to test this theme just clone this repository with

```
git clone git@github.com:akutschi/dokugo.git
```

and then

```
cd exampleSite
hugo server --themesDir ../../
```

Browse site on http://localhost:1313.
Or just visit https://akutschi.github.io/dokugo.

## Quick Start

### Requirement

Hugo minimum version: `0.69`

### Download

Create a folder that holds your project and there a folder called `content`. Assuming that `git` is installed just initialize Git and simply clone this repository as submodule into your themes folder:

```bash
mkdir -p <SITENAME>/content
cd <SITENAME>
git init
git submodule add git@github.com:akutschi/dokugo.git themes/dokugo
```

Now we have created a new Hugo site, initialized a git repository and added the theme as submodule to our site.

### Configuration and Content

Now we add the [configuration file](https://akutschi.github.io/dokugo/documentation/dokugo/configuration/) and the [content](https://akutschi.github.io/dokugo/documentation/dokugo/content/) from the example site to get started.

```bash
cp -r themes/dokugo/exampleSite/content/* ./content/
cp themes/dokugo/exampleSite/config.toml ./
```

### Start
Start the built-in Hugo web server with `hugo server` to check the page:

```bash
$ hugo server
Start building sites … 

                   | EN  
-------------------+-----
  Pages            | 76  
  Paginator pages  |  0  
  Non-page files   |  1  
  Static files     |  9  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 62 ms
Watching for changes in /home/hugo/<SITENAME>/{content,themes}
Watching for config changes in /home/hugo/<SITENAME>/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/dokugo/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

Open [http://localhost:1313/](http://localhost:1313/) in your web browser and then you can see your website. 

## Documentation

The documentation can be found on the [demo site](https://akutschi.github.io/dokugo/documentation/dokugo/) or  [here](http://localhost:1313/dokugo/documentation/dokugo/) when you are running the `exampleSite` with the command above.
## Contributions 

Problems? Feature requests? Improvements? 

Although this theme is currently optimized for my personal use, feel free to open tickets for issues or merge requests. 
I am happy to discuss and consider every request. 
Thank you.

## License

DoKugo is licensed under the [GPLv3 license](https://github.com/akutschi/dokugo/blob/master/LICENSE).

## Author

[akutschi](https://github.com/akutschi)

Copyright (c) 2021 akutschi

