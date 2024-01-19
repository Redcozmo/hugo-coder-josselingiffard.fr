---
title: Régler un problème de git diff après déplacement d'un dépôt git local
author: Josselin GIFFARD-CARLET
date: 2023-11-21
slug: probleme-git-diff-apres-deplacement-depot-git-local
categories: [dev]
tags: [linux, terminal, git]
---

Apres avoir déplacé mon dépot local d'un ordi à l'autre via un disque dur externe formaté en exFAT, tous mes fichiers du depot git apparraissent d'un coup comme modifiés dans le `working directory`. Le résultat de la commande `git diff .` est le suivant :

```bash
old mode 100644
new mode 100755
```

En fait effectuant la copie, le propriétaire et les droits d'accès sur l'ensemble des fichiers ont été modifiés. Les permissions des fichiers en `old mode` correspondent aux permissions unix `644=rw-r--r--` ont été changés en `new mode` correspondant aux permissions unix `755=rwxr-xr-x`. Les nouvelles permissions inclues le droit d'exécution `+x`

{{< notice tip >}}
Il faut rétablir les droits d'accès initiaux à tous les fichiers.
{{< /notice >}}

Dans un premier temps enlever le droit d'exécution avec la commande :

```bash
sudo chmod -R -x .
```

Cela résoud le problème du `gitt diff` mais il faut remettre le droit d'exécution au répertoires afin de pouvoir notamment lister le contenu d'un répertoire avec `ls` :

```bash
sudo chmod -R +X .
```

Par contre les fichier `.sh` a qui on a enlevé le droit d'exécution ne pourront plus s'exécuter. Il faut donc leur rendre aussi ce droit. Dans un premier temps s'assurer qu'on a bien des fichiers `.sh` dans le répertoire :

```bash
find . -name "*.sh"
```

Puis leur remettre ce droit d'exécution :

```bash
`chmod +x ./fichier.sh`
```

La réponse a été trouvée sur [stackoverflow](https://stackoverflow.com/questions/1257592/how-do-i-remove-files-saying-old-mode-100755-new-mode-100644-from-unstaged-cha).
