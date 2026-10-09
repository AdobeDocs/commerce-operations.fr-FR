---
title: 'ACSD-48362 : l''adresse d''expédition par défaut est utilisée au lieu d''une nouvelle adresse.'
description: Appliquez le correctif ACSD-48362 pour résoudre le problème d'Adobe Commerce où l'adresse d'expédition par défaut est utilisée au lieu d'une nouvelle lors de la commande à l'aide d'un devis négociable.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
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
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-48362 : l&#39;adresse d&#39;expédition par défaut est utilisée au lieu d&#39;une nouvelle adresse

Le correctif ACSD-48362 corrige le problème où l&#39;adresse d&#39;expédition par défaut est utilisée au lieu de l&#39;adresse nouvellement ajoutée lors de la commande à l&#39;aide d&#39;un devis négociable. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48362. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;adresse d&#39;expédition par défaut est utilisée au lieu de l&#39;adresse d&#39;expédition nouvellement ajoutée lors de la passation d&#39;une commande avec devis négociable.

<u>Procédure à suivre </u> :

1. Activez le devis B2B en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. Connectez-vous en tant qu’utilisateur d’entreprise.
1. Ajoutez un produit au panier.
1. Accédez à la page du panier et demandez un devis.
1. Accédez à la page **[!UICONTROL My Quotes]** du client et sélectionnez le devis qui vient d&#39;être créé.
1. Accédez à la section **[!UICONTROL Shipping Information]** de la page devis du client.
   * Cliquez sur **[!UICONTROL Add New Address]**, remplissez le formulaire et enregistrez l’adresse (ne sélectionnez ni **[!UICONTROL Use as my default billing address]** ni **[!UICONTROL Use as my default shipping address]**).
1. Cliquez sur **[!UICONTROL Send for Review]** sur la page de devis du client.
1. Accédez à l’administrateur Adobe Commerce en tant qu’utilisateur administrateur, ouvrez le devis qui vient d’être créé, puis cliquez sur **[!UICONTROL Send]**.
1. Accédez maintenant à la page de devis du client, actualisez la page, puis cliquez sur **[!UICONTROL Proceed to Checkout]**.
1. Sur la page Passage en caisse, les données affichent l’adresse de livraison par défaut même lorsque la nouvelle adresse de livraison est sélectionnée.
1. Cliquez sur **[!UICONTROL Continue]** et passez la commande.

<u>Résultats attendus</u> :

La commande doit utiliser la nouvelle adresse sans resélectionner l’adresse d’expédition par défaut sur la page de passage en caisse.

<u>Résultats réels</u> :

La commande est passée avec l&#39;adresse d&#39;expédition par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud . 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
