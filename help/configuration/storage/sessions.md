---
title: Emplacement de stockage de session
description: Découvrez où les fichiers de session sont stockés.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Emplacement de stockage de session

Cette rubrique explique comment localiser vos fichiers de session. Le système utilise la logique suivante pour stocker les fichiers de session :

- Si vous avez configuré la mémoire mise en cache, les sessions sont stockées dans la mémoire RAM. Voir [Utiliser la mémoire mise en cache pour le stockage de session](memcached.md).
- Si vous avez configuré Redis, les sessions sont stockées sur le serveur Redis ; voir [Utilisation de Redis pour le stockage de session](../cache/redis-session.md).
- Si vous utilisez le stockage de session basé sur les fichiers par défaut, nous stockons les sessions aux emplacements suivants dans l’ordre indiqué :

   1. Répertoire défini dans [`env.php`](#example-in-envphp)
   1. Répertoire défini dans [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Exemple dans `env.php`

Un exemple de fragment de code de `<magento_root>/app/etc/env.php` suit :

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

L’exemple précédent stocke des fichiers de session dans `/var/www/session`

## Exemple dans `php.ini`

En tant qu’utilisateur avec `root` privilèges, ouvrez votre `php.ini` et recherchez la valeur de `session.save_path`. Cela identifie l’emplacement de stockage des sessions.

## Gestion de la taille de session

Voir [Gestion des sessions](https://docs.magento.com/user-guide/stores/security-session-management.html) dans le _Guide de l’utilisateur_.

## Configuration du nettoyage de la mémoire

Pour nettoyer les sessions expirées, le système appelle la variable `gc` (_nettoyage_), selon une probabilité calculée par la variable `gc_probability / gc_divisor` de . Par exemple, si vous définissez ces directives sur `1/100` cela signifie une probabilité de `1%` (_probabilité d’un appel de nettoyage de la mémoire pour 100 demandes_).

Le gestionnaire de nettoyage de la mémoire utilise la variable `gc_maxlifetime` directive : nombre de secondes après lesquelles les sessions sont vues comme _ordures_ et potentiellement nettoyé.

Sur certains systèmes d&#39;exploitation (Debian/Ubuntu), la valeur par défaut `session.gc_probability` est `0`, qui empêche l’exécution du gestionnaire de nettoyage de la mémoire.

Vous pouvez remplacer la variable `session.gc_` des directives `php.ini` dans le fichier `<magento_root>/app/etc/env.php` fichier :

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configuration varie en fonction du trafic et des besoins spécifiques du site web du commerçant.
