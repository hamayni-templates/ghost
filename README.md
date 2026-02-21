# Ghost — Hamayni Certified Template

## Description
Ghost est une plateforme de publication moderne, rapide et élégante. Ce template inclut Ghost 5.101 + MySQL 8.4, prêt à déployer via Hamayni.

## Prérequis
- Docker & Docker Compose

## Variables d'environnement
| Variable | Requis | Description | Défaut |
|----------|--------|-------------|--------|
| GHOST_URL | **Oui** | URL publique du blog | — |
| MYSQL_PASSWORD | **Oui** | Mot de passe MySQL | — |
| MYSQL_ROOT_PASSWORD | **Oui** | Mot de passe root MySQL | — |
| MYSQL_DATABASE | Non | Nom de la base | ghost |
| MYSQL_USER | Non | Utilisateur MySQL | ghost |

## Déploiement
```bash
docker-compose up -d
```

Ghost sera accessible sur le port **2368**.
L'interface d'administration est disponible sur `/ghost/`.

## Health Check
- URL: `http://localhost:2368/ghost/api/v4/admin/site/`
- Timeout: 60s

## Architecture
- **ghost**: Ghost CMS (Node.js) sur Alpine Linux
- **db**: MySQL 8.4 avec health check intégré
- **Réseau**: Réseau bridge isolé (`ghost_net`)
- **Volumes**: Données persistantes pour le contenu et la BDD

## Licence
MIT — Ghost Foundation
