---
title: "R markdown test notice"
author: "Josselin GIFFARD-CARLET"
date: "2023-02-10"
output:
  html_document: default
  pdf_document: default
  word_document: default
slug: "rmarkdown-test-notice"
draft: yes
categories: R
tags:
- lidar
- osm
- opendata
summary: ''
editor_options:
  markdown:
    wrap: 72
  chunk_output_type: inline
---
<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/leaflet/leaflet.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/leaflet/leaflet.js"></script>
<link href="{{< blogdown/postref >}}index_files/leafletfix/leafletfix.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/proj4/proj4.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/Proj4Leaflet/proj4leaflet.js"></script>
<link href="{{< blogdown/postref >}}index_files/rstudio_leaflet/rstudio_leaflet.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/leaflet-binding/leaflet.js"></script>



# R Markdown

{{< notice warning >}}
Test shortcode notice
{{< /notice >}}

# Introduction {#introduction}

Le programme de couverture nationale en [LiDAR
HD](https://geoservices.ign.fr/lidarhd) de l'IGN est en cours et prévu
sur une diurée de 5 ans. Les données diffusées sont des nuages de points
en 3 dimensions bruts ou classifiés. Plus tard nous auront à disposition
sur la France entière des produits dérivés comme le MNT (modèles
numériques de terrain), le MNS (modèles numériques de surface) et le MNH
(modèles numériques de hauteur). En attendant ces produits IGN, nous
allons voir comment utiliser ces nuages de points avec un package R
nommé lidR.

# Objectifs {#objectifs}

{{< notice warning >}}
Sous Ubuntu des dépendances sont à installer au préalable comme indiqué
sur le dépot GitHub [dépot GitHub
lidR](https://github.com/r-lidar/lidR#install-lidr-dependencies-on-gnulinux)
{{< /notice >}}



```r
library(sf) # for spatial vector data manipulation
library(dplyr)
library(tmap) # for visualisation
library(maptiles)
library(leaflet) # for interactive map plot
library(widgetframe)
```







```r
query <- "Fontaines-Saint-Martin"
boundary_dir <- "metropole-de-lyon"
boundary_file <- "adr_voie_lieu_adrcomgl.shp"
boundary_filepath <- paste(data_dir, boundary_dir, boundary_file, sep = "/")
file_layer <- "adr_voie_lieu_adrcomgl"
fsm <- st_read(dsn = boundary_filepath,
               layer = file_layer,
               quiet = TRUE) %>%
  filter(nom == query)
fsm
## Simple feature collection with 1 feature and 7 fields
## Geometry type: POLYGON
## Dimension:     XY
## Bounding box:  xmin: 4.83728 ymin: 45.83288 xmax: 4.866836 ymax: 45.85619
## Geodetic CRS:  RGF93
##                      nom      nomreduit insee trigramme    datemaj surface_km
## 1 Fontaines-Saint-Martin Fontaines-St-M 69087       FSM 2007-02-12       2.73
##   gid                       geometry
## 1 137 POLYGON ((4.863678 45.84272...
```










