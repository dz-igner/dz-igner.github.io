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

```bash
apt install zsh
```

```bash
chsh -s /usr/bin/zsh root
```

```bash
echo $SHELL
```

```bash
apt install wget git
```

```bash
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Set in ~/.zshrc
1. Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc
2. plugins=(aliases alias-finder docker extract git history sudo web-search zsh-autosuggestions zsh-syntax-highlighting z)

```bash
p10k configure
```

```bash
exec zsh
```
