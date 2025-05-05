---
title: 'ACSD-62428 : Erreurs d’état des stocks dans l’index de recherche catalogue'
description: Appliquez le correctif ACSD-62428 pour résoudre le problème en raison duquel la valeur "is_out_of_stock" dans l’index de recherche catalogue est incorrectement définie lorsque le SKU n’est pas un attribut pouvant faire l’objet d’une recherche.
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428 : Erreurs d’état des stocks dans l’index de recherche catalogue

Le correctif ACSD-62428 corrige le problème en raison duquel les valeurs `is_out_of_stock` de l’index de recherche catalogue sont définies sur une valeur incorrecte lorsque l’attribut SKU n’est pas défini comme pouvant faire l’objet d’une recherche. Ce correctif est disponible avec le [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID de correctif est ACSD-62428. Veuillez noter que le problème devait être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur `is_out_of_stock` de l’index de recherche de catalogue est définie sur une valeur incorrecte lorsque le SKU n’est pas configuré comme un attribut pouvant faire l’objet d’une recherche, ce qui entraîne une représentation du stock inexacte.

<u>Étapes à reproduire</u> :

1. Créez un [!UICONTROL Source] personnalisé et un [!UICONTROL Stock] personnalisé.
1. Créez trois produits simples et attribuez leur inventaire au [!UICONTROL Source] personnalisé. Affectez ces produits à une catégorie.
1. Définissez *[!UICONTROL Inventory (MSI) Indexer]* sur *[!UICONTROL Update on Save]* pour faciliter la réplication.
1. Définissez le *[!UICONTROL Source Item Status]* sur *[!UICONTROL In Stock]* et affectez un *[!UICONTROL Quantity]*.
1. Enregistrez le produit.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et ouvrez l’attribut **[!UICONTROL SKU]** .
1. Définissez *[!UICONTROL Use In]* sur *[!UICONTROL No]*.
1. Modifiez la quantité du produit (assurez-vous qu’elle n’est pas définie sur 0).
1. Enregistrez le produit.

<u>Résultats attendus</u> :

La valeur `is_out_of_stock` reflète exactement l’état du stock du produit, même si le SKU n’est pas un attribut pouvant faire l’objet d’une recherche.

<u>Résultats réels</u> :

La valeur `is_out_of_stock` est incorrectement définie sur 1 et l’attribut SKU est absent des données indexées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
