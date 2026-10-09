---
title: 'MDVA-39153 : le montant de la remise n’est pas calculé correctement lors de la réorganisation dans l’administrateur'
description: Le correctif MDVA-39153 corrige le problème en raison duquel le montant de la remise n’est pas calculé correctement lors de la réorganisation dans l’administrateur. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID du correctif est MDVA-39153. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%
---
# MDVA-39153 : le montant de la remise n’est pas calculé correctement lors de la réorganisation dans l’administrateur

Le correctif MDVA-39153 corrige le problème en raison duquel le montant de la remise n’est pas calculé correctement lors de la réorganisation dans l’administrateur. Ce correctif est disponible lors de l’installation de l’outil [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) version 1.1.8. L’ID du correctif est MDVA-39153. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le montant de la remise n’est pas calculé correctement lors de la réorganisation dans l’administrateur.

<u>Procédure à suivre </u> :

1. Accédez à **Admin** > **Magasins** > **Configuration** > **Ventes** > **Taxes**.
1. Activez la taxe pour l’expédition en affichant la taxe dans le panier.
1. Activez et configurez la méthode d’expédition Tarif du tableau ($15).
1. Créez une règle de taxe pour le taux de taxe prédéfini (pour l&#39;autorité de certification).
1. Créez une règle de prix de panier avec une remise fixe de 5 $ appliquée à l’ensemble du panier et au montant de l’expédition.
1. Ajoutez au panier un produit au prix de 12 $ et accédez à la page Panier.
1. Appliquez la remise au panier.
1. Définissez le mode d’expédition dans la section « Estimations » sur « Taux forfaitaire ».
1. Effectuez le passage en caisse jusqu’aux étapes de révision (ne passez pas la commande).
1. Accédez à la page d’accueil, puis revenez au panier.
1. Remplacez la méthode d&#39;expédition dans la section « Estimations » par « Taux de tableau ».

<u>Résultats attendus</u> :

La remise reste la même - 5 $.

<u>Résultats réels</u> :

La remise est de 6,31 $.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
