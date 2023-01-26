---
layout: post
title: "Docker einrichten unter Linux, Windows, macOS"
date: 2022-07-03 16:25:00 +0200
category: self-hosted
author: 
tags: [docker]
summary: 
---

Um in die Welt von Docker einzusteigen, muss man die Container-Software erst einmal installieren. Die offizielle Docker-Dokumentation ist leider nicht unbedingt für Docker-Neulinge optimiert. Wir haben zusammengefasst, welche Versionen der Software es gibt, wo sie zu finden ist und wie Sie die aktuelle Ausgabe auf Ihrem System zum Laufen bringen.

## Community oder Desktop

Die Firma hinter Docker, die Docker Inc., hat zwei Versionen im Angebot: Die Community-Edition (docker-ce) ist Open-Source-Software. Sie bringt alle zum Betrieb von Containern nötigen Funktionen mit und kann auf Servern und auf Entwicklungs- und Testmaschinen unter Linux genutzt werden. Die Open-Source-Lizenz macht keine Einschränkungen, Sie dürfen die Software auch im Produktivbetrieb einsetzen.

Für Windows, macOS und Linux gibt es eine weitere Variante, ausgerichtet auf Entwickler: Docker Desktop. Gedacht ist sie ausdrücklich zum Entwickeln und Testen. Für viele Nutzer ist Docker Desktop kostenlos. Erst wenn Sie in einer Firma arbeiten, die mehr als 250 Mitarbeiter hat oder mehr als 10 Millionen US-Dollar im Jahr umsetzt, müssen Sie für den kommerziellen Einsatz auf Ihren Entwicklermaschinen einen Monats- oder Jahresplan (ab 5 US-Dollar im Monat) abschließen.

Docker Desktop laden Sie auf der Website von Docker herunter. Zur Installation gibt es nicht viel zu beschreiben, der Installer ist selbsterklärend. Unter Windows sollten Sie vorab das Windows Subsystem for Linux (WSL2) installieren und bei der Installation diese Option auswählen. Für Linux-Systeme stellt Docker fertige Pakete für Ubuntu, Debian, Fedora und Arch Linux bereit. Letzteres versieht Docker noch mit dem Status "experimentell". Für die Installation unter Linux brauchen Sie KVM-Virtualisierung, Qemu 5.2 oder neuer, systemd und eine KDE- oder Gnome-Desktopumgebung. Je nach Distribution müssen Sie eine Gnome-Erweiterung für das Docker-Menü nachrüsten.

In den folgenden Hinweisen geht es um die Installation der Community-Edition für Linux-Server und Linux-Desktops.

## Docker Engine unter Linux

Unter Linux gibt es neben Docker Desktop noch die reguläre Docker-Installation, die sich besser für den Serverbetrieb eignet. Die offiziellen Paketquellen der Distributionen sind meist kein geeigneter Anlaufpunkt für eine aktuelle Docker-Version. Docker entwickelt sich schneller weiter als die Zeitpläne der Distributionen es vorsehen.

Für Docker-Einsteiger gibt es ein bequemes Installations-Skript. Wer kein Problem damit hat, ein fremdes Skript auszuführen, kommt damit schnell zur laufenden Docker-Umgebung. Heruntergeladen wird es per Curl:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```

Um sicherzugehen, dass das Skript nicht manipuliert ist, können Sie den Inhalt mit einem Texteditor öffnen. Zum Abgleich können Sie das zugehörige GitHub-Repository heranziehen. Führen Sie anschließend das Skript mit Root-Rechten aus:

```bash
sudo sh get-docker.sh
```

Das Skript lädt Docker herunter und installiert es. Anschließend sollten Sie den aktuellen Benutzer zur Gruppe docker hinzufügen, damit Sie auch als normaler Benutzer auf den Docker-Daemon und die laufenden Container einwirken können.

```bash
sudo usermod -aG docker $USER
```

Damit die Änderung wirkt, müssen Sie sich einmal ab- und wieder anmelden. Anschließend ist Docker einsatzbereit.

Wer sich nicht auf ein Skript verlassen möchte, kann die Schritte auch per Hand durchführen – für Produktivsysteme ist das der empfohlene Weg. In der Docker-Dokumentation gibt es Anleitungen für CentOS, Debian, Fedora und Ubuntu.

## Docker-Compose

Für Container-Zusammenstellungen ist Docker-Compose das Mittel der Wahl. Mit diesem Programm können Sie Ihre Zusammenstellung als YAML-Datei speichern und mit dem Befehl docker compose up hochfahren. Lange Zeit war Docker-Compose eine parallel entwickelte Software neben Docker. Auf der Kommandozeile hat man es mit docker-compose (mit Bindestrich) aufgerufen. Seit 2021 hat Docker die Arbeit an einem großen Integrationsprojekt abgesschlossen und Compose als Subcommand in die Docker-CLI eingebaut (docker compose). Wenn Sie noch alte Anleitungen finden, können Sie den Bindestrich einfach weglassen, das neue Compose funktioniert nahezu identisch.

In Docker Desktop ist Compose bereits eingebaut und aktiviert. docker compose sollte also direkt funktionieren. Unter Linux müssen Sie es als Plugin installieren. Bis März 2022 musste man die Binärdatei direkt herunterladen und per Hand in das Verzeichnis für CLI-Erweiterungen kopieren. Auch Updates gab es nur mit Handarbeit.

Damit ist jetzt Schluss: Docker hat Docker-Compose V2 in seine Paketquellen für apt und rpm integriert, die man per Hand oder mit dem Installations-Skript eingerichtet hat. Auf Linux-Distributionen mit apt installiert man die Erweiterung etwa mit

```bash
apt install docker-compose-plugin
```

Auch das Updaten ist einfach – mit apt upgrade werden Docker und Docker-Compose auf den aktuellen Stand gebracht.

## Docker testen

Nach der Installation von Docker und Docker-Compose können Sie Programme schnell auf allen Betriebssystemen testen. Ob der Docker-Daemon läuft, verrät `docker version`.

```docker
docker version
```

Ob Docker-Compose läuft, verrät `docker compose version`.

```docker
docker compose version
```

## Docker unterwegs

Docker gibt es noch nicht für mobile Betriebssysteme wie iOS oder Android. Wer unterwegs mit Docker experimentieren oder testen möchte, kann sich den Webdienst `Play With Docker` ansehen. Dort kann man sich mit den Docker-Anmeldedaten einloggen und im Browser mit Containern hantieren.
