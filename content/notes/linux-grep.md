---
title: Rechercher du Texte avec `grep`
author: Josselin GIFFARD-CARLET
date: 2023-07-22
slug: commande-linux-grep
categories: [dev]
tags: [linux, terminal]
---

La commande `grep` permet de rechercher des motifs dans les fichiers. Voici comment l'utiliser pour trouver toutes les occurrences d'un mot dans un fichier :

```bash
grep "motif" fichier.txt
```

Par exemple, pour trouver toutes les lignes contenant "erreur" dans un fichier de logs :

```bash
grep "erreur" logs.txt
```
