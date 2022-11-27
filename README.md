# DevOps TP2
1) J'ai décidé d'utiliser debian 11.5 car j'y suis habitué, et on va nommer le stage build :
FROM debian:11.5 as build

2) On commence par mettre à jour les packages par défaut d'ubuntu puis on installe nodejs et on nettoie le cache avec :
RUN apt-get update -yq \
        && apt-get install curl gnupg -yq \
        && curl -sL https://deb.nodesource.com/setup_16.x | bash \
        && apt-get install nodejs -yq \
        && apt-get clean -y
        
3) Ensuite on ajoute un dossier add que l'on va définir comme espace de travail avec : 
ADD . /app/
WORKDIR /app

4) Puis on installe npm sous sa dernière version en global ainsi que express (que l'on utilise dans notre code) avec :
RUN npm install -g npm && npm install express

5) Et enfin, on lance le serveur en tant que l'utilisateur spécifié (root, même si le but même de spécifier l'utilisateur est de ne pas passer par root) : 
CMD npm run start
USER root


Pour créér l'imag en multi-stage (Dockerfile.2), nous allons procéder comme pour le premier fichier Dockerfile jusqu'à la 4e étape, puis nous allons créer le stage exec depuis build avec :
FROM build as exec

Et nous allons lancer le serveur en tant que root: 
CMD npm run start
USER root


Voici les commandes à utiliser :
  - Pour créer l'image avec un seul stage : docker build -t tp2 .
  - Pour créer l'image avec 2 stages : docker build -t tp2 -f Dockerfile.2 .
  - Pour créer et lancer un conteneur depuis cette image sur le port d'écoute du serveur : docker run -d -p 3000:3000 tp2
