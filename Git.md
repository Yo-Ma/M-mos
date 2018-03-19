# MÉMO GIT


## La logique Git 

Git, comme système, gère et manipule trois arbres au cours de son opération normale :

| Arbre  | Rôle   |
| :----: | :----: |
| Répertoire de travail | Bac à sable |
| Index | Instantané proposé de la prochaine validation _Stagging Area_ |
| HEAD | Instantané de la dernière validation, prochain parent |


## Les basiques

Télécharger un projet existant

    $ git clone [URL_DU_DEPOT]

(Ré)-Initialiser un projet git (crée un dossier .git contenant la config du projet)

    $ git init
    
Initialiser un projet dans un répértoire existant :
    
    $ git init
    $ cd [NOM_DU_REPERTOIRE]
    $ git remote add origin [URL_DU_DEPOT]
    $ git add .
    $ git commit -m 'First commit'
    $ git push -u origin master
            ----------
    $ git push -u origin --all
    $ git push -u origin --tags         => Permet, s'il en existe, de pousser les tags avec les commits


Récupérer l'état actuel des fichiers dans un dossier git (apparaissent les fichiers modifiés depuis le dernier commit etc...)

    $ git status


Ajouter le(s) élément(s) dans la liste du suivi de version. Ils seront ajoutés au HEAD mais pas encore dans le dépôt distant.

    $ git add [NOM DU/DES FICHIER/S]
    $ git add .         => Ajoute tous les fichiers modifiés


Enregistrer et nomme (via -m "") les changements effectués

    $ git commit -m "[MESSAGE]"         => Ajoute un message au commit
_-m permet d'ajouter un message au commit, s'il n'est pas mis, git ouvrira l'éditeur de texte par défaut afin de le renseigner_.



## Les commits

Afficher tous les 'commits' d'un projet (sous forme de liste)

    $ git log

> commit d3606256e46967624fb2f591b11b64958a2e8a0e (HEAD -> master, origin/master)   
> Author: Yo-Ma <>  
> Date:   Thu Jan 4 09:29:45 2018 +0100  
> _Add glossaire SQL & modif glossaire PHP_ 
> 
> commit c08bc5c8d3639c2b8876e900f82babc7d0aab8b2  
> Author: Yo-Ma <>  
> Date:   Wed Jan 3 16:20:49 2018 +0100  
> _Modif schema_

    $ git log --oneline         => Résultat sous forme condensé en une ligne par entrée
   
> d360625* (HEAD -> master, origin/master)  
> Add glossaire SQL & modif glossaire PHP  
> c08bc5c Modif schema  
> ...

_* : Pour faire référence à un commit, l'on peut se contenter des premiers caractères de son identifiant (tant que la référence reste unique)._ 


#### $ GIT REMOTE

Ajouter un nouveau dépôt distant Git comme nom court auquel il est facile de faire référence

    $ git remote add [NOM_COURT] [URL]
    
Visualiser les serveurs distants enregistrés

    $ git remote
    $ git remote -v         => montre l’URL que Git a stockée pour chaque nom court
    
Ajouter au dossier git un "repository" distant, et le lier à 'origin'

    $ git remote add origin


#### $ GIT PUSH & PULL
**_Pousser ou récupérer son travail sur ou depuis un dépôt distant_**

    $ git push
    $ git push -u origin master         => pousse la branche MASTER vers le serveur ORIGIN 
    (pour rappel, cloner un dépôt définit automatiquement ces noms)


Récupérer et fusionner les changements distants

    $ git pull


Montrer les différences entre l'état actuel local et un état 'committé'

    $ git diff
    $ git diff [BRANCHE_SOURCE] [BRANCHE_CIBLE]          => Après avoir fusionné les changements, en avoir un aperçu 
   
      
Comparer les fichiers indexés et le dernier instantané 
    
    $ git diff --staged  
    
     
Inverse de 'add' sur un élément. Si l'élément a été ajouté (add) au commit en cours, il ne le sera plus.

    $ git reset


Remettre l'élément à l'état du précédent commit

    $ git checkout


## LES BRANCHES

_**Les branches sont utilisées pour développer des fonctionnalités isolées des autres.** 
La branche master est la branche par défaut._ 

Créer une nouvelle branche

    $ git branch [NOM_DE_LA_BRANCHE]
L'option -b permet, dans la foulée, de pointer 'HEAD' sur la branche nouvelle créée

On crée ainsi un nouveau contexte, indépendant de la branche "master". 
Il sera, ensuite, possible de les fusionner 'merging'.


Lister l'ensemble des branches actuellement disponibles.

    $ git branch 


Changer de branche de travail, 'HEAD'

    $ git checkout [NOM_DE_LA_BRANCHE]
    
    
Une branche n'est pas disponible pour les autres tant qu'elle n'est pas envoyée vers le dépôt distant
    
    $ git push origin [NOM_DE_LA_BRANCHE]
    

Supprimer une branche

    $ git branch -d [NOM_DE_LA_BRANCHE]        



**Remplacer les changements locaux**

Annuler les changements locaux
    
    $ git checkout -- <filename>
Cela remplacera les changements dans votre arbre de travail avec le dernier contenu du HEAD. 
Les changements déjà ajoutés à l'index, aussi bien que les nouveaux fichiers, seront gardés.

Si à la place, l'on soufaite supprimer tous les changements et validations locaux :
Il faut récupérer le dernier historique depuis le serveur...

    $ git fetch origin
    
...et pointer la branche principale locale dessus

    $ git reset --hard origin/master


Supprimer du répértoire local un ou plusieurs éléments, et notifier git de cette suppression (ajout dans le journal)

    $ git rm [NOM_DE_L'ÉLÉMENT]



**Fusionner local & distant**

Fusionner la branche dans laquelle on travaille avec la branche master

    $ git merge 
    $ git merge [NOM_DE_LA_BRANCHE]         => pour fusionner une autre branche avec la branche active (par exemple master)

 
 
 ## LES TAGS (étiquettes)

Il est recommandé de créer des tags pour les releases de programmes. 
C'est un concept connu, qui existe aussi dans SVN. Exemple, vous pouvez créer un tag nommé 1.0.0 en exécutant la commande :
    
    $ git tag 1.0.0 1b2e1d63ff
    
Le **'1b2e1d63ff'** désigne les 10 premiers caractères de l'identifiant du commit que vous voulez référencer avec ce tag. 


## La configuration

Configurer son nom d'utilisateur et son email

    $ git config --global user.name "[USERNAME]"
    $ git config --global user.email "[EMAIL]"


## Liens utiles

**Guides :** \
[Git Community Book] (http://book.git-scm.com/fr) \
[Pro Git] (http://progit.org/book/) \
[Think like a git] (http://think-like-a-git.net/) \
[GitHub Help] (http://help.github.com/) \
[A Visual Git Guide] (http://marklodato.github.com/visual-git-guide/index-en.html)

**Clients graphiques :** \
[GitX (L) (OSX, open source)] (http://gitx.laullon.com/) \
[Tower (OSX)] (http://www.git-tower.com/) \
[Source Tree (OSX, free)] (http://www.sourcetreeapp.com/) \
[GitHub for Mac (OSX, free)] (http://mac.github.com/) \
[GitBox (OSX)] (https://itunes.apple.com/gb/app/gitbox/id403388357?mt=12) \
[Git Extensions (WIN, open source)] (https://code.google.com/p/gitextensions/) 
