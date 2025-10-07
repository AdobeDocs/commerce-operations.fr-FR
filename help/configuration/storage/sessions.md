---
title: Emplacement de stockage de la session
description: Découvrez les emplacements de stockage de session et la gestion des fichiers dans Adobe Commerce. Découvrez la logique de stockage et les options de configuration.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Emplacement de stockage de la session

Cette rubrique explique comment localiser l’emplacement de stockage de vos fichiers de session. Le système utilise la logique suivante pour stocker les fichiers de session :

- Si vous avez configuré memcached, les sessions sont stockées dans la RAM ; voir [Utiliser memcached pour le stockage des sessions](memcached.md).
- Si vous avez configuré Redis, les sessions sont stockées sur le serveur Redis ; voir [Utiliser Redis pour le stockage de session](../cache/redis-session.md).
- Si vous utilisez l’espace de stockage de session basé sur des fichiers par défaut, les sessions sont stockées aux emplacements suivants dans l’ordre indiqué :

   1. Répertoire défini dans [`env.php`](#example-in-envphp)
   1. Répertoire défini dans [`php.ini`](#example-in-phpini)
   1. répertoire `<magento_root>/var/session`

## Exemple dans `env.php`

Voici un exemple de fragment de code provenant de `<magento_root>/app/etc/env.php` :

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

L’exemple précédent stocke les fichiers de session dans `/var/www/session`

## Exemple dans `php.ini`

En tant qu’utilisateur disposant de droits d’`root`, ouvrez votre fichier `php.ini` et recherchez la valeur de `session.save_path`. Cela identifie l’emplacement de stockage des sessions.

## Gérer la taille de session

Voir la [Gestion des sessions](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-session-management) dans le _Guide de l’utilisateur_.

## Configuration du nettoyage de la mémoire

Pour nettoyer les sessions expirées, le système appelle le gestionnaire `gc` (_nettoyage de la mémoire_) de manière aléatoire en fonction d’une probabilité calculée par la directive `gc_probability / gc_divisor`. Par exemple, si vous définissez ces directives sur `1/100` respectivement, cela signifie une probabilité de `1%` (_probabilité d’un appel de nettoyage pour 100 requêtes_).

Le gestionnaire de récupération de l’espace mémoire utilise la directive `gc_maxlifetime`, à savoir le nombre de secondes après lesquelles les sessions sont vues comme _espace mémoire_ et potentiellement nettoyées.

Sur certains systèmes d’exploitation (Debian/Ubuntu), la directive `session.gc_probability` par défaut est `0`, ce qui empêche le gestionnaire de récupération de l’espace mémoire de s’exécuter.

Vous pouvez remplacer les directives `session.gc_` à partir du fichier `php.ini` dans le fichier `<magento_root>/app/etc/env.php` :

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configuration varie en fonction du trafic et des besoins spécifiques du site web du commerçant.
