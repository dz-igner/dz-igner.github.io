---
layout: post
title: "Proxmox VE mit Fail2ban absichern gegen Loginversuche"
date: 2023-02-20 14:51
category: 
author: 
tags: []
summary: 
---

## Proxmox VE mit Fail2ban absichern gegen Loginversuche

![Darth Vaper](https://nextcloud.newsxc.net/s/MmYmFEMqTWDycDt/download/firewall.png){: width="150" height="150" }{: .left }

Wer einen Proxmox VE Host im Internet betreibt und die Login-Oberfläche so für alle offen hat, sollte sich vor fehlerhaften “Login Versuchen” schützen. Doch Fail2ban muss erstmal lernen wie ein fehlerhafter Loginversuch bei Proxmox aussieht. Dafür erstellen wir bei der Einrichtung eine kleine Konfigurationsdatei die dabei fail2ban unterstützt.

Wer noch kein fail2ban auf dem Proxmox Host installiert hat, der sollte dies nun tun mit folgendem Befehl.

```bash
apt install fail2ban
```

Als nächstes aktivieren / erstellen wir die Funktion damit fail2ban “Proxmox” als Aufgabe akzeptiert.
Dafür fügen wir in der Datei `/etc/fail2ban/filter.d/proxmox.conf` ein paar Zeilen hinzu.

Wer es genau wissen möchte. In dieser Konfiguration wird rückwirkend 6 Stunden in die Vergangenheit geschaut und bei 3 Fehlversuchen für wird 6 Stunden gesperrt. Diese Werte könnt Ihr natürlich auf eure Anforderung anpassen.

```bash
nano /etc/fail2ban/filter.d/proxmox.conf
```

```bash
[proxmox]
enabled = true
port = https,http,8006
filter = proxmox
logpath = /var/log/daemon.log
maxretry = 3
# 6 ban time
bantime = 21600
# 6 Stunden Rückwärts
findtime = 21600
```

Jetzt müssen wir Fail2Ban noch beibringen wie man fehlerhafte Logins erkennt. Sowas macht sich in der Regel bemerkbar mit Einträgen in eine Logdatei. Wir lesen also die Datei aus und werten die dort enthaltenen Informationen aus.

Wir legen eine neue Datei an mit folgenden Pfad. `/etc/fail2ban/jail.local`

```bash
nano /etc/fail2ban/jail.local
```

```bash
[Definition]
failregex = pvedaemon\[.*authentication failure; rhost=<HOST> user=.* msg=.*
ignoreregex =
```

Abschließend einmal Fail2ban neu starten.

```bash
systemctl restart fail2ban
```
