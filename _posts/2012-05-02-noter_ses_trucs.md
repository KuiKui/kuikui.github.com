---
layout: post
title: Noter ses trucs
---

# {{ page.title }} #

<span class="date post">{{ page.date | date: "%d/%m/%Y" }}</span>

Avec la [Team-Fusion](http://team-fusion.pmsipilot.com/), nous utilisions [Campfire](http://campfirenow.com/) de manière presque abusive. Je dirais même que c'était notre outil de travail principal. Grâce à ce chat online et [ouvert](http://developer.37signals.com/campfire/), nous pouvions :

* discuter,
* être informés de l'état de nos tests d'intégration continue,
* recevoir les notifications de nos revues de code,
* échanger des liens et des fichiers,
* utiliser notre [robot](http://team-fusion.pmsipilot.com/572/installation-hubot-et-creation-scripts/) pour [détendre](http://team-fusion.pmsipilot.com/600/hubot-cest-beau/) l'atmosphère. 

Et tout ça de manière _intuive_ (bye bye Jabber).

## Le problème

Certaines petites informations importantes passaient régulièrement par Campfire :

* les liens,
* les commandes à exécuter,
* les titres de livres,
* les bonnes phrases,
* etc.

Or, il était assez difficile de les retrouver par la suite.

![stickdown](http://img213.imageshack.us/img213/2473/stickdownstart.png)

## La solution

Avec [Mickaël](https://twitter.com/spocky12), nous avons donc développé [Stickdown.me](http://stickdown.me/), une application web sans inscription qui permet à tout le monde de lister et d'ordonner ce genre d'informations. 

Toutes les informations saisies sont publiques et stockées dans un espace que vous nommez librement. Ainsi, vous pouvez partager l'url de votre espace avec qui vous voulez et, si vous choisissez bien le nom de vos espaces, il est fort probable que personne d'autre ne viendra les polluer.

A contrario, il est aussi possible de créer des listes collaboratives en utilisant des noms courts et simples.

## L'utilisation

* allez sur [http://stickdown.me](http://stickdown.me/) puis saisisez un nom de _board_,
* ajoutez vos _stuffs_ les uns après les autres,
* ordonnez vos _stuffs_ en les glissant/déposant (ancre en début de ligne),
* mettez vos _stuffs_ importants en avant en cliquant sur l'étoile,
* mettez vos _stuffs_ en retrait en les cochant,
* éditez vos _stuffs_ en cliquant sur leur contenu,
* supprimez vos _stuffs_ en cliquant sur la poubelle.

Libre à vous d'utiliser ce service comme bon vous semble. Personnellement, j'ai plusieurs listes dont une pour me souvenir des articles à écrire : [http://stickdown.me/kuikui-to-write](http://stickdown.me/kuikui-to-write)

## L'évolution

Nous avons développé ce service pour [nos propres besoins](http://gettingreal.37signals.com/ch02_Whats_Your_Problem.php). Il est donc possible qu'il ne réponde pas complètement aux votres, mais n'hésitez pas à nous [contacter](https://twitter.com/dondouny) pour nous proposer des évolutions ou nous remonter des bugs (c'est une version _alpha_ dirons-nous).

Prochainement, nous allons :

* exposer le service avec une API REST,
* améliorer le design pour le rendre _responsive_,
* prévisualiser les images et les vidéos au survol des liens.

Au fait, il est fortement probable que [Stickdown.me](http://stickdown.me/) ne fonctionne que sur les navigateurs récents :-)
