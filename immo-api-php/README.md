# API Immobilier (immo-api-php)

API REST développée avec Slim 4 pour la gestion immobilière, incluant une base de données MySQL et un stockage S3 optionnel.

## Description

Cette API fait partie d'un ensemble de trois projets :
- API Backend (PHP/Slim 4) - Ce projet
- Interface d'administration (React)
- Interface client (Vue.js)

## Technologies Utilisées

- PHP 8.x
- Slim Framework 4
- MySQL 8.0
- Docker & Docker Compose
- JWT pour l'authentification
- AWS S3 / MinIO pour le stockage des images

## Installation

### Avec Docker (Recommandé)

1. Cloner le dépôt :
```bash
git clone https://github.com/SachaDodane/automa.git
cd automa
```

2. Créer le fichier `.env` :
```bash
cp immo-api-php/.env.exemple immo-api-php/.env
```

3. Configurer les variables d'environnement dans le fichier `.env`

4. Lancer les conteneurs Docker :
```bash
docker-compose up -d
```

L'API sera disponible sur `http://localhost:8080`

### Installation Manuelle

1. Copier `.env.exemple` vers `.env`
2. Configurer les variables d'environnement
3. Installer les dépendances : `composer install`
4. Lancer le serveur : `php -S localhost:<PORT> -t ./public`

## Variables d'Environnement

Configuration requise dans le fichier `.env` :

### Base de données MySQL
- `MYSQL_HOST` : Hôte de la base de données (par défaut : "db" pour Docker)
- `MYSQL_DATABASE` : Nom de la base de données
- `MYSQL_USER` : Utilisateur MySQL
- `MYSQL_PASSWORD` : Mot de passe MySQL

### Stockage S3 (Optionnel)
- `S3_ENDPOINT` : URL du endpoint S3 ou MinIO
- `S3_ACCESS_KEY` : Clé d'accès S3
- `S3_SECRET_KEY` : Clé secrète S3
- `S3_BUCKET` : Nom du bucket S3

## Structure du Projet

```
immo-api-php/
├── src/
│   ├── Controllers/    # Contrôleurs de l'application
│   ├── Middlewares/    # Middlewares (CORS, Auth, etc.)
│   ├── Models/         # Modèles de données
│   ├── Routes/         # Définition des routes
│   ├── Utils/          # Classes utilitaires
│   └── config/         # Configuration
├── public/            # Point d'entrée de l'application
└── vendor/           # Dépendances
```

## GitFlow

Le projet suit la méthodologie GitFlow :

- `main` : Branche de production
- `develop` : Branche de développement
- `feature/*` : Branches de fonctionnalités
- `hotfix/*` : Branches de corrections urgentes

### Processus de développement :
1. Créer une branche feature : `git checkout -b feature/ma-fonctionnalite`
2. Développer la fonctionnalité
3. Créer une Pull Request vers `develop`
4. Après review, merger dans `develop`

## Fonctionnalités

- Authentification JWT
- CRUD pour les biens immobiliers
- Upload d'images (avec support S3/MinIO)
- Pagination des résultats
- Validation des données
- CORS configuré

## Configuration MinIO (Bonus)

Pour activer le stockage d'images avec MinIO :

1. Ajouter le service MinIO dans `docker-compose.yml` :
```yaml
minio:
  image: minio/minio
  ports:
    - "9000:9000"
    - "9001:9001"
  environment:
    MINIO_ROOT_USER: minioadmin
    MINIO_ROOT_PASSWORD: minioadmin
  command: server /data --console-address ":9001"
```

2. Configurer les variables S3 dans `.env` :
```
S3_ENDPOINT=http://minio:9000
S3_ACCESS_KEY=minioadmin
S3_SECRET_KEY=minioadmin
S3_BUCKET=images
```

## Contribution

1. Fork le projet
2. Créer une branche feature
3. Commit les changements
4. Pousser la branche
5. Créer une Pull Request

## Licence

MIT
