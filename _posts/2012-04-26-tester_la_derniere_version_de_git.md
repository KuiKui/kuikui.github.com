---
layout: post
title: Tester la dernière version de Git
---

# {{ page.title }} #

<span class="date post">{{ page.date | date: "%d/%m/%Y" }}</span>

[Git](http://git-scm.com/) c'est bien.

Mais Git est en constante évolution. C'est pourquoi il peut être utile de tester les dernières évolutions qui pourraient potentiellement nous simplifier la vie.

Git ayant un miroir sur [GitHub](https://github.com/gitster/git) (sans gestion des PullRequests), il est facile de se brancher sur le master :

    $ cd /tmp
    $ git clone git://github.com/gitster/git.git

Ensuite il suffit de lancer quelques commandes pour générer le programme :

    $ cd /tmp/git
    $ autoreconf
    $ ./configure --prefix=/chemin/vers/nouveaugit
    $ make install

Afin de pouvoir utiliser cette version de Git nouvellement installée avec une autre commande que `git`, il est possible de créer un alias `gitdev` :

    $ vi ~/.bashrc

Ajouter la ligne `alias gitdev="/chemin/vers/nouveaugit/bin/git"` puis recharger le fichier pour pouvoir en profiter tout de suite :

    $ source ~/.bashrc
    
Si tout fonctionne bien, les numéros de version des deux commandes doivent être différents :

    $ git --version
    git version 1.7.4.1
    $ gitdev --version
    git version 1.7.10.334.gf9d99

Et voilà.
