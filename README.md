# 📄 README – Authentification OAuth2 / OpenID Connect avec Spring Boot
🎯 Objectif du projet

Ce projet a pour but d’intégrer un système d’authentification moderne dans une application Spring Boot en s’appuyant sur un fournisseur d’identité externe (Google ou Keycloak) via les protocoles OAuth2 et OpenID Connect (OIDC).

Il montre comment :

Déléguer l’authentification à un Identity Provider (IdP)

Utiliser le flux OAuth2 Authorization Code

Obtenir et valider un Access Token et un ID Token

Extraire les informations du profil utilisateur

Protéger des routes avec Spring Security

Mettre en place une redirection automatique lors du login

# 🔐 Concepts clés
OAuth2

→ Sert à autoriser l’accès à une ressource protégée.
Token principal : Access Token

OpenID Connect (OIDC)

→ Extension de OAuth2 pour authentifier un utilisateur.
Token principal : ID Token (JWT) contenant identité + claims.

Spring Security gère automatiquement les deux couches grâce à spring-security-oauth2-client.

🛠️ Technologies utilisées

Spring Boot (Web, Security, OAuth2 Client)

Thymeleaf (vues)

Google Identity (OAuth2 / OIDC)

Keycloak (Variante locale)

Maven

Java 17+ recommandé

# 📁 Fonctionnalités de l'application
1️⃣ Authentification via Google OAuth2

Redirection automatique vers Google

Récupération des informations du compte (nom, email, photo)

Protection des routes sécurisées

Déconnexion propre (invalidation de session)

2️⃣ Intégration avec Keycloak (optionnelle)

Possibilité d’utiliser son propre serveur Keycloak

Gestion locale des utilisateurs et rôles

Issuer-uri configurable

3️⃣ Pages disponibles

/ → Accueil (non protégée)

/profile → Profil utilisateur (protégée)

/logout → Déconnexion

# 🔧 Configuration Google Cloud

Créer un projet sur
👉 https://console.cloud.google.com

Activer Google Identity Services

Créer un Client OAuth 2.0 → Application Web

Ajouter l’URL de redirection :

http://localhost:8080/login/oauth2/code/google


Récupérer :

Client ID

Client Secret

Ces valeurs doivent être ajoutées dans application.yml.
<img width="1366" height="728" alt="Créer un ID client OAuth – Google Auth Platform – My Project – Console Google Cloud - Google Chrome 28_11_2025 21_39_16" src="https://github.com/user-attachments/assets/6632118a-98a9-445a-a42c-e47da5772d66" />

<img width="1366" height="728" alt="Créer un ID client OAuth – Google Auth Platform – My Project – Console Google Cloud - Google Chrome 28_11_2025 21_50_40" src="https://github.com/user-attachments/assets/b400df6f-fa50-4fdf-96d0-bac2354774f6" />
🔧 Configuration Spring Boot

L'application nécessite :

Configuration du client OAuth2 (ID, secret, scope)

Déclaration de l’issuer Google

Activation de oauth2Login() dans la configuration Spring Security

Protection des routes sécurisées

Les vues permettent d'afficher :

Le nom de l’utilisateur

L’adresse email

La photo de profil

# 🧪 Comment tester l’application

Lancer l'application Spring Boot

Aller sur :

http://localhost:8080/profile


Vous êtes automatiquement redirigé vers la page de connexion Google

Après connexion :

Le profil utilisateur s’affiche

Les informations sont extraites du ID Token

<img width="1366" height="728" alt="Connexion _ comptes Google - Google Chrome 28_11_2025 22_43_34" src="https://github.com/user-attachments/assets/fd6ccc14-9179-4864-b9e0-b4694744a0a7" />
<img width="1366" height="728" alt="Connexion _ comptes Google - Google Chrome 28_11_2025 22_47_24" src="https://github.com/user-attachments/assets/d08c7287-5366-407e-9215-86c4d65830dc" />
