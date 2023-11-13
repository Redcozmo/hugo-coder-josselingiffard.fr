---
title: "Exploration des Données OSM pour la Cartographie Humanitaire"
author: 'Josselin GIFFARD-CARLET'
date: '2023-08-19'
slug: osm-cartographie-humanitaire
draft: true
categories: [données]
tags: [osm]
---

***Article test rédigé par chatGPT***

*Les données OpenStreetMap (OSM) sont une ressource précieuse pour la cartographie humanitaire, offrant des informations détaillées sur les infrastructures, les routes et les zones géographiques. Dans cet article, nous explorerons comment utiliser ces données pour créer des cartes utiles dans des contextes humanitaires.*

## Introduction aux Données OpenStreetMap (OSM)

[OpenStreetMap (OSM)](https://www.openstreetmap.org) est une plateforme collaborative de cartographie où des contributeurs du monde entier ajoutent et mettent à jour des informations géographiques. Ces données libres de droits et accessibles sont utilisées dans divers domaines, notamment la cartographie humanitaire.

## Accès aux Données OSM

Pour accéder aux données OSM, vous pouvez utiliser des API telles que [Overpass API](https://overpass-turbo.eu/), qui permettent de récupérer des données spécifiques à une région ou à un thème.

```R
# Exemple de requête Overpass API pour obtenir les écoles dans une région
library(osmdata)

# Coordonnées d'une région (à remplacer par la région d'intérêt)
bbox <- c(left = -1.5, bottom = 52, right = 0, top = 53)

# Requête pour obtenir les écoles
school_query <- opq(bbox) %>% add_osm_feature(key = "amenity", value = "school") %>% osmdata_sf()

# Affichage des données
head(school_query$osm_points)
```

# Création de Cartes Interactives avec Leaflet

Leaflet est une bibliothèque JavaScript populaire pour la création de cartes interactives. Intégrons une carte Leaflet dans R pour visualiser les écoles extraites des données OSM.

```R
# Installation des bibliothèques nécessaires
install.packages(c("leaflet", "sf"))

# Chargement des bibliothèques
library(leaflet)
library(sf)

# Création de la carte Leaflet
map <- leaflet() %>%
  addTiles() %>%
  addMarkers(data = school_query$osm_points, ~geometry$coordinates[1], ~geometry$coordinates[2], popup = ~tags)

# Affichage de la carte
map
```

# Applications Humanitaires

La cartographie humanitaire avec les données OSM a des applications variées, de la planification d'interventions d'urgence à la gestion des ressources dans des régions en développement. Les informations détaillées sur les écoles, les hôpitaux et les routes peuvent considérablement améliorer la préparation et la réponse aux crises.
Ressources Additionnelles

Pour en savoir plus sur la cartographie humanitaire avec les données OSM, consultez les ressources suivantes :

1. [HOT - Humanitarian OpenStreetMap Team](https://www.hotosm.org/)
2. [OSM Tasking Manager](https://tasks.hotosm.org/)
3. [OpenStreetMap Wiki - Humanitarian OSM Tags](https://wiki.openstreetmap.org/wiki/Humanitarian_OSM_Tags)


Explorez ces ressources pour vous impliquer dans des projets de cartographie humanitaire et utiliser les données OSM de manière significative.

Note : N'oubliez pas de respecter les politiques de licence et d'utilisation des données OpenStreetMap.
