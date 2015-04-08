[[_TOC_]]
Voici un glossaire des lignes de commandes utile sous GIT :

## Création d'un dépot
créez un nouveau dossier, ouvrez le et exécutez la commande<br/>
`git init` <br/>
pour créer un nouveau dépôt. 

## Cloner un dépôt
créez une copie de votre dépôt local en exécutant la commande<br/>
`git clone /path/to/repository`<br/>
si vous utilisez un serveur distant, cette commande sera
`git clone username@host:/path/to/repository`

## Ajouter & valider
Vous pouvez proposer un changement (l'ajouter à l'Index) en exécutant les commandes<br/>
`git add <filename>`<br/>
`git add *`<br/>
C'est la première étape dans un workflow git basique. Pour valider ces changements, utilisez<br/>
`git commit -m "Message de validation"`<br/>
Le fichier est donc ajouté au HEAD, mais pas encore dans votre dépôt distant.

## Envoyer des changements
Vos changements sont maintenant dans le HEAD de la copie de votre dépôt local. Pour les envoyer à votre dépôt distant, 
exécutez la commande<br/>
`git push origin master`<br/>
Remplacez master par la branche dans laquelle vous souhaitez envoyer vos changements.

Si vous n'avez pas cloné votre dépôt existant et voulez le connecter à votre dépôt sur un serveur distant, 
vous devez l'ajouter avec<br/>
`git remote add origin <server>`<br/>
Maintenant, vous pouvez envoyer vos changements vers le serveur distant sélectionné

## Branches
Créer une nouvelle branche nommée "feature_x" et passer dessus pour l'utiliser<br/>
`git checkout -b feature_x`<br/>
retourner sur la branche principale<br/>
`git checkout master`<br/>
et supprimer la branche<br/>
`git branch -d feature_x`<br/>
une branche n'est pas disponible pour les autres tant que vous ne l'aurez pas envoyée vers votre dépôt distant<br/>
`git push origin <branch>`

## Mettre à jour & fusionner
pour mettre à jour votre dépôt local vers les dernières validations, exécutez la commande<br/>
`git pull`
dans votre espace de travail pour récupérer et fusionner les changements distants. 
Pour fusionner une autre branche avec la branche active (par exemple master), utilisez<br/>
`git merge <branch>`<br/>
dans les deux cas, git tente d'auto-fusionner les changements. Malheureusement, ça n'est pas toujours possible et 
résulte par des conflits. Vous devez alors régler ces conflits manuellement en éditant les fichiers indiqués par git. 
Après l'avoir fait, vous devez les marquer comme fusionnés avec<br/>
`git add <filename>`<br/>
après avoir fusionné les changements, vous pouvez en avoir un aperçu en utilisant<br/>
`git diff <source_branch> <target_branch>`

## tags
il est recommandé de créer des tags pour les releases de programmes. c'est un concept connu, qui existe aussi dans SVN. 
Vous pouvez créer un tag nommé 1.0.0 en exécutant la commande<br/>
`git tag 1.0.0 1b2e1d63ff`
le 1b2e1d63ff désigne les 10 premiers caractères de l'identifiant du changement que vous voulez référencer avec ce tag. 
Vous pouvez obtenir cet identifiant avec<br/>
`git log`<br/>
vous pouvez utiliser moins de caractères de cet identifiant, il doit juste rester unique.


## Remplacer les changements locaux
Dans le cas où vous auriez fait quelque chose de travers (ce qui bien entendu n'arrive jamais ;) 
vous pouvez annuler les changements locaux en utilisant cette commande<br/>
`git checkout -- <filename>`<br/>
cela remplacera les changements dans votre arbre de travail avec le dernier contenu du HEAD. 
Les changements déjà ajoutés à l'index, aussi bien les nouveaux fichiers, seront gardés.

Si à la place vous voulez supprimer tous les changements et validations locaux, récupérez le dernier historique depuis 
le serveur et pointez la branche principale locale dessus comme ceci<br/>
`git fetch origin`<br/>
`git reset --hard origin/master`


## Conseils utiles
utiliser des couleurs dans la sortie de git<br/>
`git config color.ui true`

afficher le journal sur une seule ligne pour chaque validation<br/>
`git config format.pretty oneline`

utiliser l'ajout interactif
`git add -i`

## Liens
  * http://rogerdudler.github.io/git-guide/index.fr.html
  * http://book.git-scm.com/
  * http://progit.org/book/
  * http://think-like-a-git.net/
  * http://help.github.com/
  
<!-- --- tags: git -->