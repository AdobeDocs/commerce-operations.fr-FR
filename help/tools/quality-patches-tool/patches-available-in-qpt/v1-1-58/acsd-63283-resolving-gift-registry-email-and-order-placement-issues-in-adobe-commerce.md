---
title: 'ACSD-63283 : résolution des problèmes [!UICONTROL Gift Registry] d’e-mail et de placement des commandes dans Adobe Commerce'
description: Appliquez le correctif ACSD-63283 pour résoudre le problème d’Adobe Commerce où la commande d’éléments à partir de l’[!UICONTROL Gift Registry] provoque une exception et garantit [!UICONTROL Gift Registry Updates]’inclure uniquement les éléments corrects.
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%
---
# ACSD-63283 : résolution des problèmes [!UICONTROL Gift Registry] d’e-mail et de placement des commandes dans Adobe Commerce

Le correctif ACSD-63283 corrige le problème où la commande d’éléments à partir du [!UICONTROL Gift Registry] provoque une exception et garantit [!UICONTROL Gift Registry Updates]’inclure uniquement les éléments corrects. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63283. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

>[!NOTE]
>Ce correctif remplace et étend le correctif [ACSD-56280](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed.md) QPT.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La fonctionnalité [!UICONTROL Gift Registry] d’Adobe Commerce est affectée par deux problèmes importants :

* Lorsqu’un client passe une commande pour des articles provenant de son [!UICONTROL Gift Registry], le processus échoue en raison d’une exception déclenchée.
* De plus, le [!UICONTROL Gift Registry Updates] e-mail envoyé au propriétaire du registre inclut incorrectement des articles de toutes les registres de cadeaux, plutôt que de limiter les mises à jour aux articles du registre spécifique mis à jour.

<u>Procédure à suivre </u> :

1. Créez deux produits : Produit A et Produit B.
1. Créez deux clients : Client A et Client B.
1. Connectez-vous en tant que client A et créez un nouveau [!UICONTROL Gift Registry].
1. Accédez à la page produit du produit A et ajoutez-la à la [!UICONTROL Wishlist]. Ouvrez le [!UICONTROL Wishlist Page] et déplacez le produit A vers le [!UICONTROL Gift Registry] à l’aide de [!UICONTROL Add to Gift Registry].
1. Connectez-vous en tant que client B, créez un [!UICONTROL Gift Registry] et ajoutez-y le produit B.
1. En tant que client B, partagez le [!UICONTROL Gift Registry] par e-mail : **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**.
1. Déconnectez-vous en tant que client B.
1. Cliquez sur le lien reçu dans l’e-mail. Ajoutez le produit B au [!UICONTROL Cart] et passez une commande.

<u>Résultats attendus</u> :

Le client B reçoit l’e-mail avec les articles mis à jour uniquement de son registre des cadeaux.

<u>Résultats réels</u> :

Le client B reçoit l’e-mail contenant les articles de toutes les caisses cadeaux.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
