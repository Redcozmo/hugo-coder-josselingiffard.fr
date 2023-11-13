---
title: Trouver des Fichiers avec `find`
author: Josselin GIFFARD-CARLET
date: 2023-07-18
slug: commande-linux-find
categories: [dev]
tags: [linux, terminal]
---

La commande `find` en Linux est un outil puissant pour rechercher des fichiers et des répertoires dans le système de fichiers. Son utilisation de base est simple :

```bash
find /chemin/du/repertoire -name "nom_du_fichier"
```

Cela recherche le fichier spécifié dans le répertoire indiqué. Par exemple, pour trouver tous les fichiers texte dans le dossier "Documents":

```bash
find ~/Documents -name "*.txt"
```
