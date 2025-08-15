---
title: 'MDVA-42969 : la règle de produit associé ne fonctionne que lorsque le segment client est défini sur tous'
description: Le correctif MDVA-42969 corrige le problème en raison duquel la règle de produit associée ne fonctionne que lorsque le segment client est défini sur Tous. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-42969. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969 : la règle de produit associé ne fonctionne que lorsque le segment client est défini sur tous

Le correctif MDVA-42969 corrige le problème en raison duquel la règle de produit associée ne fonctionne que lorsque le segment client est défini sur Tous. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-42969. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de produit associé ne fonctionne que lorsque le segment client est défini sur Tous.

<u>Procédure à suivre </u> :

1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **Relations de produits basées sur des règles** et définissez **Afficher les produits associés** = **Basé uniquement sur des règles**.
1. Accédez à **Clients** > **Segments** et créez un segment : **Appliquer à** = **Visiteurs et clients enregistrés**.
1. Accédez à **Marketing** > **Règles des produits associés** et créez une règle.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Ouvrez le produit correspondant sur le storefront et vérifiez que les produits à afficher sont affichés.
1. Modifiez la règle créée à l’étape 3 et définissez **Segments clients** = **Spécifique** > **Segment** à partir de l’étape 2.
1. Ouvrez le produit correspondant sur le storefront.

<u>Résultats attendus</u> :

Les produits associés à des règles s’affichent sur le storefront pour les visiteurs sur le produit, car le segment client est créé avec la configuration suivante :

**Appliquer à** = **Visiteurs et clients enregistrés**

<u>Résultats réels</u> :

Aucun produit associé ne s&#39;affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
