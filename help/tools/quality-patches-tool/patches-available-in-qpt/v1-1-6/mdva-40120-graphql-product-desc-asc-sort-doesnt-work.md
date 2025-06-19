---
title: 'MDVA-40120 : le tri DESC/ASC du produit GraphQL ne fonctionne pas'
description: Le correctif MDVA-40120 résout le problème où le tri GraphQL par DESC/ASC ne fonctionne pas avec les produits ayant la même pertinence ou le même prix. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-40120. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: GraphQL, Products
role: Admin
exl-id: 4df7f14d-181b-4f34-aff7-0af823632015
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-40120 : le tri DESC/ASC du produit GraphQL ne fonctionne pas

Le correctif MDVA-40120 résout le problème où le tri GraphQL par DESC/ASC ne fonctionne pas avec les produits ayant la même pertinence ou le même prix. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-40120. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

Créez quelques produits différents au même prix.

<u>Procédure à suivre </u> :

1. Exécutez la requête GraphQL suivante :

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Vérifiez la réponse.
1. Modifiez l’ordre de tri de **ASC** en **DESC** dans la requête GraphQL :

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Vérifiez la réponse.

<u>Résultats attendus</u> :

La liste des produits dans la réponse GraphQL doit être modifiée en fonction de l’ordre de tri.

<u>Résultats réels</u> :

L’ordre de tri reste inchangé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
