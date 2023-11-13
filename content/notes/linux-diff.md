---
title: Comparer des Fichiers avec `diff`
author: Josselin GIFFARD-CARLET
date: 2023-07-18
slug: commande-linux-diff
categories: [dev]
tags: [linux, terminal]
---

La commande `diff` compare le contenu de deux fichiers. Son utilisation de base est la suivante :

```bash
diff fichier1.txt fichier2.txt
```

Par exemple, pour comparer deux scripts shell :

```bash
diff script_v1.sh script_v2.sh
```

Cela affichera les différences entre les deux fichiers, soulignant les lignes modifiées.
