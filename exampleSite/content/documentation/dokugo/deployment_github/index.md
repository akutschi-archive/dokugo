---
author: DoKugo
title: Deployment with GitHub
description: Deployment with GitHub Actions and Pages
date: 2021-04-13
categories:
    - dokugo
categories_weight: 6
tags:
    - themes
    - documentation
    - hugo
    - deployment
    - github
draft: false
---

Here we are not running `hugo` manually to create and publish the site as in the [manual deployment]({{< ref "../installation/index.md" >}}).
Instead we use [GitHub Actions](https://docs.github.com/en/actions) and publish on [GitHub Pages](https://docs.github.com/en/pages).

## Configuration

For a successful deployment we have to adjust the `config.toml`.
Just replace the `baseURL` with the correct URL.

```toml
baseURL = "https://username.github.io/repository/
```

[Here](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites) you find some information for different types of GitHub Pages sites.
The type decides which `baseURL` you have to use.

## Deployment

Since we want to use GitHub Pages for hosting our site in conjunction with GitHub Actions we have to create the file `.github/workflows/deploy.yml`. 
The directory structure is the following one:

```bash
$ tree demodokugo/ -a
demodokugo/
├── config.toml
├── content
├── .github
│   └── workflows
│       └── deploy.yml      <----- Configuration file for GitHub Actions
├── .gitmodules
└── public
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
When you go to GitHub and open `Actions` then you will see that the `build & deploy` process is started.
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
> [Here]({{< ref "../deployment_gitlab/index.md" >}}) you find the description to use GitLab Pages for your site.
