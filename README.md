# 📇 MyContact - Gestionnaire de Contacts

**MyContact** est une application fullstack de gestion de contacts permettant de **créer**, **consulter**, **modifier** et **supprimer** des contacts personnels.

---

## 📋 Table des matières
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Démarrage](#-démarrage)
- [Tests](#-tests)
- [API Endpoints](#-api-endpoints)
- [Structure du projet](#-structure-du-projet)
- [Notes](#-notes)

---

## 🔧 Prérequis

- Node.js (v14+)
- MongoDB
- NPM ou Yarn

---

## 💻 Installation

```bash
# Cloner le dépôt
git clone https://github.com/AV-13/MyContact.git
cd MyContact

# Installer les dépendances du serveur
cd server
npm install

# Installer les dépendances du client
cd ../client
npm install
```

---

## ⚙️ Configuration

### Configuration du serveur

Créez un fichier `.env` dans le répertoire `/server` :

```bash
PORT=5000
MONGO_URI=mongodb://localhost:27017/mycontact
JWT_SECRET=votre_secret_jwt
```

---

## 🚀 Démarrage

### Démarrer le serveur

```bash
cd server
npm run dev
```
Le serveur démarrera sur [http://localhost:5000](http://localhost:5000) par défaut.

### Démarrer le client

```bash
cd client
npm start
```
L'application client sera accessible sur [http://localhost:3000](http://localhost:3000).

---

## 🧪 Tests

### Exécuter les tests du serveur

```bash
cd server
npm test
```

### Exécuter les tests avec couverture

```bash
cd server
npx jest --coverage
```

---

## 📡 API Endpoints

> Toutes les routes nécessitent une authentification JWT (**sauf login/register**).

### 🔐 Authentification

#### POST `/api/auth/register`
Créer un nouveau compte  
**Body :**
```json
{ "nom": "", "prenom": "", "email": "", "password": "", "telephone": "" }
```

#### POST `/api/auth/login`
Se connecter  
**Body :**
```json
{ "email": "", "password": "" }
```

---

### 👥 Contacts

#### GET `/api/contacts/all`
Récupérer tous les contacts de l'utilisateur  
**Headers :**
```
Authorization: Bearer token
```

#### GET `/api/contacts/getContact/:id`
Récupérer un contact par ID  
**Headers :**
```
Authorization: Bearer token
```
**Params :** `id` (ID du contact)

#### POST `/api/contacts/create`
Créer un nouveau contact  
**Headers :**
```
Authorization: Bearer token
```
**Body :**
```json
{ "nom": "", "prenom": "", "telephone": "", "email": "", "adresse": "" }
```

#### PATCH `/api/contacts/update`
Mettre à jour un contact  
**Headers :**
```
Authorization: Bearer token
```
**Body :**
```json
{ "_id": "", "nom": "", "prenom": "", "telephone": "", "email": "", "adresse": "" }
```

#### DELETE `/api/contacts/delete/:contactId`
Supprimer un contact  
**Headers :**
```
Authorization: Bearer token
```
**Params :** `contactId` (ID du contact)

---

## 📁 Structure du projet

```
MyContact/
├── client/                 # Frontend React
│   ├── public/             # Fichiers statiques
│   ├── src/                # Code source React
│   │   ├── components/     # Composants React
│   │   ├── pages/          # Pages de l'application
│   │   ├── services/       # Services API
│   │   └── App.jsx         # Composant principal
│   └── package.json        # Dépendances frontend
│
└── server/                 # Backend Node.js/Express
    ├── controllers/        # Contrôleurs
    ├── middleware/         # Middlewares (auth, validation)
    ├── model/              # Modèles MongoDB
    ├── routes/             # Définition des routes API
    ├── services/           # Services métier
    ├── __tests__/          # Tests
    ├── server.js           # Point d'entrée du serveur
    └── package.json        # Dépendances backend
```

---

## 📝 Notes

- N'oubliez pas d'avoir une instance **MongoDB** en cours d'exécution.
- Pour les environnements de production, utilisez des **variables d'environnement sécurisées**.
- La documentation complète de l'API est disponible dans `/server/docs`.

---

© 2025 | Développé par **AV-13**
