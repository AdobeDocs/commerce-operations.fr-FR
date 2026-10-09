---
title: 'MDVA-29400 : commandes dupliquées passées avec PayPal Express Checkout'
description: Le correctif MDVA-29400 résout le problème de création de commandes dupliquées lorsque les clients passent des commandes avec PayPal Express Checkout. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID du correctif est MDVA-29400. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.
feature: Checkout, Orders, Payments
role: Admin
exl-id: 6f7291d3-d554-4e4e-a55d-89ea2b9dea33
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%
---
# MDVA-29400 : commandes dupliquées passées avec PayPal Express Checkout

Le correctif MDVA-29400 résout le problème de création de commandes dupliquées lorsque les clients passent des commandes avec PayPal Express Checkout. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID du correctif est MDVA-29400. Notez que le problème a été résolu dans Adobe Commerce 2.4.1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes en double sont créées lorsque les utilisateurs passent des commandes avec PayPal Express Checkout.

<u>Conditions préalables</u> :

Activation et configuration du paiement PayPal Express.

<u>Procédure à suivre </u> :

1. Ajoutez un produit au panier.
1. Accédez à la page de passage en caisse et utilisez PayPal Express comme mode de paiement.
1. Il sera redirigé vers la page paypal/express/review/ .
1. Passer une commande. Vous serez redirigé vers la page de succès.
1. Retournez sur la page PayPal/express/review/.
1. Cliquez sur le bouton **Passer une commande**.

<u>Résultats attendus</u> :

Une seule commande est créée.

<u>Résultats réels</u> :

Vous obtenez l&#39;erreur suivante : *le jeton de paiement PayPal Express n&#39;existe pas*, mais la deuxième commande a été passée avec succès.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
