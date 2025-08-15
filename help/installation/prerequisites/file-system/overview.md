---
title: Propriété et autorisations des fichiers
description: Découvrez l’importance des autorisations de système de fichiers lors de l’utilisation d’installations sur site d’Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Propriété et autorisations des fichiers

Il est important de sécuriser votre installation Adobe Commerce dans un environnement de développement afin d’éviter tout problème lié à l’accès de votre système à des personnes ou processus non autorisés, ainsi que tout risque potentiel d’endommagement de votre système. Appliquez les règles suivantes relatives aux droits d&#39;accès et de propriété du système de fichiers pour protéger votre installation.

## Propriétaire du système de fichiers

Le propriétaire du système de fichiers est un utilisateur qui possède et détient des autorisations d’écriture sur les fichiers du système de fichiers.

Il existe deux types de propriétaires de système de fichiers :

- **Hébergement partagé avec un seul utilisateur**

  Les fournisseurs d’hébergement partagés vous permettent de vous connecter au serveur d’applications en tant qu’utilisateur unique. En tant qu’utilisateur unique, vous pouvez vous connecter, transférer des fichiers par FTP et exécuter le serveur web. Vous avez la possibilité de définir un [`umask`](#restrict-access-with-a-umask) pour restreindre davantage l’accès, en particulier dans un environnement de production.

- **Hébergement privé avec deux utilisateurs**

  L’hébergement privé est utile si vous gérez un serveur d’applications. Chaque utilisateur a une responsabilité spécifique :

   - L’_utilisateur du serveur web_ exécute l’administration et le storefront.

   - Le _utilisateur de ligne de commande_ exécute les tâches cron et les utilitaires de ligne de commande.

  Les deux utilisateurs requièrent les mêmes autorisations pour le système de fichiers. Il est donc préférable d’utiliser un [groupe partagé](configure-permissions.md#set-ownership-and-permissions-for-two-users) et de définir un [`umask`](#restrict-access-with-a-umask).

### Restreindre l’accès avec un masque

Pour renforcer la sécurité, en particulier dans un environnement de production sur un système d’hébergement partagé, vous pouvez utiliser `umask` pour restreindre l’accès. Un `umask`, également appelé masque de création de système de fichiers _file system creation mask_, est un ensemble de bits qui contrôle la manière dont les autorisations de fichier sont définies pour les fichiers nouvellement créés.

>[!WARNING]
>
>La sécurité du système de fichiers est complexe et importante. Nous vous recommandons vivement de consulter un administrateur système ou un administrateur réseau expérimenté avant de décider du niveau d’autorisations à définir. Nous fournissons un mécanisme que vous pouvez utiliser, mais la création d’une stratégie d’autorisations relève de votre responsabilité.

Adobe Commerce utilise un masque par défaut de trois bits : `002`. Soustrayez le masque par défaut des valeurs par défaut UNIX de 666 pour les fichiers et 777 pour les répertoires.

Par exemple :

- **775 pour les répertoires** : contrôle complet par l&#39;utilisateur, contrôle complet par le groupe et permet à tous de parcourir le répertoire. Ces autorisations sont généralement requises par les fournisseurs d’hébergement partagés.

- **664 pour les fichiers** : modifiable par l&#39;utilisateur, modifiable par le groupe et en lecture seule pour tous les autres utilisateurs.

Pour plus d’informations sur la création d’un fichier `magento_umask`, voir [Définir un masque](../../next-steps/set-umask.md).

## Autorisations, propriété et modes d’application

Nous vous recommandons de définir des autorisations et des propriétaires différents lorsque vous utilisez les différents modes d’application d’Adobe Commerce :

- Par défaut
- Développeur
- Production

Voir [À propos des modes](../../../configuration/bootstrap/application-modes.md) dans le _Guide de configuration_.

Nous discuterons plus en détail des recommandations d’autorisations dans [Autorisations d’accès aux systèmes de fichiers](../../../configuration/deployment/file-system-permissions.md) dans le _Guide de configuration_.

>[!TIP]
>
>Avant d’installer Adobe Commerce, consultez [Configuration de la propriété et des autorisations des fichiers](configure-permissions.md).
