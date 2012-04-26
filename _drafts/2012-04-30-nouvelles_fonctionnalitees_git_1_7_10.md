
La nouvelle version [1.7.10](https://raw.github.com/gitster/git/master/Documentation/RelNotes/1.7.10.txt) de Git est sortie le 06/04/2012.  

Je ne vais pas faire comme si j'avais compris toutes les améliorations disponibles, mais sachant qu'il est facile de [tester les dernière version de Git](http://denisroussel.fr/2012/04/26/tester_la_derniere_version_de_git.html), je vais simplement détailler les fonctionnalités qui me semblent avoir un intérêt direct pour mon utilisation régulière.

## Cloner une seule branch

> _"git clone" learned "--single-branch" option to limit cloning to a single branch (surprise!); tags that do not point into the history of the branch are not fetched._

### Le temps

Sur des gros projets, comme celui de PMSIpilot, cette otion permet de cloner le projet plus rapidement. Cela peut s'avérer utile lorsque l'on ne souhaite pas disposer de toutes les branches mais simplement du master pour faire un test rapide de l'application.

A l'ancienne :

    $ time git clone git@pmsipilot.git:pmsipilot.git pmsipilot1
    Cloning into pmsipilot1...
    remote: Counting objects: 783421, done.
    remote: Compressing objects: 100% (242790/242790), done.
    remote: Total 783421 (delta 499911), reused 782818 (delta 499453)
    Receiving objects: 100% (783421/783421), 7.20 GiB | 29.29 MiB/s, done.
    Resolving deltas: 100% (499911/499911), done.

    real	8m23.102s
    user	7m9.927s
    sys	1m37.066s

Avec une seule branch :

    $ time gitdev clone --single-branch git@pmsipilot.git:pmsipilot.git pmsipilot2
    Cloning into 'pmsipilot2'...
    remote: Counting objects: 691388, done.
    remote: Compressing objects: 100% (229919/229919), done.
    remote: Total 691388 (delta 438843), reused 675416 (delta 424889)
    Receiving objects: 100% (691388/691388), 5.75 GiB | 24.36 MiB/s, done.
    Resolving deltas: 100% (438843/438843), done.
    
    real	7m51.321s
    user	6m12.167s
    sys	1m19.793s

On voit cependant que le gain de temps dépasse difficilement les 6%...

### La taille

Concernant la place occupée sur le disque, les résultats sont plus intéressants :

    $ du -s pmsipilot1 pmsipilot2
    9535232	pmsipilot1
    8019856	pmsipilot2

Le gain de place dépasse les 15%, ce qui peut s'avérer intéressant lorsque l'on clone plusieurs gros projets en même temps, notamment lors de l'intégration continue.

Attention cependant, toutes ces statistiques de comptoirs n'ont été réalisées que sur un seul projet : elle ne sont donc statistiquement pas acceptables :-)

D'autant plus que les résultats doivent probablement beaucoup varier d'un projet à l'autre.

### La blague

Effectivement, il y a une bonne blague dans cette nouvelle fonctionnalité : on ne choisi pas la branch qui est clonée.

Facile.

Donc après une petite excursion dans le code source de Git, il semblerait que 

## La description d'une branch

C'est en fait une évolution qui date de la version [1.7.9](https://raw.github.com/gitster/git/master/Documentation/RelNotes/1.7.9.txt) de Git.

> "git branch --edit-description" can be used to add descriptive text to explain what a topic branch is about.

Sur le coup, je me suis dit : "Chouette on va pouvoir détailler un peu le contenu de chaque branch et utiliser ensuite cette description dans nos super logiciels [Crew](http://pmsipilot.github.com/Crew/) et [Gitboard](http://denisroussel.fr/Gitboard/) !".

Mais non.

C'est une fonctionnalité qui ajoute simplement une description _locale_ à une branch... 

Ainsi après la commande adéquate :

    $ gitdev checkout -b nouvelle-feature
    $ gitdev branch --edit-description

suivie de la saisie d'une description dans l'éditeur de texte qui s'ouvre automatiquement, un nouvel attribut fait son apparition dans le fichier de config de Git : 

    [branch "nouvelle-feature"]
        description = Description plus complète de la feature

Donc cela ne sert finalement pas à grand chose puisque cette information n'est pas contenu dans les méta data de la branch. C'est probablement pour cette raison que seule la commande `request-review` l'utilise actuellement.
