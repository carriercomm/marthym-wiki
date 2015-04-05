Comment envoyer une requête POST avec le contenu d'un fichier dans le body. Le tout avec un header :

``` sh
curl -H "Content-Type: application/json" --data "@salut.txt" http://localhost:8082/export
``` 

Le fichier salut.txt est dans le répertoire courant ...

<!-- tags: linux, network -->
