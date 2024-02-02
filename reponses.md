Alexandre Bruneau

## B1-Git - Partie 1 : Création du dépôt et _commits_

- Ouvrir un terminal (terminal _Git Bash_ à privilégier)

- Créer, en ligne de commande, un répertoire `tp-git`
-> mkdir tp-git

- Se déplacer dans le répertoire
-> cd tp-git

- Vérifier qu'on est dans le bon répertoire en affichant le chemin du répertoire courant
-> pwd

- Initialiser un dépôt Git
-> git init

- Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s'assurer que le répertoire `.git` à été créé
-> ls -a

- Ouvrir ce répertoire sous VS Code

- Exécuter `git status` et copier/coller la sortie

-> Sur la branche master

Aucun commit

rien à valider (créez/copiez des fichiers et utilisez "git add" pour les suivre)

- Créer le fichier `fichier1.md` avec un contenu quelconque et l'enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)

-> nano fichier1.md

  - Attention, il s'agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.

- Créer le fichier `fichier2.md` avec un contenu quelconque et l'enregistrer

-> nano fichier2.md

- Exécuter `git status` et copier/coller la sortie

-> Sur la branche master

Aucun commit

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
	fichier1.md
	fichier2.md

aucune modification ajoutée à la validation mais des fichiers non suivis sont présents (utilisez "git add" pour les suivre)

- Ajouter `fichier1.md` à l'index de Git (zone de _Staging_)

-> git add fichier1.md

- Exécuter `git status` et copier/coller la sortie

-> Sur la branche master

Aucun commit

Modifications qui seront validées :
  (utilisez "git rm --cached <fichier>..." pour désindexer)
	nouveau fichier : fichier1.md

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
	fichier2.md

- Créer un _commit_ avec pour message : "Ajout de fichier1.md"

-> git commit -m "Ajout de fichier1.md"

- **_VALIDATION PROF01_**

- Exécuter `git status` et copier/coller la sortie

-> On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	fichier2.md

nothing added to commit but untracked files present (use "git add" to track)


- Modifier `fichier1.md` et enregistrer

-> nano fichier1.md

- Exécuter `git status` et copier/coller la sortie

-> On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")

- Ajouter `fichier1.md` et `fichier2.md` à la zone de _Staging_

-> git add fichier1.md fichier2.md

- Créer un _commit_ "Ajout de fichier2.md et modification de fichier1.md"

-> git commit -m "Ajout de fichier2.md et modification de fichier1.md"

- Exécuter `git status` et copier/coller la sortie

-> On branch master
nothing to commit, working tree clean

- Copier/coller l'ID des deux premiers _commits_ (utiliser `log`) :

  - ID _commit_ 1 : f8b5df9a132152361fce62c3ca6608c25b8d8601
  - ID _commit_ 2 : c51b342170d5d69099bacb661093bb10dc1592b9

- Que signifie qu'un fichier est "_tracked_" ou "_untracked_" ?

-> "tracked" signifie qu'il est géré par Git. "_untracked_" signifie qu'il ne l'est pas".

- Pourquoi doit-on passer les fichiers par la zone de _Staging_ (l'index) avant de les committer ?

-> afin de les ajouter au prochain commit 

- **_VALIDATION PROF02_**

## B1-Git - Partie 2 : Gestion de branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- Créer une branche `fonctionnalite1`

-> git branch fonctionnalite1

- Lister les branches

-> git branch

- Se déplacer sur la branche `fonctionnalite1`

-> git switch fonctionnalite1

- Lister les branches

-> git branch

- Que représente l'étoile à côté des noms des branches ?

-> elle indique la branche dans laquelle on se trouve actuellement

- Créer un nouveau fichier `fichier3.md`

-> nano fichier3.md

- Modifier le fichier `fichier2.md`

-> nano fichier2.md

  - Comment utiliser VS Code pour qu'il nous montre les différences entre l'ancienne version de `fichier2.md` et la version courante que l'on vient d'éditer ?

-> en cliquant sur fichier2.md dans la section changements

- Committer ces deux modifications : "Fonctionnalité 1 - première phase"

-> git add fichier2.md fichier3.md
   git commit -m "Fonctionnalité 1 - première phase"

- Créer un nouveau fichier `fichier4.md`

-> nano fichier4.md

- Modifier de nouveau le fichier `fichier2.md`

-> nano fichier2.md

- Committer ces deux modifications : "Fonctionnalité 1 - terminée"

-> git add fichier2.md fichier4.md
   git commit -m "Fonctionnalité 1 - terminée"

- **_VALIDATION PROF03_**

- Afficher la liste des fichiers du répertoire

-> ls
"fichier1.md  fichier2.md  fichier3.md  fichier4.md"

- Se déplacer sur la branche `master`

-> git switch master

- Afficher la liste des fichiers du répertoire

-> ls
"fichier1.md  fichier2.md"

- Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?

-> Les fichiers 3 et 4 ont uniquement été ajouté à la branche fonctionnalite1, on ne peut donc pas les voir lorsqu'on est dans la branche master.

- Créer une nouvelle branche `fonctionnalite2`

-> git branch fonctionnalite2

  - Cette branche ne va pas avoir toutes les données incluses dans `fonctionnalite1`. Pourquoi ?

-> Elle a été créée à partir des fichiers de la branche actuelle, c'est-à-dire master.

  - Qu'aurait-il fallu faire si on avait souhaité démarrer la branche `fonctionnalite2` en intégrant les modifications récentes de `fonctionnalite1` ?

-> Se déplacer dans la branche fonctionnalite1 puis faire "git branch fonctionnalite2".

- Se déplacer sur la nouvelle branche `fonctionnalite2`

-> git switch fonctionnalite2

- Créer un nouveau fichier `fichier5.md`

-> nano fichier5.md

- Faire un _commit_ intégrant cette ajout : "Ajout fichier5.md"

-> git add fichier5.md
   git commit -m "Ajout fichier5.md"

- Entrer la commande `git log --oneline --decorate --graph --all` pour visualiser, sur le terminal, le graphe des _commits_ sur toutes les branches

  - Noter la « déviation » entre les deux branches, à partir de la branche `master` (schématisée sous forme de traits)
  - l'option `--all` permet de visualiser toutes les branches, pas seulement celle sur laquelle on est
  - l'option `--oneline` affiche les _commits_ sur une seule ligne
  - l'option `--graph` affiche le log sous forme de graphe
  - (utilisez si besoin les touches haut/bas pour naviguer dans la sortie de cette commande et `Q` pour quitter)

- Installer l'extension VS Code _Git Graph_ et visualiser le graphe actuel des _commits_ à l'aide de cette extension

  - Sur cette représentation, que représente les points ?

-> Les commits.

  - Comment voit-on sur quelle branche on est actuellement ?

-> Un point est présent juste avant le nom de la branche actuelle.

- **_VALIDATION PROF04_**

## Partie 3 - Fusionner des branches

_Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite._

- On considère que la branche originale (`master` ou `main`) est la branche d'intégration, c'est-à-dire celle qui va contenir l'historique de toutes les modifications développées au fur et à mesure dans les branches annexes

- Se déplacer sur la branche `master`

-> git switch master

  - Noter le changement dans l'onglet _Git Graph_

-> Le point est maintenant devant master.

- On va maintenant intégrer la branche `fonctionnalite1`, qui est terminée, dans la branche d'intégration (ça s'appelle une _fusion_, ou un _merge_) : fusionner avec la branche `fonctionnalite1`

