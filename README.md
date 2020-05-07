# install-hexo
Blog on GitHub with Hexo and Icarus theme

> I wanted to create a simple blog for documentation and how-to I would be writing in markup language, as GitHub repositories. I would also like to have automated the posting dates, menus, tags, navigation and adapted view for mobile devices.

I will not be thorough, just dot the guidelines, and changes I had to make to the References below, due to updated software and my specific Linux host OS (Fedora 23).

1.  [Prerequisites](#1.-Prerequisites)
    -   [Install Git](#Install-Git)
    -   [Install Node.js](#Install-Node.js)
    -   [Install Hexo](#Install-Hexo)
2.  [Setting up Hexo with GitHub](#2.-Setting-up-Hexo-with-GitHub)
3.  [References and Credits](#3.-References-and-Credits)
4.  [Summary](#4.-Summary)

## 1. Prerequisites

### Install Git

You can check updated details in "[Getting Started - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)".

-   Linux (Ubuntu, Debian): `sudo apt install git-all`
-   Linux (Fedora, Red Hat, CentOS): `sudo dnf install git-all`
-   Windows: Download & install [git](https://git-scm.com/download/win).
-   Mac: Download & install [git](https://git-scm.com/download/mac).

### Install Node.js

As suggested in ["How to install Node.js"](https://nodejs.dev/how-to-install-nodejs) the best way to install **Node.js** is with **nvm** ([https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)).

To install or update **nvm**, you should run the [install script](https://github.com/nvm-sh/nvm/blob/v0.35.3/install.sh). To do that, you may either download and run the script manually, or use the following cURL or Wget command:

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash`

`wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash`

Once nvm is installed, restart the terminal and run the following command to install Node.js (you can check latest available versions in [https://nodejs.org/](https://nodejs.org/) but I would recommend to let nvm to automatically select the latest LTS version for you):

```shell
nvm install --lts
```
You can check the installed version with `nvm current` or `nvm alias`. This is the output:

```shell
[barond@fedora]$ nvm install --lts
Installing latest LTS version.
Downloading and installing node v12.16.3...
Downloading https://nodejs.org/dist/v12.16.3/node-v12.16.3-linux-x64.tar.xz...
########################################################################################################################################### 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v12.16.3 (npm v6.14.4)
Creating default alias: default -> lts/* (-> v12.16.3)
[barond@fedora]$ nvm current
v12.16.3
[barond@fedora]$ nvm alias
default -> lts/* (-> v12.16.3)
node -> stable (-> v12.16.3) (default)
stable -> 12.16 (-> v12.16.3) (default)
iojs -> N/A (default)
unstable -> N/A (default)
lts/* -> lts/erbium (-> v12.16.3)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.20.1 (-> N/A)
lts/erbium -> v12.16.3
```

### Install Hexo

Once all the requirements are installed, you can install Hexo with npm. Detailed and advanced procedure is explained here: [https://hexo.io/docs/#Install-Hexo](https://hexo.io/docs/#Install-Hexo).

```shell
npm install -g hexo-cli
```
This is the output:

```shell
[barond@fedora ~]$ npm install -g hexo-cli
/home/barond/.nvm/versions/node/v12.16.3/bin/hexo -> /home/barond/.nvm/versions/node/v12.16.3/lib/node_modules/hexo-cli/bin/hexo
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@~2.1.2 (node_modules/hexo-cli/node_modules/chokidar/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

+ hexo-cli@3.1.0
added 81 packages from 322 contributors in 7.941s
```

### Set up a GitHub repository

Set up a github repo with the name: {github_user_name}.github.io.

> In my case it was barondandi.github.io

If you did it right you should be able to access the webpage [https://{github_user_name}.github.io](https://{github_user_name}.github.io)

> In my case it is [https://barondandi.github.io](https://barondandi.github.io)

If you need extra help detailed procedure is explained in "Creating a GitHub Pages site" ([https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site](https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site)).

Setting up Hexo with GitHub

Setup a blog

$ hexo init {blogname}
$ cd {blogname}
$ npm i
$ git init

This will generate the {blogname} folder and install dependencies.
Install a theme

Browse here to find out something cool.

Once you decide your mind, fork it to customize it or just get the github repo url from the theme info.

ex) https://github.com/ppoffice/hexo-theme-minos

$ git submodule add {theme-github-url} themes/{theme-name}

Copy \_config.yml.example to \_config.yml

1


´´´shell
    $ cp themes/{theme-name}/_config.yml.example themes/{theme-name}/_config.yml


*Some themes may differ on _config.yml.example file name
Refer to the theme docs

Update _config.yml to use newly installed theme. (Don't get confused with the theme config file)

1



$ vi _config.yml

Find theme attribute and change it.
ex) theme: hueman


theme: {theme-name}

Setup blog & deploy info

Edit _config.yml in root folder. (Don't get confused with the theme config file)


$ vi _config.yml

Update blog info as desired.
Below is my own for instance.


title: CodePaste
subtitle:
description:
author: Joshua Youngjae Ji
language: en
timezone: America/Los_Angeles

Add below code at the bottom of the file for deploy on github repo.


deploy:
  type: git
  repo: {your github repo url}
  branch: master
  message: "Site updated: {{ now('YYYY-MM-DD HH:mm:ss') }}"

Deploy the blog


$ npm i -S hexo-deployer-git
$ hexo deploy

At this point, you should be able to see your blog at http://{blogname}.github.io.
Add the source to the github repository (optional)

To maintain version of the code, you can make another branch and push the commits.

$ git remote add origin {your-git-repo-url}
$ git checkout -b source
$ git push origin source

Deploy new post

Adding a new post

1



$ hexo new {postname}

Edit the new post file

1



$ vi source/_posts/{postname}.md

Regenerate files and deploy at once

1



$ hexo generate -d

Happy posting!
__


## References and Credits

This document is based on the following resources. I really thank the authors for sharing their knowledge and trouble:

-   How to setup a blog on github with Hexo - [https://zirho.github.io/2016/06/04/hexo/](https://zirho.github.io/2016/06/04/hexo/)


-   Hexo docs - [https://hexo.io/docs/](https://hexo.io/docs/)
-   Hexo themes - [https://hexo.io/themes/](https://hexo.io/themes/)
-   github pages - [https://pages.github.com/](https://pages.github.com/)


## 7. Summary

-   **Objetive:** Simple yet powerful blog deployment using static GitHub Pages service.
