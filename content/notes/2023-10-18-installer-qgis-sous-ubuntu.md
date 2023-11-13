---
title: Installer QGis sous ubuntu
author: Josselin GIFFARD-CARLET
date: '2023-10-18'
slug: installer-qgis-sous-ubuntu
draft: true
categories:
  - linux
tags: []
---

# Installation de QGis

https://www.qgis.org/fr/site/forusers/alldownloads.html#debian-ubuntu

ou / et

https://geotribu.fr/articles/2023/2023-01-05_installer-qgis-sur-ubuntu/

```bash
sudo apt install gnupg software-properties-common
sudo wget -O /etc/apt/keyrings/qgis-archive-keyring.gpg https://download.qgis.org/downloads/qgis-archive-keyring.gpg
```
Créer le fichier qgis.sources 

`sudo touch /etc/apt/sources.list.d/qgis.sources`

et y ajouter le dépôt qgis voulu :

```
Types: deb deb-src
URIs: https://qgis.org/ubuntu-ltr
Suites: jammy
Architectures: amd64
Components: main
Signed-By: /etc/apt/keyrings/qgis-archive-keyring.gpg
```
Details : to know distribution codename (suites) : 
`lsb_release -cs`

## Installer QGis
```
sudo apt update
sudo apt install qgis qgis-plugin-grass
```

## Installer LAStools plugins in QGis

- pluginq --> manage and install plugins
- rechercher et installer LAStools
- télécharger les fichiers sources de LAStools ici : https://rapidlasso.de/customer-support/
- dézipper l'archive dans `~/.local/share/QGIS/QGIS3/profiles/default/LAStools/`
- installer wine (https://doc.ubuntu-fr.org/wine) car LAStools est un exécutable (?) windows : `sudo apt install wine64`
- dans QGis : settings --> options --> providers --> LAStools :
-   dans LAStools folder : `/home/<your-username>/.local/share/QGIS/QGIS3/profiles/default/LAStools`
-   dans Wine folder : `/usr/bin`