---
title: 'MDVA-42969 : la règle de produit associée ne fonctionne que lorsque le segment de client est défini sur tous'
description: Le correctif MDVA-42969 corrige le problème en raison duquel la règle de produit associée ne fonctionne que lorsque le segment client est défini sur tous. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-42969. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969 : La règle de produit associée ne fonctionne que lorsque le segment de client est défini sur tous les

Le correctif MDVA-42969 corrige le problème en raison duquel la règle de produit associée ne fonctionne que lorsque le segment client est défini sur tous. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-42969. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de produit associée ne fonctionne que lorsque le segment client est défini sur tous.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **Relations de produits basées sur des règles** et définissez **Afficher les produits associés** = **Basé sur des règles uniquement**.
1. Accédez à **Customers** > **Segments** et créez un nouveau segment : **Appliquer à** = **Visiteurs et clients enregistrés**.
1. Accédez à **Marketing** > **Règles de produit connexes** et créez une règle.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Ouvrez le produit correspondant sur le storefront et vérifiez que les Produits à afficher s’affichent.
1. Modifiez la règle créée à l’étape 3 et définissez **Segments du client** = **Spécifique** > **Segment** à partir de l’étape 2.
1. Ouvrez le produit correspondant sur le storefront.

<u>Résultats attendus</u> :

Les produits associés basés sur des règles s’affichent sur le storefront pour les visiteurs du produit, car le segment de client est créé avec la configuration suivante :

**Appliquer à** = **Visiteurs et clients enregistrés**

<u>Résultats réels</u> :

Aucun produit associé ne s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
