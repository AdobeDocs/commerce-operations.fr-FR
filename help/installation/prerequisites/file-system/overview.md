---
title: Propriété de fichier et autorisations
description: Découvrez l’importance des autorisations du système de fichiers lors de l’utilisation d’installations sur site d’Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Propriété de fichier et autorisations

Il est important de sécuriser votre installation d’Adobe Commerce dans un environnement de développement afin de vous aider à prévenir les problèmes liés à des personnes ou à des processus non autorisés qui accèdent à votre système et peuvent le endommager. Pour protéger votre installation, appliquez les directives suivantes concernant la propriété et les autorisations du système de fichiers.

## Propriétaire du système de fichiers

Le propriétaire du système de fichiers est un utilisateur qui possède et détient des autorisations d’écriture sur les fichiers du système de fichiers.

Il existe deux types de propriétaires de système de fichiers :

- **Hébergement partagé avec un seul utilisateur**

  Les fournisseurs d’hébergement partagés vous permettent de vous connecter au serveur d’applications en tant qu’utilisateur unique. En tant qu’utilisateur unique, vous pouvez vous connecter, transférer des fichiers par FTP et exécuter le serveur web. Vous avez la possibilité de définir une [`umask`](#restrict-access-with-a-umask) afin de restreindre davantage l&#39;accès, notamment dans un environnement de production.

- **Hébergement privé avec deux utilisateurs**

  L’hébergement privé est utile si vous gérez un serveur d’applications. Chaque utilisateur a une responsabilité spécifique :

   - La variable _utilisateur du serveur web_ exécute l’administrateur et le storefront.

   - La variable _utilisateur de ligne de commande_ exécute les tâches cron et les utilitaires de ligne de commande.

  Les deux utilisateurs requièrent les mêmes autorisations pour le système de fichiers. Il est donc préférable d’utiliser une [groupe partagé](configure-permissions.md#set-ownership-and-permissions-for-two-users) et définissez une [`umask`](#restrict-access-with-a-umask).

### Limitation de l’accès avec un masque

Pour renforcer la sécurité, en particulier dans un environnement de production sur un système d’hébergement partagé, vous pouvez utiliser `umask` pour restreindre l’accès. A `umask`—également appelé _masque de création du système de fichiers_—est un ensemble de bits qui contrôle la manière dont les autorisations de fichier sont définies pour les fichiers nouvellement créés.

>[!WARNING]
>
>La sécurité du système de fichiers est complexe et importante. Nous vous recommandons vivement de consulter un administrateur système ou un administrateur réseau expérimenté avant de décider du niveau d’autorisation à définir. Nous vous fournissons un mécanisme à utiliser, mais la création d’une stratégie d’autorisations est de votre responsabilité.

Adobe Commerce utilise un masque par défaut à trois bits : `002`. Soustrayez le masque par défaut des valeurs par défaut UNIX 66 pour les fichiers et 777 pour les répertoires.

Par exemple :

- **775 pour les répertoires**: contrôle complet par l’utilisateur, contrôle complet par le groupe et permet à chacun de parcourir l’annuaire. Ces autorisations sont généralement requises par les fournisseurs d’hébergement partagés.

- **664 pour les fichiers**: écriture par l’utilisateur, écriture par le groupe et lecture seule pour tous les autres utilisateurs.

Pour plus d’informations sur la création d’un `magento_umask` fichier, voir [Définir un masque](../../next-steps/set-umask.md).

## Autorisations, propriété et modes d’application

Il est recommandé d’utiliser différents modes d’application Adobe Commerce en fonction des autorisations et de la propriété :

- Par défaut
- Développeur
- Production

Voir [A propos des modes](../../../configuration/bootstrap/application-modes.md) dans le _Guide de configuration_.

Nous discutons plus en détail des recommandations relatives aux autorisations dans [Autorisations d’accès aux systèmes de fichiers](../../../configuration/deployment/file-system-permissions.md) dans le _Guide de configuration_.

>[!TIP]
>
>Avant d’installer Adobe Commerce, consultez [Configuration de la propriété et des autorisations de fichier](configure-permissions.md).
