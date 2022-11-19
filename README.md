# DevOps

Objectifs : 
- Mise en place d'un environnement de développement et les bases du projet avec le moins de dépendances possibles :
  - Utilisation de la librairie *express* pour la mise d'un serveur web rapide sur http://localhost:3000
- Développer une API qui retourne au format JSON les headers de la requête quand il y une requête HTTP GET sur /ping
  - La requête http://localhost:3000/ping renvoie bien les headers au format .JSON
- Le serveur doit écouter sur un port configurable via la variable d'environnement : PING_LISTEN_PORT ou par défaut sur un port au choix
  - La variable d'environnement PING_LISTEN_PORT permet de choisir un port au choix qui sera utiliser par le serveur. Par exemple : http://localhost:3000 --> http://localhost:2700
- Réponse vide avec code 404 si quoi que ça soit d'autre que GET /ping 
  - Réalisation d'un message d'erreur (par défaut) avec code 404 Not found pour tout autre requête différente que http://localhost:3000/ping 


Pour lancer le projet :

- Utiliser à la suite les commandes :
  - *npx tsc*
  -  *node dist/app.js*
- Un message avec *Express is listning on http://localhost:3000* apparaitra dans la console lors d'une requête dans le navigateur sur l'adresse indiquée.

NOTE : Le projet est téléchargeable en .rar , un extracteur de fichier sera necessaire pour extraire le projet.
