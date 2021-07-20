---
author: DoKugo
title: Deployment with GitLab
description: Deployment with GitLab CI/CD and Pages
date: 2021-04-13
categories:
    - dokugo
categories_weight: 7
tags:
    - themes
    - documentation
    - hugo
    - deployment
    - gitlab
draft: false
---

This is even simpler than the deployment with [GitHub]({{< ref "../deployment_github/index.md" >}}). 
It's just one file in the project root to run [GitLab CI/CD](https://docs.gitlab.com/ee/ci/) and to deploy on [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/).

## Configuration

For a successful deployment we have to adjust the `config.toml`.
Just replace the `baseURL` with the correct URL.

```toml
baseURL = "https://username.gitlab.io/repository/
```

[Here](https://docs.gitlab.com/ee/user/project/pages/getting_started_part_one.html#gitlab-pages-default-domain-names) you find some information for the different domain names for GitLab Pages.
The type decides which `baseURL` you have to use.

## Deployment

Since we want to use GitLab Pages for hosting our site in conjunction with GitLab CI/CD we have to create the file `.gitlab-ci.yml`. 
The directory structure is the following one:

```bash
$ tree demodokugo/ -a
demodokugo/
├── config.toml
├── content
├── .gitlab-ci.yml      <----- Configuration file for GitHub Actions
└── .gitmodules
```

Now we have an empty GitLab CI/CD configuration file.
Copy and paste the code into the `deploy.yml` file:


```yaml
image: registry.gitlab.com/pages/hugo:latest

variables:
  GIT_SUBMODULE_STRATEGY: recursive

pages:
  script:
    - hugo
  artifacts:
    paths:
      - public
  only:
    - master
```

Now you can commit and push everything to your GitHub repository.
The steps are:

```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin git@gitlab.com:username/repository.git
git push -u origin main
```

The last step will send everything to the GitLab repository.
When you go to GitLab and open `CI/CD` then you will see that the building and deploy process is started.
After a successful finish the site will be available under the address https://username.gitlab.io/repository.
