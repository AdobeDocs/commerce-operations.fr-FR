---
title: Bonnes pratiques relatives aux extensions
description: Découvrez comment éviter les problèmes de performances causés par les extensions tierces d’Adobe Commerce.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 1fdbded7738365593ef7da64f4dbe6713984bff3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Bonnes pratiques relatives aux extensions

Les extensions tierces d’Adobe Commerce (modules) peuvent entraîner divers problèmes qui peuvent avoir un impact négatif sur les performances du storefront. Vous pouvez éviter ces problèmes en suivant les bonnes pratiques suivantes :

- Développez vos intégrations et personnalisations Commerce à l’aide de l’[extensibilité hors processus](https://developer.adobe.com/commerce/extensibility/) chaque fois que possible pour faciliter la maintenance et la mise à niveau.
- Téléchargez et achetez des extensions tierces à partir d’une source de confiance, comme le [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- Mettez à jour toutes les extensions tierces vers la dernière version.
- Si vous ne pouvez pas conserver vos extensions tierces à jour, pensez à utiliser d’autres extensions.
- Lors de la planification d’une mise à niveau vers une nouvelle version d’Adobe Commerce, vérifiez que les extensions tierces installées sont compatibles avec la nouvelle version et mettez à niveau les extensions si nécessaire.

>[!NOTE]
>
> Toutes les extensions disponibles dans Adobe Commerce Marketplace sont nécessaires pour maintenir la compatibilité avec les nouvelles versions de Commerce. Voir [Compatibilité des versions](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Informations supplémentaires

- [Bonnes pratiques pour la planification des mises à niveau](../../../upgrade/prepare/best-practices.md)
- Utilisation d’extensions tierces avec Adobe Commerce sur l’infrastructure cloud
   - [Technologies et exigences - Développement et test](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [Pourquoi tester entièrement dans l’intégration et l’évaluation ?](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
