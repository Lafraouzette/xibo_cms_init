# Guide Xibo CMS Docker

## **Comment lancer le CMS**
- Vous aurez besoin de deux fichiers principaux :
  1. `docker-compose.yaml` : Configuration pour démarrer les conteneurs.
  2. `config.env` : Fichier de configuration des variables d'environnement (à créer à partir de `config.env.template`).
  3. Lancer le fichier `docker-compose.yml` :
     ```sh
     docker-compose -f path\docker-compose.yml up --build
     ```
  4. Identifiants par défaut : utilisateur `xibo_admin` et mot de passe `password`.

## **Les services**
- Consultez le fichier `docker-compose.yml` pour voir tous les services.
- Principalement, nous avons besoin de :
  1. Base de données : MySQL
  2. XMR
  3. Serveur CMS

