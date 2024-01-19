---
title: "test-notice-with-leaflet-or-tmap"
author: ''
date: "2024-01-17"
slug: []
categories: []
tags: []
authors: []
description: ''
externalLink: ''
series: []
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

``` r
library(sf)
library(dplyr)
library(tmap)
library(leaflet)
library(widgetframe)
```

# A notice from theme hugo-coder

{{< notice warning >}} Test shortcode notice {{< /notice >}}

{{< notice warning >}}
Test shortcode notice
{{< /notice >}}

# Shortcode hugo vimeo

{{< vimeo 55073825 >}}

{{< vimeo 55073825 >}}

# Leaflet…

``` r
leaflet() %>%
  addTiles()
```

<div class="leaflet html-widget html-fill-item" id="htmlwidget-1" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"https://openstreetmap.org/copyright/\">OpenStreetMap<\/a>,  <a href=\"https://opendatacommons.org/licenses/odbl/\">ODbL<\/a>"}]}]},"evals":[],"jsHooks":[]}</script>

``` r
tmap_mode("view")
tm <- 
  tm_basemap(c(OpenStreetMap = "OpenStreetMap",
               GeoportailFrance.orthos = "GeoportailFrance.orthos",
               OpenTopoMap = "OpenTopoMap"));tm
```

``` r
tmap_mode("view")
tm_basemap()
```

``` r
tmap_mode("plot")
tm_basemap()
```

<img src="{{< blogdown/postref >}}index_files/figure-html/tmap3-1.png" width="672" />
