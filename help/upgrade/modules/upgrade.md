---
title: Modules et extensions de mise à niveau
description: Utilisez l’interface de ligne de commande et le compositeur pour mettre à niveau les modules et extensions Adobe Commerce.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Mise à niveau des modules et des extensions

Pour mettre à jour ou mettre à niveau un module ou une extension :

1. Téléchargez le fichier mis à jour depuis Marketplace ou un autre développeur d’extensions. Prenez note du nom et de la version du module.

1. Exportez le contenu vers votre répertoire d’installation racine Adobe Commerce.

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

## Extensions groupées de fournisseurs (VBE)

Adobe a supprimé tous les [VBEs](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/modules/upgrade) dans la version 2.4.4. Les fournisseurs continuent de prendre en charge ces extensions sur Adobe Commerce Marketplace.

Si vous souhaitez continuer à utiliser ces extensions avec Adobe Commerce 2.4.4 et versions ultérieures, vous devez mettre à jour les dépendances de package correspondantes dans votre fichier `composer.json` _avant_ de procéder à la mise à niveau vers la version 2.4.4. Contactez le fournisseur pour connaître le nom et la version du module à utiliser.

Pour plus d’informations, consultez les listes Adobe Commerce Marketplace suivantes :

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
