---
title: Emplacement de stockage de session
description: Découvrez où les fichiers de session sont stockés.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Emplacement de stockage de session

Cette rubrique explique comment localiser vos fichiers de session. Le système utilise la logique suivante pour stocker les fichiers de session :

- Si vous avez configuré la mémoire mise en cache, les sessions sont stockées dans la mémoire vive. Voir [Utiliser la mémoire mise en cache pour le stockage de session](memcached.md).
- Si vous avez configuré Redis, les sessions sont stockées sur le serveur Redis ; voir [Utiliser Redis pour le stockage de session](../cache/redis-session.md).
- Si vous utilisez le stockage de session basé sur les fichiers par défaut, nous stockons les sessions aux emplacements suivants dans l’ordre indiqué :

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

L’exemple précédent stocke des fichiers de session dans `/var/www/session`.

## Exemple dans `php.ini`

En tant qu’utilisateur disposant des privilèges `root`, ouvrez votre fichier `php.ini` et recherchez la valeur `session.save_path`. Cela identifie l’emplacement de stockage des sessions.

## Gestion de la taille de session

Voir la [gestion des sessions](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-session-management) dans le _guide de l’utilisateur_.

## Configuration du nettoyage de la mémoire

Pour nettoyer les sessions expirées, le système appelle le gestionnaire `gc` (_nettoyage de la mémoire_) de manière aléatoire selon une probabilité calculée par la directive `gc_probability / gc_divisor`. Par exemple, si vous définissez ces directives sur `1/100`, cela signifie une probabilité de `1%` (_probabilité d’un appel de nettoyage de la mémoire pour 100 requêtes_).

Le gestionnaire de nettoyage de la mémoire utilise la directive `gc_maxlifetime` : le nombre de secondes après lesquelles les sessions sont vues comme _la mémoire_ et potentiellement nettoyées.

Sur certains systèmes d&#39;exploitation (Debian/Ubuntu), la directive `session.gc_probability` par défaut est `0`, ce qui empêche l&#39;exécution du gestionnaire de nettoyage de la mémoire.

Vous pouvez remplacer les directives `session.gc_` du fichier `php.ini` dans le fichier `<magento_root>/app/etc/env.php` :

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configuration varie en fonction du trafic et des besoins spécifiques du site web du commerçant.
