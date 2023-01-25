---
layout: post
title: "Proxmox VE Host Backup mit Borg"
date: 2022-08-04 21:45 +0200
category: self-hosted
author: 
tags: [proxmox]
summary: 
---

![Darth Vaper](https://borgbackup.readthedocs.io/en/stable/_static/logo.svg){: width="200" height="200" }{: .left }{: .shadow }

Das Proxmox Host Backup ist genauso wichtig, wie die Backups der virtuellen Maschinen. Wenn der Host ausfällt, sind nicht nur die Hüllen der virtuellen Maschinen weg, sondern auch alle Einstellungen der Proxmox Umgebung.

Eventuell wurden spezielle Einstellungen vorgenommen, spezielle Backup oder HA Regeln. Alle diese Regeln sind nun weg. Also müssen wir uns bemühen, dass auch diese Einstellungen schnell und einfach gesichert werden.

## Proxmox VE Host Backup mit Borg Backup

Borg Backup ist eine kostenlose Software, welche für sehr viele Betriebssysteme verfügbar ist, unter anderem natürlich Linux. Mir persönlich gefallen die effizienten Funktionen, wie z.B. Deduplication & Compression sehr gut. Es spart besonders für das “lästige” Backup enorm viel Speicherplatz. Beide Funktionen in Kombination erreichen gerne mal schnell Werte von bis zu 9:1, je nachdem was Ihr so an Daten in euer Backup schiebt.

Kommen wir zum eigentlichen, was sollte ich von meinem Proxmox Host alles speichern?

* /etc/pve
* /etc/network
* /etc/hosts
* /etc/passwd
* Der Template Ordner wo eure Templates und ISOs liegen

Grundsätzlich reicht es wenn Ihr den Ordner /etc/pve speichert, denn dort liegen alle Konfigurationen für den Proxmox VE. Wenn Ihr noch zusätzlich weitere Informationen speichern möchte wie ich hier, braucht ihr diese Ordner nur mit in euer Backup aufnehmen. Aber wie das jetzt wirklich geht kommt im folgenden Abschnitt.

## Manuelles Borg Backup – Schritt für Schritt

Borg Backup benötigt für die gewisse Intelligenz sein eigenes Repository. Das heißt nichts anderes, dass Ihr das Backup einmalig auf einem Pfad eurer Wahl initiieren müsst.

Wo legt man das Backup hin? Natürlich auf einen entfernten Speicher wie z.B. ein NFS oder SMB/Cifs Share. Ein iSCSI Blockdevice eignet sich natürlich ebenfall. Ein USB-Stick tut es auch, aber dieser Steckt ja wieder im System selber, kann also genauso ausfallen oder betroffen sein.

```bash
#Damit wird das Borg Backupauf dem gewünschten Pfad initialisiert. (Es wird nach einem Passwort verlangt)
borg init --encryption=repokey /pfad/zum/backup_ordner
```
