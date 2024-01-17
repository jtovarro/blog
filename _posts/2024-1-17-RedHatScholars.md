---
layout: post
title: Create a Red Hat Developer site hosted on GitHub to enable customers and individuals to participate in a workshop
---

Have you ever think or have the need to create a page for people/customer following a workshop? If that's the case Red Hat Scholars is a framework that will make your life much easier.

Steps to deploy a Red Hat Scholar framework to create a workshop:

#### 1) Fork [https://github.com/redhat-scholars/courseware-template](https://github.com/redhat-scholars/courseware-template) repo and unclick: ‘Copy the master Branch only’. This is because this template uses a branch named gh-pages to deploy Git Hub pages trough Actions.

![Untitled (1)](https://user-images.githubusercontent.com/95486210/226349082-30cb26d1-4d2e-4392-9040-820197aad154.png)

#### 2) Click ‘Use this template’ then ‘Create new repository’.

![Untitled (2)](https://user-images.githubusercontent.com/95486210/226349353-b5047c7d-7b4e-4989-8953-caf389505aef.png)

#### 3) Click ‘Include all branches’, make it public, give it a name and hit create.

![Untitled (3)](https://user-images.githubusercontent.com/95486210/226349223-8f1b96c8-3ea3-4c79-89b7-d2a667c6709e.png)

#### 4) Once the new repo is created go to ‘Settings’ → ‘Pages’ and verify you have the build and deployment configuration.

![Untitled (4)](https://user-images.githubusercontent.com/95486210/226349400-6b22e9d3-68dc-425e-a5f9-5b7c56246f4a.png)

#### 5) In ‘Settings’ → ‘Actions’ → ‘General’ → ‘Workflow permissions’ click ‘Read and write permissions’ and hit ‘Save’, this allow GitHub Actions to redeploy correctly the page when a change in the code is done.

![Untitled (5)](https://user-images.githubusercontent.com/95486210/226349440-7f860717-06bd-40d6-8b06-5ff35aa52ba1.png)

#### 6) Modify ‘site.yml’, it is necessary to change site.url and site.start_page

```yaml
runtime:
  cache_dir: ./.cache/antora

site:
  ##Change the title
  title: Manual for GitOps workshop
  ##Change url from repo
  url: https://github.com/jtovarro/gitops-workshop-manual
  ##The start_page should be the name of your repo
  start_page: gitops-workshop-manual::index.adoc

content:
  sources:
    - url: ./
      start_path: documentation

asciidoc:
  attributes:
    release-version: master
    page-pagination: true
  extensions:
    - ./lib/tab-block.js
    - ./lib/remote-include-processor.js

ui:
  bundle:
    url: https://github.com/redhat-developer-demos/rhd-tutorial-ui/releases/download/v0.1.9/ui-bundle.zip
    snapshot: true
  supplemental_files:
    - path: ./supplemental-ui
    - path: .nojekyll
    - path: ui.yml
      contents: "static_files: [ .nojekyll ]"

output:
  dir: ./gh-pages
```

#### 7) In ‘Actions’ it is possible to see all the workflows that deployed GitHub pages, and in the ‘Environments’ section you can find the url to the GitHub page deployed.

![Untitled (7)](https://user-images.githubusercontent.com/95486210/226348602-4c078e47-0933-4244-bbf7-d87b5d6b2eba.png)

![Untitled (6)](https://user-images.githubusercontent.com/95486210/226349568-57501c42-d894-4b80-b7c9-5d97a06a7afd.png)

#### 8) To add/remove pages go to ‘documentation/modules/ROOT/pages’ and ‘documentation/modules/ROOT/nav.adoc’ to edit the sections. 

## Remote Workstation
A possible solution to avoid installing cli in our workstation is to create a remote terminal with oc,jq, and more cli already installed:
  - Using Podman or Docker:

```yaml
$ podman run -p 7681:7681 -it quay.io/redhat-scholars/ttyd-openshift:latest
$ docker run -p 7681:7681 -it quay.io/redhat-scholars/ttyd-openshift:latest
```

  - Run `localhost:7681` in your browser to access the terminal.

## Related Links
- Reference: [https://redhat-scholars.github.io/build-course/rhs-build-course/overview.html#file-structure](https://redhat-scholars.github.io/build-course/rhs-build-course/overview.html#file-structure)

<a href="https://www.buymeacoffee.com/techtovar"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a piece of fruit&emoji=🍌&slug=techtovar&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
