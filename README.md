# Architecture de Xibo CMS

Xibo CMS est une solution de gestion de contenu open-source pour les affichages numériques. Son architecture est conçue pour être modulaire, évolutive et facile à déployer. Voici une vue d'ensemble de l'architecture de Xibo CMS :

## Composants Principaux

1. **Serveur Web** : Héberge l'application Xibo CMS et sert les pages web aux utilisateurs. Il peut être configuré avec des serveurs web populaires comme Apache ou Nginx.

2. **Base de Données** : Stocke toutes les informations nécessaires au fonctionnement de Xibo CMS, y compris les utilisateurs, les mises en page, les médias et les programmations. Xibo utilise MySQL ou MariaDB comme système de gestion de base de données.

3.  **Client Xibo** : Les clients Xibo sont les dispositifs qui affichent le contenu. Ils se connectent au serveur Xibo CMS pour télécharger les mises à jour de contenu et les afficher selon la programmation définie.

4. **API Xibo** : Fournit une interface pour interagir avec Xibo CMS de manière programmatique. Elle permet l'intégration avec d'autres systèmes et l'automatisation des tâches courantes.

## Outils et Technologies Utilisés pour le Développement de Xibo CMS

### Langages de Programmation

- **PHP** : Le cœur de Xibo CMS est développé en PHP, un langage de script côté serveur largement utilisé pour le développement web.
- **JavaScript** : Utilisé pour les fonctionnalités interactives côté client et les améliorations de l'interface utilisateur.

### Frameworks et Bibliothèques

- **Slim Framework** : Un micro-framework PHP utilisé pour structurer l'application, gérer les routes et fournir des fonctionnalités de base.
- **Swig** : moteur de template 
- **jQuery** : Une bibliothèque JavaScript utilisée pour simplifier la manipulation du DOM, la gestion des événements et les requêtes AJAX.
-  **Bootstrap** : Un framework CSS populaire utilisé pour concevoir des interfaces utilisateur réactives et modernes.

### Bases de Données

- **MySQL/MariaDB** : Systèmes de gestion de bases de données relationnelles utilisés pour stocker les données de l'application de manière fiable et performante.

### Serveurs Web

- **Apache/Nginx** : Serveurs web populaires utilisés pour héberger l'application Xibo CMS et servir les pages web aux utilisateurs.

### Outils de Développement

- **Composer** : Un gestionnaire de dépendances pour PHP, utilisé pour installer et gérer les bibliothèques et les packages nécessaires au projet.
- **Node.js et npm** : Utilisés pour gérer les dépendances JavaScript et les outils de développement front-end.

### Outils de Test

- **PHPUnit** : Un framework de test pour PHP utilisé pour écrire et exécuter des tests unitaires, assurant la qualité et la fiabilité du code.
- **Selenium** : Un outil de test automatisé pour les applications web, utilisé pour tester les interactions utilisateur et les fonctionnalités de l'interface.

## XMR (Xibo Message Relay)

XMR est un composant de messagerie en temps réel utilisé par Xibo CMS pour envoyer des notifications instantanées aux clients Xibo. Cela permet une communication bidirectionnelle efficace entre le serveur et les clients.

- **Configuration** : XMR doit être configuré avec un serveur de messages compatible, comme Mosquitto. Les détails de connexion sont configurés dans Xibo CMS.
- **Utilisation** : XMR est utilisé pour envoyer des commandes en temps réel, telles que les mises à jour de contenu immédiates, les redémarrages de clients et les notifications de statut.

## Flux de Travail de la Création à la Diffusion de Contenu dans Xibo CMS

### 1. Connexion à Xibo CMS et Création de Contenu

L'utilisateur se connecte à l'interface web de Xibo CMS en utilisant ses identifiants et crée du contenu.

### 2. Programmation du Contenu

L'utilisateur programme le contenu créé pour qu'il soit diffusé à des moments spécifiques. Cela inclut :

- 📅 **Calendrier** : Définition des horaires de diffusion pour chaque mise en page.
- ⚠️ **Priorités** : Définition des priorités pour les contenus critiques ou urgents.
- 🔁 **Répétitions** : Configuration des répétitions pour les contenus récurrents.

### 3. Publication du Contenu

Une fois le contenu programmé, l'utilisateur publie les mises en page. Xibo CMS envoie les informations de programmation aux clients Xibo.

### 4. Téléchargement par les Clients Xibo

Les clients Xibo se connectent au serveur Xibo CMS et téléchargent les mises à jour de contenu selon la programmation définie.

### 5. Diffusion du Contenu

Les clients Xibo affichent le contenu téléchargé selon le calendrier de diffusion. Les mises à jour en temps réel peuvent être envoyées via XMR pour des modifications immédiates.

### Connexion entre le Client Xibo et le CMS Xibo

1. 🔧 **Configuration Initiale** : Lors de la première installation, le client Xibo doit être configuré avec l'URL du serveur CMS Xibo. Cette URL permet au client de savoir où se connecter pour obtenir les mises à jour de contenu.

