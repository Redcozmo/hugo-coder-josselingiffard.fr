---
title: Syntaxe markdown
author: 'Josselin GIFFARD-CARLET'
date: '2023-10-19'
slug: syntaxe-markdown
draft: true
categories: []
tags: [markdown]
---

Le langage markdown est un langage de balisage léger créé en 2004 par John Gruber et Aaron Swartz : https://daringfireball.net/projects/markdown/

Cette syntaxe est reprise dans ce document : https://www.markdownguide.org/basic-syntax/

La compatibilité entre Hugo et Markdown est détaillée ici : https://www.markdownguide.org/tools/hugo/

## Titres

Les éléments titres HTML ont six niveaux de `<h1>` à `<h6>`. `<h1>` est le plus haut niveau et `<h6>` le plus bas.

Markdown | HTML
---|---
`# Titre h1` | `<h1>Titre h1<\h1>`

```
`# Titre h1` avec signe dièse
## Titre h2 avec signes dièses
#### Titre h4 avec signes dièses
##### Titre h5 avec signes dièses
###### Titre h6 avec signes dièses

Titre h1 avec signes égal
=======

Titre h2 avec tirets
-------
```

# Titre h1 avec signe dièse
## Titre h2 avec signes dièses
#### Titre h4 avec signes dièses
##### Titre h5 avec signes dièses
###### Titre h6 avec signes dièses

Titre h1 avec signes égal
=======

Titre h2 avec tirets
-------

## Paragraphes

Afin d'obtenir un retour à la ligne simple, noté `<br/>` en HTML, il est nécessaire de mettre deux espaces à la fin de la ligne et d'aller à la ligne. Cela créé ainsi deux paragraphes sans saut de ligne.

Afin de séparer deux paragraphes par un espacement, équivalent des balises `<p><\p>` en HTML, il est nécessaire de laisser une ligne vide.

## Emphases

Markdown | HTML | Rendu
---|---|---
`**en gras**` ou `__en gras__` | `<strong>en gras<\strong>` | **en gras**
`*en italique*` ou `_en italique_` | `<em>en italique<\em>` | _en italique_
`***en gras et en italique***` ou `___en gras et en italique___` | `<strong><em>en italique<\em><\strong>` | ***en gras et en italique***

## Liens

Un lien est noté `[nom](url)`.

Markdown | HTML | Rendu
---|---|---
`[nom](url)` | `<a href="url">nom</a>` | [nom](url)

## Images

Une image est noté `![image](image.png "icon")`.
Markdown | HTML
---|---
`![image](image.png "icon")` | `<img alt="Image" title="icon" src="image.png" />`

## Citations

```
> La géomatique est étroitement liée à l'information géographique, qui est la représentation d'un objet ou d'un phénomène localisé dans l'espace.
>
> Le domaine de la géomatique* englobe les SIG et les dépasse.
```

> La géomatique est étroitement liée à l'information géographique, qui est la représentation d'un objet ou d'un phénomène localisé dans l'espace.
>
> Le domaine de la géomatique* englobe les SIG et les dépasse.

## Tables

```
| Titre 1           |       Titre 2      |       Titre 3     |
| :---------------- | :----------------: | ----------------: |
| Colonne alignée à | Colonne alignée au | Colonne alignée à |
| Gauche            |       Centre       |            Droite |
```

| Titre 1           |       Titre 2      |       Titre 3     |
| :---------------- | :----------------: | ----------------: |
| Colonne alignée à | Colonne alignée au | Colonne alignée à |
| Gauche            |       Centre       |            Droite |

## Filet

Une ligne horizontale peut être insérée avec trois `*`.
Markdown | HTML
---|---
`***` | ``<hr/>``

## Code

Du `code` en ligne est entouré de guillemets arrière ou "backticks" obtenus avec par la combinaison des touches `Alt Gr` + `7` et notés `` ` ``.

Markdown | HTML
---|---
`` `code` `` | `<code>code</code>`

### Blocs de code avec 3 guillemets arrière ou "backticks"

Le bloc de code est entouré entre `` ```html `` et `` ``` ``

```html
<!DOCTYPE html>
<html lang="fr">
    <head>
        <meta charset="utf-8" />
    </head>
</html>
```


### Bloc de code indenté avec quatre espaces

    <!DOCTYPE html>
    <html lang="fr">
        <head>
            <meta charset="utf-8" />
        </head>
    </html>

### Bloc de code avec coloration syntaxique des shortcodes Hugo

```
{{< highlight html >}}

<!DOCTYPE html>
<html lang="fr">
    <head>
        <meta charset="utf-8" />
    </head>
</html>

{{< /highlight >}}
```

Ce qui donne :

{{< highlight html >}}

<!DOCTYPE html>
<html lang="fr">
    <head>
        <meta charset="utf-8" />
    </head>
</html>

{{< /highlight >}}

### Bloc de code avec coloration syntaxique adaptée en fonction du langage

Bloc de code en PYTHON

```python
# Bloc de code en PYTHON
x = 2
```
Bloc de code en JSON

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Bloc de code en r

```r
# Bloc de code en r
library(lidR) # comments
file.exists("leaflet.R")
```

## Types de listes

#### Liste ordonnée

En markdown :
```
1. Kaki
2. Anonne
3. Corossol
```

En HTML :

```html
<ol>
  <li>Kaki</li>
  <li>Anonne</li>
  <li>Corossol</li>
</ol>
```

Ce qui donne :

1. Kaki
2. Anonne
3. Corossol

#### Liste non ordonnée

En markdown :

```
- Huit
- Trois
- Sept
```

En HTML :

```html
<ul>
  <li>Huit</li>
  <li>Trois</li>
  <li>Sept</li>
</ul>
```

Ce qui donne :

- Huit
- Trois
- Sept

#### Listes imbriquées

En markdown :

```
- Fruit
    1. Kaki
    2. Anonne
    3. Corossol
- Légume
    1. Topinambour
    2. Rutabaga
```

En HTML :

```html
<ul>
  <li>Fruit<ol>
      <li>Kaki</li>
      <li>Anonne</li>
      <li>Corossol</li>
  </ol></li>
  <li>Légume<ol>
      <li>carotte</li>
      <li>brocoli</li>
  </ol></li>
</ul>
```

ou :

```html
<ul>
  <li>Fruit</li>
    <ol>
      <li>Kaki</li>
      <li>Anonne</li>
      <li>Corossol</li>
    </ol>
  <li>Légume</li>
    <ol>
      <li>carotte</li>
      <li>brocoli</li>
    </ol>
</ul>
```

Ce qui donne :

- Fruit
    1. Kaki
    2. Anonne
    3. Corossol
- Légume
    1. Topinambour
    2. Rutabaga

## Commentaires

La syntaxe HTML est utilisée.

```
<!--ceci est un commentaire-->
```

## Note de bas de page

Le topinambour[^1] est un légume ancien[^2] au même titre que le rutabaga[^3].

***
[^1]: Le [topinambour](https://fr.wikipedia.org/wiki/Topinambour) (bot. Helianthus tuberosus L., 1753), aussi appelé artichaut de Jérusalem, truffe du Canada ou soleil vivace

[^2]: Note de bas de page.

[^3]: Une autre note de bas de page.
