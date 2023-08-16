---
title: Rétablir la base de données partagée
description: Rétablissement d’une implémentation de base de données partagée obsolète vers une implémentation de base de données unique.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Rétablir à partir de la base de données partagée

{{ee-only}}

Pour les clients Adobe Commerce qui ont implémenté [Diviser la base de données](multi-master.md), la rubrique suivante décrit comment rétablir ou rémigrer vers une seule base de données. Nous recommandons aux commerçants Adobe Commerce qui utilisent actuellement la base de données partagée et qui prévoient d’effectuer la mise à niveau vers la version 2.4.2 et versions ultérieures de passer en revue ces étapes, ainsi que notre [annonce](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) sur l’abandon prévu de la base de données partagée.

La restauration d’une base de données partagée vers une base de données unique implique la création de sauvegardes de la variable `magento_quote` et `magento_sales` bases de données avant de les charger dans la `magento_main` base de données.

Dans cet exemple, nous nous connectons aux trois bases de données qui sont installées sur le même hôte (`magento2-mysql`) comme utilisateur &quot;root&quot;. Vous devez remplacer ces valeurs par les valeurs appropriées pour vos bases de données.

1. Créez une sauvegarde de la variable `magento_quote` base de données :

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Créez une sauvegarde de la variable `magento_sales` base de données :

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Chargez la variable `magento_quote` dans la base de données `magento_main` base de données :

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Chargez la variable `magento_sales` dans la base de données `magento_main` base de données :

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Déposez le `magento_sales` base de données :

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Déposez le `magento_quote` base de données :

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Suppression de la configuration de déploiement pour `checkout` et `sales` dans le `connections` et `resources` des sections `env.php` fichier .
1. Restaurer des clés étrangères :

   ```bash
   bin/magento setup:upgrade
   ```

## Vérifier votre travail

Pour vérifier que l’implémentation de votre base de données unique fonctionne correctement, effectuez les tâches suivantes et vérifiez que les données sont ajoutées à la variable `magento_main` des tables de base de données à l’aide d’un outil de base de données tel que [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Vérifiez que les clés étrangères ont été restaurées. Par exemple, la variable `QUOTE_STORE_ID_STORE_STORE_ID` dans la `quote` table de base de données.
1. Vérifiez que les clients peuvent passer des commandes à partir du storefront.
1. Vérifiez que les commandes créées avant de rétablir la base de données fractionnée en une seule base de données sont disponibles dans l’administrateur.