2. 🔑 **Authentification** : Le client Xibo utilise des identifiants (généralement une clé d'autorisation) pour s'authentifier auprès du CMS. Ces identifiants sont configurés dans le CMS et doivent être saisis dans le client.

3. 🔄 **Requêtes Périodiques** : Une fois configuré, le client Xibo envoie des requêtes périodiques au CMS pour vérifier les mises à jour de contenu. La fréquence de ces requêtes peut être configurée dans les paramètres du client.

4. ⬇️ **Téléchargement de Contenu** : Lorsque le CMS a de nouvelles mises à jour de contenu, il répond aux requêtes du client avec les informations nécessaires. Le client télécharge alors les fichiers de contenu (images, vidéos, etc.) et les stocke localement.

5. 📺**Affichage du Contenu** : Le client Xibo affiche le contenu téléchargé selon la programmation définie dans le CMS. Les mises à jour en temps réel peuvent être envoyées via XMR pour des modifications immédiates.

6. 📊**Retour d'Informations** : Le client Xibo envoie également des informations de retour au CMS, telles que les journaux de diffusion et les états de fonctionnement. Cela permet aux administrateurs de surveiller et de gérer les clients à distance.

# prise de main

- **Configuration des plannings** : Les plannings de diffusion doivent être configurés dans le CMS pour définir les horaires et les contenus à afficher sur les écrans de diffusion. Le Player télécharge les plannings et les met en œuvre conformément aux directives du CMS.
- **Configuration des médias** : Les médias (images, vidéos, pages Web, etc.) doivent être téléchargés et configurés dans le CMS pour être diffusés sur les écrans. Le Player télécharge les médias et les affiche en fonction des plannings définis.
- **Configuration des paramètres de lecture** : Les paramètres de lecture (durée d'affichage, transition, etc.) doivent être configurés dans le CMS pour définir le comportement du Player lors de la diffusion des médias. Le Player respecte ces paramètres pour assurer une lecture fluide et continue des contenus.
- **Configuration des paramètres réseau** : Les paramètres réseau (proxy, pare-feu, etc.) doivent être configurés sur le Player pour permettre une communication efficace avec le serveur CMS. Le Player doit être en mesure de se connecter au serveur et de télécharger les données nécessaires pour afficher le contenu.
- **Configuration des paramètres de sécurité** : Les paramètres de sécurité (certificats, clés, etc.) doivent être configurés sur le Player pour garantir une communication sécurisée avec le serveur CMS. Le Player doit être en mesure de vérifier l'authenticité du serveur et de protéger les données échangées.
- **Configuration des paramètres de journalisation** : Les paramètres de journalisation (niveaux de journalisation, fichiers journaux, etc.) doivent être configurés sur le Player pour enregistrer les activités et les événements survenus lors de l'exécution. Le Player doit être en mesure de générer des rapports d'état et de déboguer les problèmes éventuels.
- **Configuration des paramètres de mise à jour** : Les paramètres de mise à jour (fréquence, mode, etc.) doivent être configurés sur le Player pour permettre la mise à jour automatique du logiciel. Le Player doit être en mesure de télécharger et d'installer les mises à jour disponibles pour améliorer ses performances et sa fiabilité.
- **Configuration des paramètres de redémarrage** : Les paramètres de redémarrage (planifié, automatique, etc.) doivent être configurés sur le Player pour garantir un fonctionnement continu et fiable. Le Player doit être en mesure de redémarrer automatiquement en cas de panne ou de problème technique pour assurer une diffusion ininterrompue des contenus.
- **Configuration des paramètres de sauvegarde** : Les paramètres de sauvegarde (planifiée, incrémentielle, etc.) doivent être configurés sur le Player pour protéger les données et les paramètres de configuration. Le Player doit être en mesure de sauvegarder régulièrement ses données pour éviter toute perte en cas de défaillance matérielle ou logicielle.
- **Configuration des paramètres de récupération** : Les paramètres de récupération (restauration, réinitialisation, etc.) doivent être configurés sur le Player pour permettre une récupération rapide en cas de problème majeur. Le Player doit être en mesure de restaurer ses paramètres et ses données à partir d'une sauvegarde pour reprendre son fonctionnement normal.
- **Configuration des paramètres de supervision** : Les paramètres de supervision (alertes, notifications, etc.) doivent être configurés sur le Player pour surveiller son état et son activité. Le Player doit être en mesure de signaler les problèmes et les incidents au personnel de maintenance pour une intervention rapide et efficace.
- **Configuration des paramètres de gestion** : Les paramètres de gestion (accès distant, contrôle à distance, etc.) doivent être configurés sur le Player pour permettre une gestion centralisée et à distance. Le Player doit être en mesure de recevoir des commandes et des instructions du personnel de supervision pour ajuster son comportement et sa configuration en temps réel.
- **Configuration des paramètres de personnalisation** : Les paramètres de personnalisation (logo, thème, etc.) doivent être configurés sur le Player pour refléter l'identité visuelle de l'entreprise ou de l'organisation. Le Player doit être en mesure d'afficher des éléments graphiques et des messages personnalisés pour renforcer l'image de marque et la communication interne.
- **Configuration des paramètres de compatibilité** : Les paramètres de compatibilité (matérielle, logicielle, etc.) doivent être configurés sur le Player pour garantir une intégration harmonieuse avec les autres composants du système. Le Player doit être en mesure de fonctionner correctement avec les écrans, les périphériques et les logiciels utilisés dans l'environnement de diffusion.
- **Configuration des paramètres de performance** : Les paramètres de performance (optimisation, surveillance, etc.) doivent être configurés sur le Player pour garantir des performances optimales. Le Player doit être en mesure d'ajuster sa consommation de ressources et de surveiller sa charge de travail pour éviter les ralentissements et les interruptions lors de la diffusion des contenus.
- **Configuration des paramètres de personnalisation** : Les paramètres de personnalisation (logo, thème, etc.) doivent être configurés sur le Player pour refléter l'identité visuelle de l'entreprise ou de l'organisation. Le Player doit être en mesure d'afficher des éléments graphiques et des messages personnalisés pour renforcer l'image de marque et la communication interne.
- **Configuration des paramètres de compatibilité** : Les paramètres de compatibilité (matérielle, logicielle, etc.) doivent être configurés sur le Player pour garantir une intégration harmonieuse avec les autres composants du système. Le Player doit être en mesure de fonctionner correctement avec les écrans, les périphériques et les logiciels utilisés dans l'environnement de diffusion.

