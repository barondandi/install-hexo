# install-hexo
Blog on GitHub with Hexo and Icarus theme

> I wanted to create a simple blog for documentation and how-to I would be writing in markup language, as GitHub repositories. I would also like to have automated the posting dates, menus, tags, navigation and adapted view for mobile devices.

# \*\*\* WIP \*\*\*

I will not be thorough, just dot the guidelines, and changes I had to make to the References below, due to updated software and my specific Linux host OS (Fedora 23). For additional information links are provided in each chapter.

1.  [Prerequisites](#1.-Prerequisites)
    -   [Install Git](#Install-Git)
    -   [Install Node.js](#Install-Node.js)
    -   [Install Hexo](#Install-Hexo)
2.  [Setting up Hexo with GitHub](#2.-Setting-up-Hexo-with-GitHub)
    -   [Setup a blog](#Setup-a-blog)
    -   [Install a theme](#Install-a-theme)
    -   [Edit YAML configuration files](#Edit-YAML-configuration-files)
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

## 2. Setting up Hexo with GitHub

### Setup a blog

We will generate the a {blogname} folder and install dependencies with the following commands:

```shell
hexo init {blogname}
cd {blogname}
npm i
git init
```
> NOTE: In our case the {blogname} will be the previously created repository ({github_user_name}.github.io)

More information of Hexo commands here [https://hexo.io/docs/commands](https://hexo.io/docs/commands)

This is the output:

```shell
[barond@fedora BLOG]$ hexo init barondandi.github.io
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
Cloning into '/home/barond/BLOG/barondandi.github.io'...
remote: Enumerating objects: 30, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (24/24), done.
remote: Total 161 (delta 12), reused 12 (delta 4), pack-reused 131
Receiving objects: 100% (161/161), 31.79 KiB | 452.00 KiB/s, done.
Resolving deltas: 100% (74/74), done.
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'
Cloning into '/home/barond/BLOG/barondandi.github.io/themes/landscape'...
remote: Enumerating objects: 4, done.        
remote: Counting objects: 100% (4/4), done.        
remote: Compressing objects: 100% (4/4), done.        
remote: Total 1067 (delta 0), reused 0 (delta 0), pack-reused 1063        
Receiving objects: 100% (1067/1067), 3.22 MiB | 3.84 MiB/s, done.
Resolving deltas: 100% (585/585), done.
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'
INFO  Install dependencies
npm WARN deprecated urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
npm WARN deprecated resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
> ejs@2.7.4 postinstall /home/vfranco/zzz_Private/DOCs/BLOG/barondandi.github.io/node_modules/ejs
> node ./postinstall.js
Thank you for installing EJS: built with the Jake JavaScript build tool (https://jakejs.com/)
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@~2.1.2 (node_modules/chokidar/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
added 253 packages from 450 contributors and audited 470 packages in 8.241s
5 packages are looking for funding
  run `npm fund` for details
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
INFO  Start blogging with Hexo!

[barond@fedora BLOG]$ cd barondandi.github.io

[barond@fedora barondandi.github.io]$ npm i
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.3 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
audited 470 packages in 1.3s
5 packages are looking for funding
  run `npm fund` for details
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details

[barond@fedora barondandi.github.io]$ git init
Initialized empty Git repository in /home/vfranco/zzz_Private/DOCs/BLOG/barondandi.github.io/.git/
```

## Install a theme

You have a lot of Hexo themes to choose from here [https://hexo.io/themes/](https://hexo.io/themes/).

Once you decide your mind, fork it to customize it or just get the GitHub repo url from the theme info.

```shell
git submodule add {theme-github-url} themes/{theme-name}
```
You have the installation instructions inside each of the themes, for example, you could check this one: [https://github.com/klugjo/hexo-theme-clean-blog](https://github.com/klugjo/hexo-theme-clean-blog)

I will be using another theme: [https://github.com/ppoffice/hexo-theme-icarus](https://github.com/ppoffice/hexo-theme-icarus)

You can find detailed installation instructions in "Getting Started with Icarus" ([https://blog.zhangruipeng.me/hexo-theme-icarus/uncategorized/getting-started-with-icarus/](https://blog.zhangruipeng.me/hexo-theme-icarus/uncategorized/getting-started-with-icarus/))

We will install Icarus as a Git submodule with the following command:
```shell
git submodule add https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus
```

### Edit YAML configuration files

You can modify the files using `vi`, `nano`, Hexo commands ([https://hexo.io/docs/commands](https://hexo.io/docs/commands)) or any text editor you feel comfortable with.

> NOTE: I would recommend Atom or Visual Studio, as they come with a lot of plugins that make life a lot easier.

We start by editing the \_config.yml file in the main folder. A description of all the parameters we can change is here: [https://hexo.io/docs/configuration](https://hexo.io/docs/configuration).


Some themes may have an example configuration file, so we would start by copying that theme example file to the `_config.yml` file in the theme folder:

´´´Shell
cp themes/{theme-name}/\_config.yml.example themes/{theme-name}/\_config.yml
´´´




Next, activate Icarus in your site’s _config.yml file:
_config.yml
theme: icarus

or use the hexo command to change the theme to Icarus:
Shell
hexo config theme icarus






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


## 3. References and Credits

This document is based on the following resources. I really thank the authors for sharing their knowledge and trouble:

-   How to setup a blog on github with Hexo - [https://zirho.github.io/2016/06/04/hexo/](https://zirho.github.io/2016/06/04/hexo/)


-   Hexo docs - [https://hexo.io/docs/](https://hexo.io/docs/)
-   Hexo themes - [https://hexo.io/themes/](https://hexo.io/themes/)
-   github pages - [https://pages.github.com/](https://pages.github.com/)


## 4. Summary

-   **Objetive:** Simple yet powerful blog deployment using static GitHub Pages service.
