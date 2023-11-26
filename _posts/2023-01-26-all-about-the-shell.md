---
layout: post
title: "All about the *NIX Shell"
date: 2023-01-26 07:51
category: 
author: 
tags: []
summary: 
---

Die Unix-Shell oder kurz Shell bezeichnet die traditionelle Benutzerschnittstelle unter Unix oder unixoiden Computer-Betriebssystemen. Der Benutzer kann in einer Eingabezeile Kommandos eintippen, die der Computer dann sogleich ausführt. Man spricht darum auch von einem Kommandozeileninterpreter.

Es gibt verschiedene Shells um Kommandos über die Benutzerschnittstelle auszuführen. Eine der bekannteren Shells ist die sogenannte ´BASH´ (Bourne Again Shell). Die Z Shell (´zsh´) erfreut sich ebenfalls großer Beliebtheit.

Mit den folgenden Schritten installieren wir die Z Shell, erweitern die um ein Framework (oh-my-zsh), fügen nützliche Plugins hinzu und optimieren das Aussehen der Shell mit einem sogenannten Theme.

### Installation von zsh

```bash
apt install zsh
```

### Setzen der Default Shell für den User root

```bash
chsh -s /usr/bin/zsh root
```

### Abfrage der aktuellen Shell

```bash
echo $SHELL
```

### Installation von git und wget (für die weiteren Schritte benötigt)

```bash
apt install wget git
```

### Installation des Frameworks oh-my-zsh

**```bash
sh -c "$(wget <https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh> -O -)"

```**

### Installation des Plugins zsh-autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

### Installation des Plugins zsh-syntax-highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### Installation des Themes p10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Set in ~/.zshrc

1. Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc
2. plugins=(aliases alias-finder docker extract git history sudo web-search zsh-autosuggestions zsh-syntax-highlighting z)

### Konfiguration des Aussehens der Shell

```bash
p10k configure
```

```bash
exec zsh
```
