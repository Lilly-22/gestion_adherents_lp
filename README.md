# Gestion des Adhérents - LyonPalme

![readme_logo__1_](https://github.com/user-attachments/assets/841f5181-8b7b-4d87-8a26-13521fc9b991)



## Sommaire

- [Description](#description)
- [Technologies Utilisées](#technologies-utilisées)
- [Diagramme de cas d'utilisation](#utilisation)
- [Diagramme de classe](#diagramme-de-classe)
- [Prérequis](#prérequis)
- [Installation](#installation)
- [Créer le premier user](#créer-le-premier-user)
- [Utilisation](#utilisation)

## Description
Le club "LyonPalme" est une association sportive de natation avec palmes : monopalme ou bi-palmes. Il compte une quarantaine d'adhérents et son siège est à Saint-Fons. L'application de gestion des adhérents permet de gérer les comptes des membres du club. Ce site est destiné aux secrétaires du club dans un premier temps qui pourrons se connecter à l’application, visualiser les adhérents inscrits, procéder à l’inscription des nouveaux adhérents et archiver les anciens adhérents. Dans un second temps, l’application permet aux nageurs connectés au site d’afficher le trombinoscope (avec la photo, nom et prénom de l’adhérent ainsi que son statut) pour la saison en cours, ainsi que l’annuaire. Il pourra modifier son compte ainsi que son mot de passe.

## Technologies Utilisées


| **Nom** | **Description** |
| ------- | ------------- |
| ![Laravel](https://img.shields.io/badge/laravel-%23FF2D20.svg?style=for-the-badge&logo=laravel&logoColor=white) | Framework. |
| ![Debian](https://img.shields.io/badge/Debian-D70A53?style=for-the-badge&logo=debian&logoColor=white) | Linux. |
| ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) | Utilisation de NodeJS pour NPM. |
| ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) | Contrôle de version. |
| ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white) | Language de code. |
| ![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white)| Système de gestion de base de données. |
| ![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white) | Serveur

## Diagramme de cas d'utilisation

<img width="787" alt="Diagramme de cas GA" src="https://github.com/user-attachments/assets/15d6cc95-7b00-472b-b621-21851dd7a301" />


## Diagramme de classe

<img width="897" alt="Capture d’écran 2025-06-08 à 21 26 48" src="https://github.com/user-attachments/assets/d265871a-6bee-4738-8bea-b29c70890bcf" />


## Prérequis
Pour exécuter ce projet, vous devez avoir Debian, Apache2, Mariadb, Laravel, NodeJS et Git.

## Installation

Tout d'abord, vous devez cloner le projet :

 ```bash
   git clone https://github.com/Lilly-22/gestion_adherent.git
   cd gestion_adherent
   ```

Puis vous devez vous placer dans le projet et accorder les droits à deux fichiers en utilisant les commandes ci-dessous. Assurez-vous de remplacer "votreusername" par votre nom d'utilisateur sur votre machine :

```xml
sudo chown -R votreusername:www-data bootstrap/cache/
sudo chown -R votreusername:www-data storage
sudo chmod -R 755 bootstrap/cache/
sudo chmod -R 755 storage/
```


Après cela, vous devrez exécuter les commandes : 
```xml
composer install
npm install
npm run build
npm run dev
```

Ensuite, copiez l'exemple de fichier .env et collez-le dans le même emplacement où il est situé, puis remplissez-le comme indiqué ci-dessous :

<img width="409" alt="Capture d’écran 2025-06-09 à 22 55 17" src="https://github.com/user-attachments/assets/519fda99-6a64-4e74-8966-1dd8af2611b6" />

**Générer la clé d’application**
   ```bash
   php artisan key:generate
   ```
**installer artisan si vous ne l'avez pas**
   ```
php artisan migrate:install
   ```
**Pour exécuter les migrations**

 ```
php artisan migrate
   ```




## Créer le premier user
Une fois la nouvelle database crée sur mariadb :

 ```xml
sudo mysql
```
1) Création de la base de données

 ```xml
 CREATE DATABASE IF NOT EXISTS `inscription_club2`

   CHARACTER SET utf8mb4

   COLLATE utf8mb4_unicode_ci;
```
Pour utiliser la base de donée inscription_club2 :
 ```xml
 use inscription_club2
 ```
2) Suppression préalable de l'utilisateur (sécurité)
```xml
 DROP USER IF EXISTS 'inscrip_user'@'localhost';
 ```
 
3) Création de l’utilisateur sur localhost
```xml
 CREATE USER 'inscrip_user'@'localhost'
   IDENTIFIED BY 'ChangezCeMotDePasse123s!';
 ```
4) Attribution des droits CRUD seulement
```xml
 GRANT SELECT, INSERT, UPDATE, DELETE
   ON `inscription_club2`.*
   TO 'inscrip_user'@'localhost';
``` 
5) Prise en compte immédiate des changements
```xml
 FLUSH PRIVILEGES;
```

## Utilisation
