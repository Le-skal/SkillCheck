<div align="center">

# QCM Engine PHP
### *Système de Questionnaire Interactif et Gestion de Résultats*

<p><em>Évaluez vos connaissances, suivez vos scores et gérez vos questions en toute simplicité.</em></p>

![Status](https://img.shields.io/badge/status-operational-success?style=flat)
![Version](https://img.shields.io/badge/version-1.0-blue?style=flat)
![License](https://img.shields.io/badge/license-MIT-green?style=flat)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat&logo=mysql&logoColor=white)

<p><em>Propulsé par les technologies web fondamentales :</em></p>

![PHP](https://img.shields.io/badge/PHP-7.4%2B-777BB4?style=flat&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-DB-4479A1?style=flat&logo=mysql&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?style=flat&logo=javascript&logoColor=black)

**Core Modules:**
![Auth](https://img.shields.io/badge/Auth-Session-orange?style=flat)
![Security](https://img.shields.io/badge/Security-Bcrypt-red?style=flat)
![Admin](https://img.shields.io/badge/Admin-Dashboard-lightgrey?style=flat)

---

### 🎓 Projet Académique - Développement Web
**Backend Development & Database Management** | PHP & MySQL Mastery

</div>

---

## 📋 Table des Matières

- [Objectif du Projet](#objectif-du-projet)
- [Fonctionnalités Implémentées](#fonctionnalités-implémentées)
- [Architecture Technique](#architecture-technique)
- [Modèle de Données (SQL)](#modèle-de-données-sql)
- [Installation et Configuration](#installation-et-configuration)
- [Sécurité et Bonnes Pratiques](#sécurité-et-bonnes-pratiques)
- [Structure du Projet](#structure-du-projet)

---

## 🎯 Objectif du Projet

L'objectif de ce projet est de fournir une plateforme complète de QCM (Questionnaire à Choix Multiples) permettant aux utilisateurs de s'inscrire, de passer des tests basés sur une sélection aléatoire de questions, et de consulter leur progression. Le projet inclut également une interface d'administration pour le suivi des performances globales des utilisateurs.

---

## ✨ Fonctionnalités Implémentées

### 1. Gestion des Utilisateurs
- **Inscription Sécurisée** : Création de compte avec hachage des mots de passe via `password_hash()`.
- **Connexion Authentifiée** : Système de session PHP pour sécuriser l'accès aux tests et résultats.
- **Profil Personnel** : Consultation de l'historique complet des scores et calcul automatique de la moyenne de l'utilisateur.

### 2. Moteur de QCM
- **Génération Aléatoire** : Sélection automatique de 10 questions aléatoires à chaque tentative.
- **Correction Instantanée** : Calcul du score final sur 20 points (chaque bonne réponse vaut 2 points).
- **Persistance des Données** : Sauvegarde automatique de la note, de l'ID utilisateur et de la date dans la base de données.

### 3. Administration (Back-office)
- **Monitoring** : Visualisation globale des noms d'utilisateurs, de leurs notes et des dates de passage.
- **Recherche Avancée** : Filtre dynamique permettant de rechercher les résultats d'un utilisateur spécifique par son nom.
- **Tri de Données** : Organisation des résultats par nom et par date pour une meilleure lisibilité.

---

## 🛠 Architecture Technique

### Stack Logicielle
- **Langage Serveur** : PHP.
- **Base de données** : MySQL.
- **Frontend** : HTML5 / CSS (Tableaux bordés, formulaires interactifs).

### Composants Clés
- **`connect.php`** : Centralise la connexion à la base de données `qcm` via `mysqli_connect()`.
- **Gestion de Session** : Utilisation de `session_start()` pour protéger l'intégrité des données utilisateur.
- **Algorithme de Scoring** : Parcours des réponses envoyées en POST et comparaison avec le champ `verite` de la table `reponses`.

---

## 🗄 Modèle de Données (SQL)

Le schéma de base de données (fourni dans `qcm.sql`) se compose de :

1.  **`utilisateurs`** : Gère l'identité (nom, email, mot de passe haché).
2.  **`questions`** : Stocke les libellés et les niveaux de difficulté.
3.  **`reponses`** : Contient les propositions de réponses liées par `idq` avec l'indicateur de validité.
4.  **`resultats`** : Archive les scores liés aux utilisateurs par une clé étrangère `utilisateur_id`.

---

## 🔐 Sécurité et Bonnes Pratiques

- **Protection des Mots de Passe** : Utilisation de l'algorithme `PASSWORD_DEFAULT` pour le hachage lors de l'inscription et `password_verify()` lors de la connexion.
- **Contrôle d'Accès** : Vérification systématique de l'existence d'une session `utilisateur_id` avant d'afficher des résultats personnels ou d'enregistrer un score.
- **Prévention XSS** : Utilisation de `htmlspecialchars()` lors de l'affichage des noms et des entrées utilisateurs dans le panneau admin.

---

## 🚀 Installation et Configuration

1. **Base de données** : 
   - Créez une base nommée `qcm`.
   - Importez le fichier `qcm.sql` pour générer les tables et les 40 questions par défaut.
2. **Configuration** : 
   - Ajustez les paramètres de connexion (host, user, password) dans le fichier `connect.php`.
3. **Serveur** : 
   - Déployez le projet sur un serveur compatible PHP (WAMP, XAMPP, Laragon).
   - Accédez à `inscription.php` pour créer votre premier compte utilisateur.

---

## 📂 Structure du Projet

```text
QCM-Project/
├── admin.php               # Interface de recherche et suivi administratif
├── connect.php             # Script de connexion MySQL centralisé
├── connexion.php           # Interface de login (Sessions)
├── inscription.php         # Enregistrement des nouveaux utilisateurs
├── listeQuestions.php      # Moteur de génération du questionnaire (10 questions)
├── qcm.sql                 # Script SQL complet (Structure + Data)
├── resultat.php            # Calcul, affichage et sauvegarde du score
└── resultats_utilisateur.php # Historique personnel et moyenne des scores
