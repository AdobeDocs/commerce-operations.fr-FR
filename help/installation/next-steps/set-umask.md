---
title: Définir un masque (facultatif)
description: Améliorez la sécurité de votre installation Adobe Commerce ou Magento Open Source sur site en restreignant les autorisations du système de fichiers.
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Définir un masque (facultatif)

Le groupe de serveurs web doit disposer d’autorisations d’écriture sur certains répertoires du système de fichiers ; toutefois, vous pouvez vouloir une sécurité renforcée, en particulier en production. Nous vous offrons la possibilité de restreindre davantage ces autorisations à l’aide d’une [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

Notre solution consiste à vous permettre de créer éventuellement un fichier nommé `magento_umask` dans le répertoire racine de votre application, qui limite les autorisations du groupe de serveurs web et de tous les autres utilisateurs.

>[!NOTE]
>
>Nous vous recommandons de modifier le masque sur un seul utilisateur ou un système d’hébergement partagé uniquement. Si vous disposez d’un serveur d’applications privé, le groupe doit disposer d’un accès en écriture au système de fichiers ; la tâche supprime l’accès en écriture du groupe.

Masque par défaut (sans `magento_umask` specified) est `002`, ce qui signifie :

* 775 pour les répertoires, ce qui signifie un contrôle total par l’utilisateur, un contrôle complet par le groupe, et permet à chacun de parcourir l’annuaire. Ces autorisations sont généralement requises par les fournisseurs d’hébergement partagés.

* 664 pour les fichiers, ce qui signifie qu’ils peuvent être écrits par l’utilisateur, écrits par le groupe et en lecture seule pour tous les autres utilisateurs.

Il est courant d’utiliser une valeur de `022` dans le `magento_umask` , ce qui signifie :

* 755 pour les répertoires : contrôle total pour l’utilisateur et tous les autres utilisateurs peuvent parcourir les répertoires.
* 644 pour les fichiers : autorisations de lecture-écriture pour l’utilisateur et de lecture seule pour tous les autres utilisateurs.

Pour définir `magento_umask`:

1. Dans un terminal de ligne de commande, connectez-vous à votre serveur d’applications en tant que [propriétaire du système de fichiers](../prerequisites/file-system/overview.md).
1. Accédez au répertoire d’installation de l’application :

   ```bash
   cd <Application install directory>
   ```

1. Utilisez la commande suivante pour créer un fichier nommé `magento_umask` et écrivez le `umask` à lui.

   ```bash
   echo <desired umask number> > magento_umask
   ```

   Vous devez maintenant avoir un fichier nommé `magento_umask` dans le `<Magento install dir>` avec le seul contenu correspondant à `umask` Nombre.

1. Déconnectez-vous et reconnectez-vous en tant que [propriétaire du système de fichiers](../prerequisites/file-system/overview.md) pour appliquer les modifications.
