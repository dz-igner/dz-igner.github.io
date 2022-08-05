---
layout: post
title: "Secure Self Hosted with Authentik | Traefik & NGINX Proxy Manager"
date: 2022-08-05 10:08 +0200
category: self-hosted
author: 
tags: [docker]
summary: 
---

![Darth Vaper](https://camo.githubusercontent.com/4745974518b69f22b6297c1fc33a7faac798f04bed3b1d582e9f7a82b70727ce/68747470733a2f2f676f61757468656e74696b2e696f2f696d672f69636f6e5f746f705f6272616e645f636f6c6f75722e737667){: width="200" height="200" }{: .left }{: .shadow }

## What is authentik?

authentik is an open-source Identity Provider focused on flexibility and versatility. You can use authentik in an existing environment to add support for new protocols, implement sign-up/recovery/etc. in your application so you don't have to deal with it, and many other things.

## docker-compose installation

This installation method is for test-setups and small-scale productive setups.

### Requirements

* A Linux host with at least 2 CPU cores and 2 GB of RAM.
* docker
* docker-compose

### Preparation

Download the latest docker-compose.yml from here. Place it in a directory of your choice.

If this is a fresh authentik install run the following commands to generate a password:

```bash
# You can also use openssl instead: `openssl rand -base64 36`
sudo apt-get install -y pwgen
# Because of a PostgreSQL limitation, only passwords up to 99 chars are supported
# See https://www.postgresql.org/message-id/09512C4F-8CB9-4021-B455-EF4C4F0D55A0@amazon.com
echo "PG_PASS=$(pwgen -s 40 1)" >> .env
echo "AUTHENTIK_SECRET_KEY=$(pwgen -s 50 1)" >> .env
# Skip if you don't want to enable error reporting
echo "AUTHENTIK_ERROR_REPORTING__ENABLED=true" >> .env
```