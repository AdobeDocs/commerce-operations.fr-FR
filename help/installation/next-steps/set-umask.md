---
title: Définir un masque (facultatif)
description: Améliorez la posture de sécurité de votre installation sur site Adobe Commerce en limitant les autorisations du système de fichiers.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Définir un masque (facultatif)

Le groupe de serveurs web doit disposer d&#39;autorisations en écriture sur certains répertoires du système de fichiers. Vous pouvez toutefois renforcer la sécurité, en particulier en production. Nous vous donnons la possibilité de restreindre davantage ces autorisations à l’aide d’un [masque](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Notre solution consiste à vous permettre éventuellement de créer un fichier nommé `magento_umask` dans le répertoire racine de votre application, ce qui limite les autorisations du groupe de serveurs web et de tous les autres utilisateurs.

>[!NOTE]
>
>Nous vous recommandons de modifier le masque sur un système d’hébergement à utilisateur unique ou partagé uniquement. Si vous disposez d’un serveur d’applications privé, le groupe doit avoir un accès en écriture au système de fichiers ; le masque supprime l’accès en écriture du groupe.

Le masque par défaut (sans `magento_umask` spécifié) est `002`, ce qui signifie :

* 775 pour les annuaires, ce qui signifie un contrôle complet par l&#39;utilisateur, un contrôle complet par le groupe, et permet à tout le monde de parcourir l&#39;annuaire. Ces autorisations sont généralement requises par les fournisseurs d’hébergement partagés.

* 664 pour les fichiers, ce qui signifie qu’ils peuvent être écrits par l’utilisateur, par le groupe et en lecture seule pour tous les autres

Une suggestion courante consiste à utiliser une valeur `022` dans le fichier `magento_umask`, ce qui signifie :

* 755 pour les répertoires : contrôle complet pour l&#39;utilisateur, et tout le monde peut parcourir les répertoires.
* 644 pour les fichiers : autorisations en lecture-écriture pour l’utilisateur et en lecture seule pour tous les autres.

Pour définir `magento_umask` :

1. Dans un terminal de ligne de commande, connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../prerequisites/file-system/overview.md).
1. Accédez au répertoire d’installation de l’application :

   ```bash
   cd <Application install directory>
   ```

1. Utilisez la commande suivante pour créer un fichier nommé `magento_umask` et y écrire la valeur `umask`.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Vous devriez maintenant avoir un fichier nommé `magento_umask` dans le `<Magento install dir>` avec le seul contenu étant le numéro de `umask`.

1. Déconnectez-vous et reconnectez-vous en tant que [propriétaire du système de fichiers](../prerequisites/file-system/overview.md) pour appliquer les modifications.
