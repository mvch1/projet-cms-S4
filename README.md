# 🎓 projet-cms-S4 — Site Universitaire

Plateforme web universitaire basée sur **Plone CMS**, conçue pour centraliser l'information académique et la vie du campus en un seul endroit.

`projet-cms-S4` permet aux étudiants et au personnel administratif de consulter les cursus universitaires, suivre les résultats des étudiants et rester informés des événements organisés par l'université.

Le site s'appuie sur un backend **Plone/Zope** exposé via **plone.restapi**, ce qui permet de construire une interface moderne tout en profitant de la gestion de contenu, de la sécurité et des workflows éprouvés de Plone.

## 🔗 Dépôt

Repository : [mvch1/projet-cms-S4](https://github.com/mvch1/projet-cms-S4)

## Vue d'ensemble

| Icône | Domaine | Rôle |
|------|---------|------|
| 📖 | Cursus | Présenter les filières, programmes et contenus pédagogiques. |
| 📊 | Résultats | Gérer et publier les résultats des étudiants. |
| 📅 | Événements | Publier et organiser les événements universitaires (conférences, examens, activités). |
| 🔐 | Sécurité | Authentification et gestion des rôles via Plone (admin, enseignant, étudiant). |
| 🌐 | API | Exposer le contenu via une API REST (plone.restapi) pour un frontend découplé. |

## Architecture

```
                     🌐 Navigateur / Client
                              |
                              v
                 🖥️ Frontend (Node.js / Yarn)
                              |
                              v  (REST API)
                 ⚙️ Backend Plone / Zope
                    - Gestion de contenu
                    - Utilisateurs & rôles
                    - Workflows
                              |
                              v
                     🗄️ ZODB (base de données)
```

## ✨ Fonctionnalités principales

### 📖 Cursus universitaires
- Présentation des filières et programmes de formation.
- Description détaillée des matières et parcours pédagogiques.
- Organisation du contenu par département / niveau d'étude.

### 📊 Résultats des étudiants
- Saisie et gestion des résultats par les administrateurs/enseignants.
- Consultation des résultats par les étudiants concernés.
- Historique et suivi des résultats au fil des semestres.

### 📅 Événements universitaires
- Publication d'événements (conférences, journées portes ouvertes, examens, activités associatives).
- Calendrier des événements à venir.
- Gestion des annonces et actualités du campus.

### 🔐 Gestion des accès
- Authentification des utilisateurs.
- Rôles différenciés (administrateur, enseignant, étudiant, visiteur).
- Workflows de publication/validation de contenu propres à Plone.

## 🛠️ Technologies utilisées

| Catégorie | Outils |
|-----------|--------|
| CMS / Backend | [Plone](https://plone.org/) (basé sur [Zope](https://zope.org/)) |
| Langage | Python 3.13 |
| API | [plone.restapi](https://plonerestapi.readthedocs.io/) |
| Traitement d'images | Pillow |
| Frontend | Node.js, Yarn (ex. Volto — frontend React officiel de Plone) |
| Génération de projet | Cookiecutter (`cookiecutter-zope-instance`) |
| Base de données | ZODB (base objet native de Zope), avec support ZEO pour le partage de stockage entre instances |
| Environnement | Environnement virtuel Python (`venv`) |

## 🚀 Instructions d'installation

### Prérequis

- Python 3.13+
- Node.js et Yarn (pour le frontend)
- Git

### 1. Cloner le dépôt

```bash
git clone https://github.com/mvch1/projet-cms-S4.git
cd projet-cms-S4
```

### 2. Créer et activer l'environnement virtuel Python

```bash
python -m venv outilweb
# Windows
outilweb\Scripts\activate
# macOS / Linux
source outilweb/bin/activate
```

### 3. Installer les dépendances du backend

```bash
pip install "plone.restapi[recommended]" Zope Pillow
```

- **plone.restapi** : expose le contenu Plone via une API REST.
- **Zope** : le framework applicatif sur lequel repose Plone.
- **Pillow** : gestion et manipulation des images.

### 4. Générer l'instance backend avec Cookiecutter

```bash
pip install cookiecutter
cookiecutter gh:plone/cookiecutter-zope-instance
```

Cette commande génère le squelette du projet backend (fichiers de configuration, `instance/`, etc.).

### 5. Démarrer le backend

```bash
cd instance
runwsgi etc/zope.ini
```

Le backend est alors accessible sur `http://localhost:8080`.

### 6. Installer et démarrer le frontend

```bash
cd ../frontend
yarn install
yarn start
```

Le site est alors accessible sur `http://localhost:3000`.

## 📁 Structure du projet

```
.
|-- outilweb/            # Environnement virtuel Python + instance Plone/Zope
|   `-- instance/        # Instance backend générée (config, données)
|-- mon_env/             # Environnement virtuel Python additionnel
|-- plone.txt            # Notes techniques sur les outils utilisés
`-- README.md            # Présentation du projet
```

## 📝 Notes de développement

- Ne pas committer les environnements virtuels (`outilweb`, `mon_env`), les secrets ou les fichiers de configuration sensibles.
- Utiliser des comptes de test dédiés avant de manipuler des données réelles d'étudiants.
- Se référer à `plone.txt` pour le détail des outils (Node.js, Yarn, Cookiecutter, ZEO).

## 📌 État actuel

Le projet est en phase de mise en place de l'infrastructure Plone/Zope (backend). Les modules fonctionnels — cursus, résultats des étudiants et événements — sont les prochaines étapes de développement.
