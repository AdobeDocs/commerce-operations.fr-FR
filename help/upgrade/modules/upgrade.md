---
title: Modules et extensions de mise à niveau
description: Utilisez l’interface de ligne de commande et le compositeur pour mettre à niveau les modules et extensions Adobe Commerce et Magento Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Mise à niveau des modules et des extensions

Pour mettre à jour ou mettre à niveau un module ou une extension :

1. Téléchargez le fichier mis à jour depuis Marketplace ou un autre développeur d’extensions. Prenez note du nom et de la version du module.

1. Exportez le contenu vers votre répertoire d’installation racine Adobe Commerce ou Magento Open Source.

1. S’il existe un module de compositeur pour le module, exécutez l’une des opérations suivantes.

   Mise à jour par nom de module :

   ```bash
   composer update vendor/module-name
   ```

   Mise à jour par version :

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Exécutez les commandes suivantes pour mettre à niveau, déployer et nettoyer le cache.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
