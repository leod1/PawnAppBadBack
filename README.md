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
docker compose up -d --build
```

## Vulnerability

### SQL Injection

Cette application présente une vulnérabilité d'injection SQL qui peut être exploitée pour manipuler ou accéder illégalement à des données dans la base de données. L'injection SQL peut être testée en insérant des chaînes malveillantes dans les entrées utilisateur qui interagissent avec les requêtes SQL.

#### Test de l'injection SQL

Pour tester cette vulnérabilité, vous pouvez essayer d'injecter le payload suivant dans les champs d'utilisateur : " || "1"=="1" || "

Ce payload tente de modifier la logique de la requête SQL pour retourner toujours vrai, ce qui peut être utilisé pour contourner les authentifications ou extraire des informations sensibles de la base de données.

### Brute Force Attack

La méthode de Brute Force est également une vulnérabilité de cette application, permettant aux attaquants de tenter un grand nombre de combinaisons de noms d'utilisateur et de mots de passe jusqu'à ce qu'ils réussissent à obtenir un accès. Cette attaque exploite les systèmes qui n'implémentent pas de mesures de sécurité adéquates comme les limites de tentatives de connexion ou les délais d'attente.
