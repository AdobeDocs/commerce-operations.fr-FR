---
title: Bonnes pratiques relatives aux extensions
description: Découvrez comment éviter les problèmes de performances causés par les extensions Adobe Commerce tierces.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%
---
# Bonnes pratiques relatives aux extensions

Les extensions tierces (modules) Adobe Commerce peuvent provoquer divers problèmes susceptibles de nuire aux performances du storefront. Vous pouvez éviter ces problèmes en suivant ces bonnes pratiques :

- Développez vos intégrations et personnalisations Commerce à l’aide de l’[extensibilité hors processus](https://developer.adobe.com/commerce/extensibility/) dans la mesure du possible pour faciliter la maintenance et la mise à niveau.
- Téléchargez et achetez des extensions tierces auprès d’une source approuvée, comme le [&#128279;](https://commercemarketplace.adobe.com//extensions.html).
- Mettez à jour toutes les extensions tierces vers la dernière version.
- Si vous ne pouvez pas garder vos extensions tierces à jour, envisagez d’utiliser des extensions différentes.
- Lors de la planification d’une mise à niveau vers une nouvelle version d’Adobe Commerce, vérifiez que les extensions tierces installées sont compatibles avec la nouvelle version et mettez à niveau les extensions si nécessaire.

>[!NOTE]
>
> Toutes les extensions disponibles sur la Marketplace Adobe Commerce sont nécessaires pour maintenir la compatibilité avec les nouvelles versions de Commerce. Voir [Compatibilité des versions](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Informations supplémentaires

- [Bonnes pratiques pour la planification des mises à niveau](../../../upgrade/prepare/best-practices.md)
- Utilisation d’extensions tierces avec Adobe Commerce sur les infrastructures cloud
  - [Technologies et exigences - Développement et tests](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/overview#cloud-req-devtest)
  - [Pourquoi effectuer des tests complets dans Intégration et évaluation ?](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
