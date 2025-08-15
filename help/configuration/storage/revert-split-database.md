---
title: Rétablir la base de données fractionnée
description: Revenir d’une implémentation de base de données partagée obsolète à une implémentation de base de données unique.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Rétablir à partir de la base de données fractionnée

{{ee-only}}

Pour les clients Adobe Commerce qui ont implémenté [base de données partagée](multi-master.md), la rubrique suivante décrit comment revenir ou migrer vers une seule base de données. Nous recommandons aux commerçants Adobe Commerce qui utilisent actuellement Split Database d’envisager une mise à niveau vers la version 2.4.2, puis de passer en revue ces étapes, ainsi que notre [annonce](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) concernant l’abandon prévu de Split Database.

Pour revenir d&#39;une base de données fractionnée à une base de données unique, vous devez créer des sauvegardes des bases de données `magento_quote` et `magento_sales` avant de les charger dans la base de données `magento_main` unique.

Dans cet exemple, nous nous connectons aux trois bases de données qui sont installées sur le même hôte (`magento2-mysql`) que l’utilisateur « root ». Vous devez remplacer ces valeurs par les valeurs appropriées pour vos bases de données.

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

1. Supprimez la configuration de déploiement de `checkout` et `sales` dans les sections `connections` et `resources` du fichier `env.php`.
1. Restaurer les clés étrangères :

   ```bash
   bin/magento setup:upgrade
   ```

## Vérification de votre travail

Pour vérifier que votre implémentation de base de données unique fonctionne correctement, effectuez les tâches suivantes et vérifiez que les données sont ajoutées aux tables de base de données `magento_main` à l’aide d’un outil de base de données tel que [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin) :

1. Vérifiez que les clés étrangères ont été restaurées. Par exemple, la clé `QUOTE_STORE_ID_STORE_STORE_ID` dans la table de base de données `quote`.
1. Vérifiez que les clients peuvent passer des commandes auprès du storefront.
1. Vérifiez que les commandes créées avant de rétablir la base de données fractionnée en une seule base de données sont disponibles dans Admin.
