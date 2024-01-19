---
title: Arrêter un processus qui a planté
author: Josselin GIFFARD-CARLET
date: 2023-07-18
slug: linux-kill-processus
categories: [dev]
tags: [linux, terminal]
---

{{< notice info >}}
Comment arrêter un processus ?

```bash
killall -9 nom_du_processus
```
{{< /notice >}}

Je ne sais pas si c'est mon ordinateur qui n'est pas assez puissant, mais il m'arrive fréquemment que `Rstudio` plante et fige sans même me laisser la possibilité de le fermer avec la croix de la fenêtre. C'est embettant de devoir redémarrer l'ordinateur et je ne peux pas faire `Ctrl+Alt+Suppr` comme sur Windows, donc que faire quand on est sur Linux ?

La dernière fois que j'ai rencontré le problème, je ne me souvenanais plus la démarche et les commandes à utiliser et donc après une recherche rapide j'ai trouvé cet article qui donne une solution :

https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-kill-a-process-from-the-command-line

## Commandes utilisées

Les commandes linux nécessaires sont
- `ps` ou `top` pour visualiser les processus actifs
- `grep` : pour rechercher dans les résultats de `ps` ou `top` celui qui nous concerne
- `kill` : pour arrêter un processus
- et le `|` ou "pipe" qui permet de chainer plusieurs commande, c'est-à-dire de passer le résultat d'une commande shell à une autre commande shell

## Identifier le processus

Dans notre cas, c'est Rstudio qui plante donc on veut des informations sur ce processus. La commande `ps` ou `top` chainée avec la commande `grep` via le pipe nous permet ceci :

```bash
top | grep rstudio
```
ou<br />
```bash
ps aux | grep rstudio
```

Personnellement j'ai bien utiliser la commande ps avec l'option `-u` pour sélectionner les processus qui m'appartiennent et sans les options aux pour simplifier le résultat :

```bash
ps -u `whoami` | grep rstudio
```

Ce qui donne deux processus dans mon cas :

![result of ps -u command](images/ps-u.png)

## Arrêter le processus

D'après le manuel `man kill` la commande `kill` ("send a signal to a process") demande deux paramètres, une inforamtion sur le signal à envoyer et sur le processus.

```bash
kill -SIGNAL PID
```

`SIGNAL = 9` permet de "tuer" le processus.

Souvent pour un même programme, il y a plusieurs processus actifs, donc pour arrêter le programme il faut arrêter tous les processus correspondants. Dans mon cas, il faut exécuter la commande suivante :

```bash
kill -9 86465 86464
```

Une solution plus simple est d'utiliser la commade `killall` qui permet de tuer un processus par son nom :

```bash
killall -9 rstudio
```
