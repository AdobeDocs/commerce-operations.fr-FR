---
title: 'ACSD-62332 : requête GraphQL de liste de produits limitée à 10 000 produits et  [!DNL Live Search] définit la page active sur 1'
description: Appliquez le correctif ACSD-62332 pour résoudre les problèmes Adobe Commerce où la requête GraphQL de la liste de produits est limitée à un nombre total de 10 000 produits et où  [!DNL Live Search] définit la page actuelle sur *1* au lieu de la page *2* dans les critères de recherche lors d’une requête via GraphQL.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 276fe6ca8d1166a8f4254aca5d49cbb4b1aa607b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332 : requête GraphQL de liste de produits limitée à 10 000 produits et [!DNL Live Search] définit la page active sur 1

>[!NOTE]
>
>Ce correctif est une version mise à jour de [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) et remplace les versions [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) sur 2.4.6 - 2.4.6-p8. Pour plus d’informations, reportez-vous aux articles correspondants.

Le correctif ACSD-62332 corrige les problèmes où la requête GraphQL de liste de produits est limitée à un `total_count` de 10 000 produits et où [!DNL Live Search] définit la page actuelle sur *1* au lieu de la page *2* dans les critères de recherche lors d’une requête via GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-62332. Veuillez noter que les problèmes ont été corrigés dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL de la liste de produits est limitée à un nombre total de 10 000 produits et où [!DNL Live Search] définit la page active sur *1* au lieu de la page *2* dans les critères de recherche lors d’une requête via GraphQL.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
