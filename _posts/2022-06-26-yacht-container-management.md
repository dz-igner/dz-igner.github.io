---
layout: post
title: Yacht - A container management UI with a focus on templates and 1-click deployments
date: 2022-06-26 07:27 +0200
category: self-hosted
author: 
tags: docker
summary: 
---

## Introduction

![Darth Vaper][def]{: width="200" height="200" }{: .left }{: .shadow }

### What is Yacht?

A web interface for managing docker containers with an emphasis on templating to provide one-click deployments of dockerized applications. Think of it like a decentralized app store for servers that anyone can make packages for.

### Features

* Container templating compatibility (Portainer compatible)
* Basic container management
* Easy template updating
* Template Variables to allow for a one-click experience
* Guided container deployment
* Dashboard for monitoring all of your docker containers in one place
* Docker-compose compatibility and editor
* One click editing of containers

### Features (Coming Soon!)

* User Managment
* Container CLI attachment _If you want something that's not planned please open a feature request issue and we'll see about getting it added_.

### Templates

Currently Yacht is compatible with portainer templates. You'll add a template url in the "Add Template" settings. The the template will be read, separated into apps, and imported into the database. The apps associated with the templates are linked via a db relationship so when the template is removed, so are the apps associated with it. We store the template url as well so we can enable updating templates with a button press.

We recommend starting with:

```html
https://raw.githubusercontent.com/SelfhostedPro/selfhosted_templates/yacht/Template/template.json
```

In templates you are able to define variables (starting with `!`) to have them automatically replaced by whatever variable the user has set in their server settings (ie. `!config` will be replaced by `/yacht/AppData/Config` by default).


[def]: https://raw.githubusercontent.com/SelfhostedPro/Yacht/master/readme_media/Yacht_logo_1_dark.png