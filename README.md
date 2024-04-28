# PawnApp

Bienvenue sur le repository de PawnApp, une application innovante pour la gestion d'un service de prêt sur gage. Ce document contient toutes les instructions nécessaires pour configurer et lancer les environnements de développement et de production.

## Prérequis

Assurez-vous d'avoir installé les logiciels suivants sur votre machine avant de continuer :

- Docker
- Docker Compose
- Git

## Configuration

Pour mettre en place l'environnement de développement local, suivez les étapes ci-dessous :

### Cloner les projets

Ouvrez un terminal et exécutez les commandes suivantes pour cloner les dépôts nécessaires :

```bash
mkdir tempfolder
cd tempfolder
git clone https://github.com/leod1/PawnAppBadFront.git
git clone https://github.com/leod1/PawnAppBadBack.git
cd PawnAppBadBack
docker compose -f docker-composeDB.yml up -d
# Attendez que la base de données MongoDB soit entièrement opérationnelle avant de continuer
docker compose up -d --build
cd ../PawnAppBadFront
docker compose up -d --build```