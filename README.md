# Ghost - Plateforme de publication professionnelle

Ghost est une plateforme de publication open source moderne, conçue pour les créateurs de contenu, les blogueurs et les médias.

## Fonctionnalités principales

- **Newsletter intégré** : Gestion complète des newsletters et abonnés
- **Membres & abonnements** : Système de membres avec abonnements payants
- **API headless** : API RESTful pour une intégration flexible
- **Éditeur moderne** : Éditeur markdown avec aperçu en temps réel
- **Thèmes personnalisables** : Thèmes personnalisables avec Handlebars

## Prérequis

- Docker
- Docker Compose

## Installation

1. Clonez ce template
2. Copiez `.env.example` vers `.env` et configurez les variables
3. Lancez la stack :
   ```bash
   docker-compose up -d
   ```
4. Accédez à `http://localhost:8080/ghost` pour terminer la configuration

## Variables d'environnement

| Variable | Description | Valeur par défaut | Requis |
|----------|-------------|-------------------|--------|
| MYSQL_ROOT_PASSWORD | Mot de passe root MySQL | rootpassword | Oui |
| MYSQL_DATABASE | Nom de la base de données | ghost | Oui |
| MYSQL_USER | Utilisateur MySQL | ghost | Oui |
| MYSQL_PASSWORD | Mot de passe MySQL | ghostpassword | Oui |
| GHOST_URL | URL publique | http://localhost:8080 | Oui |
| MAIL_TRANSPORT | Transport email | SMTP | Non |
| MAIL_HOST | Serveur SMTP | smtp.example.com | Non |
| MAIL_PORT | Port SMTP | 587 | Non |
| MAIL_USER | Utilisateur SMTP | user | Non |
| MAIL_PASSWORD | Mot de passe SMTP | password | Non |

## Volumes persistants

- `ghost_content` : Contenu de Ghost (articles, pages, paramètres)
- `ghost_images` : Images téléchargées
- `ghost_mysql_data` : Données MySQL
- `ghost_mysql_config` : Configuration MySQL

## Ports

- **8080** : Interface web de Ghost

## Maintenance

### Sauvegarde

```bash
# Sauvegarde des volumes
docker run --rm -v ghost_content:/data -v $(pwd):/backup alpine tar czf /backup/ghost_content_backup.tar.gz -C /data .
docker run --rm -v ghost_mysql_data:/data -v $(pwd):/backup alpine tar czf /backup/mysql_data_backup.tar.gz -C /data .
```

### Mise à jour

1. Arrêtez les conteneurs : `docker-compose down`
2. Mettez à jour l'image dans `docker-compose.yml`
3. Relancez : `docker-compose up -d`

## Dépannage

### Vérifier l'état des services

```bash
docker-compose ps
docker-compose logs ghost
docker-compose logs mysql
```

### Accéder à la base de données

```bash
docker exec -it ghost_mysql mysql -u ghost -p ghost
```

## Sécurité

- Changez tous les mots de passe par défaut
- Utilisez HTTPS en production
- Configurez correctement les paramètres SMTP
- Limitez l'accès aux ports exposés

## Documentation

- [Documentation officielle Ghost](https://ghost.org/docs/)
- [API Ghost](https://ghost.org/docs/api/)
- [Thèmes Ghost](https://ghost.org/docs/themes/)

## Support

Pour toute question, consultez la [documentation officielle](https://ghost.org/docs/) ou les [forums de la communauté](https://forum.ghost.org/).