---
title: Comment j'ai créé ce site / blog / portfolio ?
author: Josselin GIFFARD-CARLET
date: '2023-10-18'
slug: comment-jai-cree-ce-site-blog-portfolio
draft: true
categories:
  - non-scientifique
tags:
  - R
  - Rstudio
  - Hugo
  - Git
  - Dev
  - Web
---

# 0. Bases

Rstudio, Git, Hugo, Netlify

# 1. Création sur Rstudio et blogdown

https://bookdown.org/yihui/blogdown/a-quick-example.html
1.2 --> 1.2.3 and pass to git
on choisit le theme

# 2. Git

Git init --> add --> remote --> push

## Initialisation
https://github.com/git-guides/git-init

## Add
https://github.com/git-guides/git-add

## Commit
git commit -m "message"

## Dépot distant sur github
creation du depot distant sur github
connexion entre le depot local et distant:
git remote add origin https://github.com/Redcozmo/un-brin-de-geomatique.git
git branch -M main
git push -u origin main

et hopla pour github

# 3. Netlify
vers Netlify : sur l'accueil, add new site --> import an existing project --> deploy with github

pas besoin de faire build_site ! Netlify s'en charge
https://bookdown.org/yihui/blogdown/a-quick-deploy.html

# 4. La suite
add readme
changer template / theme
ajout article
changer le nom de domaine ?
comment savoir si mon site est visité ?

# 5. Alternative

D'apres le tres bon site https://nicolasfriedli.ch/hugo/configuration/, il dit que "l’apprentissage des logiques d’Hugo est meilleur si un thème n’est pas activé dès le début" ce qui est plutot jsute. Surtout qu'apres avoir commencé avec Rstudio / Blogdown / et un theme, j'arrive a une erreur que je n'arrive pas a résoudre : rstudio renvoie une erreur que j ene parvient pas é resoudre et il y a certaines fonctionnalité que je n'arive pas a mettre ne place.

hugo new site myblog
cd myblog
hugo new theme notheme --> pour avoir l'architecture de base dasn layouts notamment
hugo new content ...
hugo serve

ajout de rubrique dans hugo.toml :
[[menus.main]]

# Les problématiques rencontrées

## coloration syntaxique et affichage des images

A un moment j'ai voulu tester un autre theme (hugo-coder) mais j'ai rencontré un problème avec la coloration syntaxique des blocs de code et en même temps avec l'affichage des images.
Avec le fichier Rprofile deux comportements rencontrés :
 - le paramètre blogdown.method = 'markdown' : coloration syntaxique OK et affichage d'images NOK
 - le paramètre blogdown.method = 'html' : coloration syntaxique NOK et affichage d'images OK

| blogdown.method | [markup.goldmark.renderer] | coloration syntaxique | affichage d'images |
| :-------------- | -------------------------- | --------------------- | ------------------ |
| markdown        | unsafe = true              | OK                    | OK                 |
| html            | unsafe = true              | NOK                   | OK                 |
| markdown        | unsafe = false             | OK                    | NOK                |
| html            | unsafe = false             | NOK                   | OK                 |


 Après recherchessur le web j'ai trouvé la réponse ici :
 https://discourse.gohugo.io/t/raw-html-getting-omitted-in-0-60-0/22032

La solution est de mettre dans le fichier de config :
```
[markup.goldmark.renderer]
unsafe = true
```

# 6. Démarrage de 0

## besoins
- un site avec des articles : type blog
- des articles plutot dev et géomatique : donc bcp de bloc de code (coloration syntaxique)
- des articles fait à partir de Rmd pour une question de simplicité : blogdown (ou hugodown a tester) pas possible de faire uniquement avec hugo. Sauf https://www.eamoncaddigan.net/posts/rmarkdown-hugo/
- un site pour s'entrainer, pour expérimenter, et partager
- un site avec des notes rapdies (petits articles) : posts et notes
- site simple avec pages a minima : accueil, articles, notes, cv, a propros,


# 5. Remerciements / Citation / Crédits :

Xie, Yihui. 2016. Bookdown: Authoring Books and Technical Documents with R Markdown. Boca Raton, Florida: Chapman; Hall/CRC. https://github.com/rstudio/bookdown.

Git / github
R / Rstudio
Hugo
