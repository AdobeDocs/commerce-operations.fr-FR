---
title: Bonne pratique pour la configuration des rapports
description: Optimisez les performances du site en supprimant le module de création de rapports si vous ne l’utilisez pas.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# Bonne pratique pour la configuration des rapports

Si votre entreprise n’a pas besoin de la fonctionnalité de création de rapports ou de segments dynamiques de clients, désactivez la fonctionnalité [Rapports](https://experienceleague.adobe.com/fr/docs/commerce-admin/config/general/reports) pour améliorer les performances de la boutique.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Désactiver les rapports

Si vous n’utilisez pas les rapports ou les segments clients dynamiques, désactivez la fonctionnalité Rapports.

1. À partir de l’interface d’administration, accédez à **Magasins** > **Paramètres** > **Configuration** > **Général** > **Rapports**.
1. Sous **Options générales**, définissez **Activer les rapports** sur *Non*.
1. Videz le cache en exécutant `php bin/magento cache:flush` ou dans Admin sous **Système** > **Outils** > **Gestion du cache**.

## Informations supplémentaires

- [Génération de rapports dans Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/reporting/reports-menu)
- [Segments dynamiques client](https://experienceleague.adobe.com/fr/docs/commerce-admin/customers/segments/customer-segments)
