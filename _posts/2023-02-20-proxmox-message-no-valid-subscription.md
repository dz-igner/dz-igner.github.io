---
layout: post
title: "Proxmox: remove message No valid subscription"
date: 2023-02-20 14:44:00 +0200
category: 
author: 
tags: []
summary: 
---

## How to remove Proxmox message "no valid subscription"

Die Proxmox Meldung `No valid Subscription` ist zwar ganz Nett und eigentlich auch Richtig, aber sind wir mal ehrlich, diese kann auch sehr nervig sein, wenn man sich häufig in das System einloggt.

Also entfernen wir einfach diese Meldung und haben bei jedem Login unsere Ruhe.

Hinweis: Nach einem Update des Pakets `proxmox-widget-toolkit` wird diese Meldung wieder erscheinen und uns wieder nerven. Dann einfach den nachfolgenden Befehl wieder eingeben.

```bash
sed -Ezi.bak "s/(Ext.Msg.show\(\{\s+title: gettext\('No valid sub)/void\(\{ \/\/\1/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js && systemctl restart pveproxy.service
```
