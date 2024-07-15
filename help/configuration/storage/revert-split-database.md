---
title: Rétablir la base de données partagée
description: Rétablissement d’une implémentation de base de données partagée obsolète vers une implémentation de base de données unique.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Rétablir à partir de la base de données partagée

{{ee-only}}

Pour les clients Adobe Commerce qui ont implémenté [Split Database](multi-master.md), la rubrique suivante décrit comment rétablir ou rémigrer vers une base de données unique. Nous recommandons aux commerçants Adobe Commerce qui utilisent actuellement la base de données partagée et qui prévoient d’effectuer la mise à niveau vers la version 2.4.2 et versions ultérieures de passer en revue ces étapes, ainsi que notre [annonce](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sur l’abandon prévu de la base de données partagée.

La restauration d’une base de données partagée vers une base de données unique implique la création de sauvegardes des bases de données `magento_quote` et `magento_sales` avant de les charger dans la base de données unique `magento_main`.

Dans cet exemple, nous nous connectons aux trois bases de données, qui sont installées sur le même hôte (`magento2-mysql`) que l’utilisateur &quot;root&quot;. Vous devez remplacer ces valeurs par les valeurs appropriées pour vos bases de données.

1. Créez une sauvegarde de la base de données `magento_quote` :

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Créez une sauvegarde de la base de données `magento_sales` :

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Chargez la base de données `magento_quote` dans la base de données `magento_main` :

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Chargez la base de données `magento_sales` dans la base de données `magento_main` :

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Déposez la base de données `magento_sales` :

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Déposez la base de données `magento_quote` :

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Supprimez la configuration de déploiement pour `checkout` et `sales` dans les sections `connections` et `resources` du fichier `env.php`.
1. Restaurer des clés étrangères :

   ```bash
   bin/magento setup:upgrade
   ```

## Vérifier votre travail

Pour vérifier que l’implémentation de votre base de données unique fonctionne correctement, effectuez les tâches suivantes et vérifiez que les données sont ajoutées aux tables de base de données `magento_main` à l’aide d’un outil de base de données tel que [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin) :

1. Vérifiez que les clés étrangères ont été restaurées. Par exemple, la clé `QUOTE_STORE_ID_STORE_STORE_ID` dans la table de base de données `quote`.
1. Vérifiez que les clients peuvent passer des commandes à partir du storefront.
1. Vérifiez que les commandes créées avant de rétablir la base de données fractionnée en une seule base de données sont disponibles dans l’administrateur.