-> git merge fonctionnalite1

- Noter le changement dans l'onglet _Git Graph_. Que signifie la mention _Fast-forward_ indiquée par la sortie de la commande ?

-> master et fonctionnalite1 sont maintenant sur la même ligne. _Fast-forward_ signifie la mise à jour de master.

- On veut maintenant fusionner `fonctionnalite2` dans la branche d'intégration (`master`). Effectuer cette fusion.

-> git merge fonctionnalite2

- Noter le changement dans l'onglet _Git Graph_. Que signifie la mention _Merge made by the ... strategy_ indiquée par la sortie de la commande ?

-> master est maintenant l'état le plus récent du dépot. _Merge made by the 'Ort' strategy_ indique la méthode utilisée pour le merge.

- Quelle est la différence fondamentale avec la fusion précédente ?

-> Elle a été réalisée 

- Créer une nouvelle branche `fonctionnalite3`, se déplacer dessus, et modifier le fichier `fichier1.md` en y ajoutant une ligne de texte. Committer : "Modification fichier1 pour fonctionnalité 3"

-> git switch -c fonctionnalite3
   nano fichier1.md
   git add fichier1.md
   git commit -m "Modification fichier1 pour fonctionnalité3"

  - Comment utiliser _Git Graph_ pour qu'il nous montre les différences entre l'ancienne version de `fichier1.md` et la version courante que l'on vient de committer ?

-> cliquer sur le commit puis sur fichier1.md 

- Repartir sur `master`, et modifier `fichier1.md` en y ajoutant aussi une ligne (différente de celle qu'on a ajoutée sur l'autre branche) ; ajouter à l'index et _commit_

-> git switch master
   nano fichier1.md
   git add fichier1.md
   git commit -m "Ajout ligne fichier1"

- Tenter de fusionner la branche `fonctionnalite3` avec `master`

  - Que se passe-t-il et pourquoi ?

-> Il y a un conflit car 

- Lancer un `git status`

  - Que doit-on faire si on veut annuler la fusion en cours ? (**ne pas lancer la commande**)

- On veut résoudre le conflit. Plusieurs possibilités :

  - Conserver uniquement les modifications faites dans `fonctionnalite3`
  - Conserver uniquement les modifications faites dans `master`
  - Conserver les deux modifications
  - Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement

- Git nous laisse totalement la main et ne va pas essayer d'imposer l'un de ces choix pour nous, ni nous assister dans l'application automatique de l'un d'entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

- Ouvrir le fichier en question sous VS Code

  - La chaîne `<<<<<<<<<<` marque le début du conflit
  - La chaîne `>>>>>>>>>>` marque la fin du conflit
  - La chaîne `==========` sépare les deux versions

- Éditer le fichier pour faire en sorte d'intégrer les deux modifications ; à la fin de l'édition :

  - Il ne doit plus y avoir de marques quelconques en dehors des ajouts fonctionnels originaux, c'est-à-dire pas de `<<<<<<<<<<`, ni de mentions de nom de branche, etc. : vous rendez le fichier tel qu'il doit apparaître dans le _commit_ de fusion, avec les conflits résolus manuellement
  - Sauvegarder

- Ajouter les modification à l'index et committer

- NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

- NB : les conflits de fusion sont fréquents lorsqu'on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

- Les branches créées n'ont plus de raison d'exister

  - Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d'intégration
  - On va vouloir nettoyer le dépôt en les supprimant
  - Cela ne va bien sûr pas supprimer tous les _commits_ qui y sont associés
  - Attention cependant d'éviter en général de supprimer une branche qui n'a pas encore été intégrée à la branche d'intégration, sauf on souhaite vraiment abandonner le développement de cette branche
  - Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
  - Nouvelle tâche ? => nouvelle branche à partir d'un _commit_ de la branche d'intégration (en général le plus récent)
  - Tâche terminée ? => fusion dans la branche d'intégration et suppression de la branche

- Supprimer les trois branches `fonctionnalitex` (attention : on ne peut pas supprimer une branche sur laquelle on est)
