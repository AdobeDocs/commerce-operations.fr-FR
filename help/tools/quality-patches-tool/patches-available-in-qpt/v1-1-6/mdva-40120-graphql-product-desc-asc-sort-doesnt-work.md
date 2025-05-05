---
title: 'MDVA-40120 : Le tri du produit GraphQL DESC/ASC ne fonctionne pas'
description: Le correctif MDVA-40120 résout le problème en raison duquel le tri GraphQL par DESC/ASC ne fonctionne pas avec des produits ayant la même pertinence ou le même prix. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-40120. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: GraphQL, Products
role: Admin
exl-id: 4df7f14d-181b-4f34-aff7-0af823632015
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-40120 : Le tri du produit GraphQL DESC/ASC ne fonctionne pas

Le correctif MDVA-40120 résout le problème en raison duquel le tri GraphQL par DESC/ASC ne fonctionne pas avec des produits ayant la même pertinence ou le même prix. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID de correctif est MDVA-40120. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

Créez quelques produits différents au même prix.

<u>Étapes à reproduire</u> :

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
1. Remplacez l’ordre de tri de **ASC** par **DESC** dans la requête GraphQL :

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

La liste de produits dans la réponse GraphQL doit être modifiée selon l’ordre de tri.

<u>Résultats réels</u> :

L’ordre de tri reste inchangé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
