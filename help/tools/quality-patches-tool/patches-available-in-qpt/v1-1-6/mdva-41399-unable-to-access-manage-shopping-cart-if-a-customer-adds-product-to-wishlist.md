---
title: 'MDVA-41399 : impossible d’accéder à la fonction Gérer le panier si un client ajoute un produit à une liste de souhaits'
description: Le correctif MDVA-41399 résout le problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la page Gérer le panier si un client ajoute un produit à la liste de souhaits. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-41399. Notez que le problème a été résolu dans Adobe Commerce 2.4.2.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%
---
# MDVA-41399 : impossible d’accéder à la fonction Gérer le panier si un client ajoute un produit à une liste de souhaits

Le correctif MDVA-41399 résout le problème en raison duquel les utilisateurs administrateurs ne peuvent pas accéder à la page Gérer le panier si un client ajoute un produit à la liste de souhaits. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6 est installé. L’ID du correctif est MDVA-41399. Notez que le problème a été résolu dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs ne peuvent pas accéder à la page Gérer le panier si un client ajoute un produit à la liste de souhaits.

<u>Conditions préalables</u> :

1. Créez deux produits ou plus.
1. Créez un client.
1. Activez le mode Développeur.

<u>Procédure à suivre </u> :

1. Accédez à Storefront et connectez-vous en tant que client à partir des conditions préalables.
1. Ajouter un produit à la liste de souhaits.
1. Accédez au panneau d’administration et à la page d’édition du client créée, puis cliquez sur le bouton **Gérer le panier**.

<u>Résultats attendus</u> :

L’utilisateur administrateur peut gérer le panier.

<u>Résultats réels</u> :

L’utilisateur administrateur reçoit un message d’erreur : *Une erreur s’est produite. Voir le journal des erreurs pour plus de détails.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
