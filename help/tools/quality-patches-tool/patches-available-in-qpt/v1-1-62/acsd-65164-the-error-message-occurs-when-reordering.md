---
title: 'ACSD-65164 : message d’erreur affiché lors de la réorganisation du produit configurable avec une seule option de case à cocher personnalisée sélectionnée'
description: Appliquez le correctif ACSD-65164 pour résoudre le problème d’Adobe Commerce où le message d’erreur *Certaines des options d’élément sélectionnées ne sont actuellement pas disponibles* se produit lors de la réorganisation d’un produit configurable avec une seule option personnalisée de case à cocher sélectionnée.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '426'
ht-degree: 0%
---
# ACSD-65164 : message d’erreur affiché lors de la réorganisation du produit configurable avec une seule option de case à cocher personnalisée sélectionnée

Le correctif ACSD-65164 corrige le problème où le message d’erreur *Certaines des options d’élément sélectionnées ne sont actuellement pas disponibles* se produit lors de la réorganisation d’un produit configurable avec une seule option personnalisée de case à cocher sélectionnée. Ce correctif est disponible lorsque la version 1.1.62 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65164. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la réorganisation d’un produit configurable avec une seule option personnalisée de case à cocher sélectionnée, le système renvoie un message d’erreur : *Certaines des options d’élément sélectionnées ne sont actuellement pas disponibles*.

### Procédure de réplication :

1. Dans le panneau d’administration, accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**.
1. Sous **[!UICONTROL Customizable Options]**, ajoutez une option *Case à cocher*.
   * Définissez l’option de case à cocher sur *Obligatoire*.
   * Ajoutez deux valeurs d’option.
1. Accédez au storefront et connectez-vous en tant que client enregistré.
1. Ajoutez le produit au panier avec une case à cocher sélectionnée.
1. Accédez à **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**.
1. Accédez à **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** pour ajouter le même produit.

**Résultats attendus :**

Le produit doit être ajouté correctement au panier.

**Résultats réels:**

Un message d’erreur s’affiche :

*Impossible d’ajouter le produit avec le SKU « 24-MB01 » au panier : certaines des options d’article sélectionnées ne sont pas disponibles actuellement.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
