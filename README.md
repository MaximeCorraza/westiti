# Westiti 📸

**Westiti** est une application web de gestion et de partage de photos d'événements. Elle permet aux utilisateurs de créer des événements, d'inviter des participants et de partager des photos de manière collaborative.

## 🎯 Description du projet

Westiti est une plateforme qui facilite le partage de photos lors d'événements (mariages, anniversaires, soirées étudiantes, etc.). Les utilisateurs peuvent :
- Créer des événements avec des informations détaillées
- Rejoindre des événements via un code d'accès
- Téléverser et partager des photos
- Consulter les photos partagées par les autres participants

## 🏗️ Architecture

Le projet est composé de trois parties principales :

### 🔹 Frontend (App)
- **Framework** : React + TypeScript + Vite
- **Localisation** : `/App`
- Offre une interface utilisateur moderne et réactive
- Gestion des événements, photos et profils utilisateurs

### 🔹 Backend (API)
- **Framework** : NestJS (Node.js)
- **Localisation** : `/Api`
- API REST pour gérer la logique métier
- Authentification et autorisation des utilisateurs
- Gestion des uploads de fichiers

### 🔹 Base de données
- **SGBD** : PostgreSQL
- **ORM** : Prisma
- Stockage des utilisateurs, événements, participants et métadonnées des photos

### 🔹 Infrastructure
- **Containerisation** : Docker & Docker Compose
- **Reverse Proxy** : Traefik (avec certificats SSL automatiques)
- **Administration BDD** : Adminer

## 📊 Modèle de données

Le projet utilise les entités principales suivantes :

- **User** : Utilisateurs de l'application
- **Event** : Événements créés par les utilisateurs
- **UserEvent** : Table de liaison entre utilisateurs et événements (participants)
- **Photo** : Photos téléversées dans les événements
- **EventType** : Types d'événements (Mariage, Anniversaire, Soirée étudiante, Autres)

## ✨ Fonctionnalités principales

### Pour les visiteurs
- ✅ Créer un compte
- ✅ Se connecter avec email/mot de passe

### Pour les utilisateurs connectés
- ✅ Créer un événement avec des détails (nom, description, dates, adresse, type)
- ✅ Accéder à un événement via un code d'accès
- ✅ Consulter le tableau de bord avec tous ses événements
- ✅ Téléverser des photos dans un événement
- ✅ Voir les photos téléversées
- ✅ Quitter un événement
- ✅ Supprimer son compte

## 🚀 Installation et démarrage

### Prérequis

- **Docker** et **Docker Compose** installés sur votre machine
  - Installation : https://docs.docker.com/engine/install/
- **Node.js** (version 16 ou supérieure)
- **npm** ou **yarn**

### 1. Cloner le projet

```bash
git clone git@github.com:MaximeCorraza/westiti.git
cd westiti
```

### 2. Configuration des variables d'environnement

Copier le fichier `.env.exemple` en `.env` et remplir les valeurs :

```bash
cp .env.exemple .env
```

Éditer le fichier `.env` avec vos propres valeurs :
- `POSTGRES_USER` : Nom d'utilisateur PostgreSQL
- `POSTGRES_PASSWORD` : Mot de passe PostgreSQL
- `POSTGRES_DB` : Nom de la base de données
- `DATABASE_URL` : URL de connexion à la base de données
- `VITE_API_URL` : URL de l'API
- Autres variables pour le déploiement (VPS, domaine, etc.)

### 3. Installation des dépendances

#### Frontend
```bash
cd App
npm install
cd ..
```

#### Backend
```bash
cd Api
npm install
cd ..
```

### 4. Démarrer le projet avec Docker

#### Pour Windows

```bash
docker compose build
docker compose up -d
cd Api
npm run prisma
```

#### Pour Linux et macOS

```bash
sudo docker compose build
sudo docker compose up -d
cd Api
npm run prisma
```

La commande `npm run prisma` initialise la base de données avec les migrations et les données de seed si configurées.

### 5. Accéder à l'application

Une fois le projet démarré, accéder aux services suivants :

- **Frontend** : http://localhost:5173 ou http://app-westiti.localhost
- **Backend/API** : http://localhost:3000 ou http://api-westiti.localhost
- **Adminer** : http://localhost:8081 ou http://adminer-westiti.localhost
- **Traefik Dashboard** : http://localhost:8080

## 🛠️ Développement

### Scripts disponibles

À la racine du projet :
```bash
# Redémarrer complètement Docker (rebuild + migrations + seed)
npm run docker:restart
```

Dans le dossier `App` (Frontend) :
```bash
npm run dev          # Démarrer en mode développement
npm run build        # Builder pour la production
npm run preview      # Prévisualiser le build de production
npm run lint         # Linter le code
npm run test         # Lancer les tests
```

Dans le dossier `Api` (Backend) :
```bash
npm run start        # Démarrer en mode production
npm run start:dev    # Démarrer en mode développement (watch)
npm run start:debug  # Démarrer en mode debug
npm run test         # Lancer les tests unitaires
npm run test:e2e     # Lancer les tests end-to-end
npm run prisma       # Appliquer les migrations Prisma
```

## 📁 Structure du projet

```
westiti/
├── Api/                    # Backend NestJS
│   ├── src/               # Code source
│   ├── prisma/            # Schéma et migrations Prisma
│   └── ...
├── App/                    # Frontend React + Vite
│   ├── src/               # Code source
│   │   ├── Components/    # Composants React
│   │   ├── Pages/         # Pages de l'application
│   │   ├── Hooks/         # Hooks personnalisés
│   │   └── ...
│   └── ...
├── Instructions/          # Documentation de mise en route
├── traefik/              # Configuration Traefik
├── docker-compose.yml    # Configuration Docker
├── erd.puml             # Diagramme de cas d'usage
└── README.md            # Ce fichier
```

## 🔒 Sécurité

- Authentification par JWT
- Hachage des mots de passe
- Validation des entrées utilisateur
- Gestion des autorisations pour l'upload de fichiers
- HTTPS automatique avec certificats Let's Encrypt (via Traefik)

## 🤝 Contributeurs

Ce projet a été développé dans le cadre d'une application de gestion de photos collaborative.

## 📝 Licence

Ce projet est sous licence privée. Tous droits réservés.

## 📞 Support

Pour toute question ou problème, veuillez créer une issue sur le dépôt GitHub.

---

**Bon partage de photos avec Westiti ! 📸✨**
