---
title: 'MDVA-31763 : les règles de prix de catalogue sont rétablies jusqu’à la réindexation manuelle.'
description: Le correctif MDVA-31763 résout le problème où les règles de prix de catalogue sont rétablies jusqu’à la réindexation manuelle. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-31763. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---
# MDVA-31763 : les règles de prix de catalogue sont rétablies jusqu’à la réindexation manuelle.

Le correctif MDVA-31763 résout le problème où les règles de prix de catalogue sont rétablies jusqu’à la réindexation manuelle. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5 est installé. L’ID du correctif est MDVA-31763. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsqu’`catalogrule_product` indexeur partiel est exécuté sur des produits configurables, les règles de catalogue disparaissent.

<u>Procédure à suivre </u> :

1. Connectez-vous au serveur principal d’administration d’.
1. Accédez à **Magasins** > **Attributs** > **Produit** et recherchez l’attribut « fabricant ».
   * Ajoutez quelques options et définissez « Utiliser pour les conditions des règles de promotion » sur *Oui*.
1. Accédez à **Magasins** > **Attributs** > **Jeux d’attributs**.
   * Sélectionnez le jeu d’attributs par défaut et ajoutez-y l’attribut « fabricant ».
1. Créez un produit configurable avec quelques variations.
1. Définissez la valeur d’attribut « fabricant » pour le produit configurable créé précédemment.
1. Créez des règles de catalogue :
   * Actif = Oui
   * Sites Web = Site Web Principal
   * Groupes de clients = NON CONNECTÉS
   * Conditions : fabricant = \&lt;valeur sélectionnée pour le produit configurable>
   * Actions : toute remise
1. Effectuez un index complet.
1. Vérifiez le prix du produit sur PDP et assurez-vous que le prix est correct.
1. Mettez à jour l’attribut « weight » du produit configurable créé.
1. Vérifiez le prix du produit sur PDP.

<u>Résultats attendus</u> :

Les règles de prix de catalogue définies sur des produits configurables ne sont pas supprimées lors de la réindexation partielle.

<u>Résultats réels</u> :

Les règles de prix de catalogue définies sur les produits configurables sont supprimées lors de la réindexation partielle.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
