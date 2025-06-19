---
title: 'ACSD-62332 : la requête GraphQL de liste de produits est limitée à 10 000 produits et  [!DNL Live Search]  la page actuelle à 1'
description: Appliquez le correctif ACSD-62332 pour résoudre les problèmes d’Adobe Commerce où la requête GraphQL de liste de produits est limitée à un nombre total de 10 000 produits et où  [!DNL Live Search]  définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors de l’interrogation via GraphQL.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332 : requête GraphQL de liste de produits limitée à 10 000 produits et [!DNL Live Search] définit la page actuelle sur 1

>[!NOTE]
>
>Ce correctif est une version mise à jour de [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) et remplace [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) dans les versions 2.4.6 à 2.4.6-p8. Consultez les articles correspondants pour plus de détails.

Le correctif ACSD-62332 corrige les problèmes où la requête GraphQL de liste de produits est limitée à un `total_count` de 10 000 produits et où [!DNL Live Search] définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors de l’interrogation via GraphQL. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62332. Notez que les problèmes ont été résolus dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL de liste de produits est limitée à un total_count de 10 000 produits et où [!DNL Live Search] définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors de l’interrogation via GraphQL.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
