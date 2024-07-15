---
title: '[!DNL Data Migration Tool] conditions préalables'
description: Découvrez ce que vous devez faire avant de commencer à utiliser le  [!DNL Data Migration Tool] pour transférer des données entre Magento 1 et Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool] conditions préalables

Avant de commencer la migration, assurez-vous que les conditions suivantes sont remplies.

## Système Magento 2

* Configurez votre système Magento 2 afin qu’il réponde à la [configuration requise](../../installation/system-requirements.md).

  Utilisez une topologie et une conception qui correspondent au moins à votre système Magento 1 existant.

* [Installez Magento 2](../../installation/overview.md).

## Cron

Ne démarrez pas les tâches Magento 2 cron.

## Base

* Après l’installation, sauvegardez ou [videz](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) votre base de données Magento 2 dès que possible. Vous pouvez ainsi restaurer l’état initial de la base de données en cas d’échec de la migration.

* Vérifiez si le [!DNL Data Migration Tool] dispose d’un accès réseau pour connecter les bases de données du Magento 1 et du Magento 2.

  Ouvrez les ports dans votre pare-feu afin que l’outil de migration puisse communiquer avec les bases de données.

* Assurez-vous que vos comptes MySQL disposent de tous les privilèges nécessaires pour accéder aux bases de données des Magento.

Si la journalisation binaire est activée pour votre base de données Magento 1, définissez la variable système MySQL globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) sur `1` ou accordez le [privilège SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) à votre compte.

* Il est déconseillé de créer de nouvelles entités (produits, catégories et attributs) dans votre magasin Magento 2 avant la migration, car [!DNL Data Migration Tool] remplace ces nouvelles entités par les anciennes du Magento 1.

## Extensions

Migrez le code de l’extension Magento 1 vers Magento 2.

Pour trouver les dernières versions des extensions, rendez-vous sur [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) ou contactez votre fournisseur d’extension.

Vous pouvez également utiliser le [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
