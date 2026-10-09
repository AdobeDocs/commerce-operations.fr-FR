---
title: 'ACSD-49065 : les éléments de devis ne sont pas visibles dans l’administrateur'
description: Appliquez le correctif ACSD-49065 pour résoudre le problème d’Adobe Commerce où les éléments de devis ne sont pas visibles dans l’administration s’ils sont uniquement affectés au stock personnalisé.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%
---
# ACSD-49065 : les éléments de devis ne sont pas visibles dans l’administrateur

Le correctif ACSD-49065 corrige le problème où les éléments de devis ne sont pas visibles dans l’administration s’ils sont uniquement affectés au stock personnalisé. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49065. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les articles de devis ne sont pas visibles dans l&#39;administrateur s&#39;ils sont uniquement affectés au stock personnalisé.

Conditions préalables requises :

Les modules **[!UICONTROL B2B]** et **[!UICONTROL Inventory]** doivent être installés.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL Company]** et **[!UICONTROL B2B Quote]** sous **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Créez un **[!UICONTROL Inventory Source]** secondaire et affectez-le à un **[!UICONTROL Inventory Stock]** secondaire.
1. Créez un produit en attribuant uniquement la **[!UICONTROL Inventory Source]** secondaire (non par défaut).
1. Accédez au storefront et créez un compte d’entreprise. Connectez-vous en tant qu’**[!UICONTROL Company Admin]** et ajoutez le produit créé au panier.
1. Accédez au panier et à la *[!UICONTROL Request a Quote]* .
1. Accédez à l’administrateur et affichez le devis demandé à l’adresse **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>Résultats attendus</u> :

Les articles sont visibles dans le nouveau devis créé avec de nouveaux produits sans enregistrer à nouveau les produits.

<u>Résultats réels</u> :

La section *[!UICONTROL Items Quoted]* est vide. Si vous réenregistrez le produit nouvellement créé, les éléments s’affichent.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
