---
title: Conditions préalables [!DNL Data Migration Tool]
description: Découvrez ce que vous devez faire avant de commencer à utiliser l’[!DNL Data Migration Tool] pour transférer des données entre Magento 1 et Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%
---
# Conditions préalables [!DNL Data Migration Tool]

Avant de commencer la migration, assurez-vous que les conditions suivantes sont remplies.

## Système Magento 2

* Configurez votre système Magento 2 pour qu’il réponde à la [configuration requise](../../installation/system-requirements.md).

  Utilisez une topologie et une conception qui correspondent au moins à votre système Magento 1 existant.

* [Installez Magento 2](../../installation/overview.md).

## Cron

Ne démarrez pas les tâches cron Magento 2.

## Base de données

* Après l’installation, sauvegardez ou [videz](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) votre base de données Magento 2 dès que possible. Vous pouvez ainsi restaurer l’état initial de la base de données si la migration échoue.

* Vérifiez si l’[!DNL Data Migration Tool] dispose d’un accès réseau pour connecter les bases de données Magento 1 et Magento 2.

  Ouvrez les ports de votre pare-feu afin que l’outil de migration puisse communiquer avec les bases de données.

* Assurez-vous que vos comptes MySQL disposent de tous les privilèges nécessaires pour accéder aux bases de données Magento.

Si la journalisation binaire est activée pour votre base de données Magento 1, définissez la variable système MySQL [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) globale sur `1` ou accordez le privilège [SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) à votre compte.

* Il est déconseillé de créer de nouvelles entités (produits, catégories et attributs) dans votre boutique Magento 2 avant la migration, car la [!DNL Data Migration Tool] remplace ces nouvelles entités par les anciennes de Magento 1.

## Extensions

Migration du code d’extension Magento 1 vers Magento 2.

Pour trouver les dernières versions d’extensions, rendez-vous sur [[!DNL [Commerce Marketplace]]](https://commercemarketplace.adobe.com//) ou contactez votre fournisseur d’extensions.

Tu peux également utiliser le [[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
