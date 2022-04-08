# Veille sur Docker :fish: :+1:
##  Qu'est ce que Docker ?
Docker est une plateforme lancée en 2013 permettant aux développeurs et aux administrateurs système de développer, déployer et exécuter des applications avec des conteneurs.
En d’autres termes, nous pouvons embarquer une application avec toutes ses dépendances dans un process isolé (conteneur) qui peut ensuite être exécutée dans n’importte quelle machine, n’importe quel système d’exploitation qui est compatible avec le moteur Docker.
## Qu'est ce la conteneurisation ?
La conteneurisation permet de packager (regrouper) tous les scripts, API, librairies dont une application a besoin. L’objectif de la conteneurisation est d'exécuter l’application sur n’importe quel noyau compatible.

Elle évite de se soucier d’interactions ou d’incompatibilités avec les conteneurs déjà présents ou à venir sur cette machine.

Elle permet de ne pas occuper autant de ressources que réclamerait une machine virtuelle (ou virtual machine, VM), qui emporte son propre système d’exploitation et bloque des ressources à son lancement.

## Comparaison entre conteneur et machine virtuelle
![image de comparaison conteneur et VM](https://user.oc-static.com/upload/2019/05/13/15577645779374_vm-vs-conteneur.png)
Les conteneurs ne reservent que les ressources nécessaires et démarrent plus rapidement que les VM.
## Pourquoi utiliser les conteneurs ?
Moins couteux
Augmente la densite de deploiement
:warning:
``Il faut savoir que VM et conteneur son liés.``
##  CHAPITRE :one:: Prise en main de Docker
### lister les images disponibles sur votre ordinateur
``docker images``
### recuperer ou telecharger une image
``docker pull nom_image``
### executer un conteneur
``docker run -it nom_image``
### executer un conteneur de maniere détachée 
``docker run -it -d nom_image``
### pour arreter le processus d'une image
``docker stop id_processus``
### faire le menage sur docker
``docker system prune``
Cette commande supprime l'ensemble des conteneurs docker **qui ne sont pas en cours, ce qui ne sont pas utilise par docker mais aussi le cache**
## Creer une image avec le DOCKERFILE
Dans ce chapitre nous créerons une image contenant un contenant *node js*, pour ce faire nous allons creer un fichier nommé Dockerfile qui est comparable au fichier ``composer.json et package.json`` sur php et nodejs
La commande ``FORM`` permet de definir l'image de depart que nous souhaitons utiliser pour creer notre image. Elle ne peut être utilisé q'une seule fois

La commande ``RUN`` permet d'enchainer les commandes necessaires au bon fonctionnement de notre image

La commande ``ADD`` permet de telecharger ou copier des fichiers dans l'image

La commande ``WORKDIR`` permet de modifier le repertoire courant.Elle est comparable au ``cd`` 
La commande ``EXPOSE`` permet de preciser le port sur lequel notre image ecoutera
La commande ``VOLUME`` permet de definir les repertoires que nous souhaitons partager

La commande ``CMD`` contient la commande que nus devons executer apres installation de l'image
## Le dossier dockerignore
Ce fichier est comparable au fichier ``.gitignore``, elle contient les dossiers et fichiers qui seront ignorés 
## Lancer son propre conteneur
Après configuration de votre conteneur grâce au ``DockerFile``, lancer votre conteneur avec la commande **``docker build -t nom_conteneur .``**
Le drapeau ``-t`` permet de donner un nom à notre image, le ``.``  correspond au repertoire où se trouve notre le dockerfile
## Partager nos images grâce au DockerHub
Étant donné que l'on peut être amené à travailler en ligne, un moyen de partage de ressources est nécessaire, en ce sens nous pouvons utiliser git pour nous patager le fichier dockerfile mais aussi le ``DockerHub``. Pour cela il est impératif d'utiliser les commandes suivantes:
``docker tag nom_image:latest nom_utilisateur/nom_image_sur_le_hub:latest``: :smile: cette commande semble compliqué mais loin de là, elle permet de creer un lien entre  notre image en local ``nom_image`` et notre image en ligne ``nom_utilisateur/nom_image_sur_le_hub``
``docker push nom_utilisateur/nom_image_sur_le_hub:latest``: vous permetta de pousser le projet(conteneur) en ligne :airplane:
Et voilà votre image est maintenant disponible sur le Hub :100:

## CHAPITRE :two:: Docker compose
Docker composer permet d'orchestrer nos conteneurs et de simplifier le deploiement sur les environnements.Il est ecrit sur du python et permet d'écrire sur des fichier ``yaml`` des conteneurs comme un ensemble de services

### recuperer ou telecharger une image
``docker-compose pull nom_image``
### lancer un conteneur 
``docker-compose up``
Une stack est un ensemble de conteneurs docker lances via un seul fichier docker-compose
### voir le statut d'une stack
``docker-compose ps``
### voir les logs d'une stack
``docker-compose logs -f --tail 5`se 
``docker-compose stop``
### supprimer une stack docker-compose 
``docker-compose down``
### valider une stack docker-compose 
``docker-compose config``
## Definir notre fichier docker-compose
Un fichier docker compose doit toujours contenir:
une ``version`` permet de savoir lea version minimale
## Liens utiles :link:
[Docker Hub](https://hub.docker.com/)
Installation de docker desktop sur ubuntu :link:https://docs.docker.com/desktop/linux/
webdevops /php-nginx