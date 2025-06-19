---
title: 'ACSD-63299 : Le prix spécial d''un produit configurable ne s''affiche pas sur le storefront'
description: Appliquez le correctif ACSD-63299 pour résoudre le problème d’Adobe Commerce où l’attribut de prix spécial n’affecte plus l’affichage des prix spéciaux pour les produits configurables.
feature: Catalog Management
Role: Admin, Developer
exl-id: cd1775c5-783e-4ed5-a148-1dae0b7542f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299 : Le prix spécial d&#39;un produit configurable ne s&#39;affiche pas sur le storefront

Le correctif ACSD-63299 corrige le problème où l&#39;attribut de prix spécial n&#39;affecte plus l&#39;affichage des prix spéciaux pour les produits configurables. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63299. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

En [!DNL Adobe Commerce], la modification de la valeur *Utilisé dans la liste des produits* pour l&#39;attribut de prix spécial n&#39;affecte plus l&#39;affichage des prix spéciaux pour les produits configurables.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**.
1. Recherchez l’attribut ***[!UICONTROL special_price]*** et accédez à **[!UICONTROL Storefront Properties]**.
1. Remplacez ***[!UICONTROL Used in Product Listing]*** par ***[!UICONTROL No]***.
1. Créez un produit configurable avec un enfant :
   * Nom et SKU : test
   * Prix : 159 $
   * Option de génération en fonction de la couleur. Ajoutez une nouvelle couleur : Bleu
   * Enregistrer
1. Ouvrez le produit enfant et procédez comme suit :
   * Fixez un prix spécial à 99,90 $ en **[!UICONTROL Advanced Pricing]**
   * Remplacez [!UICONTROL Visibility] par **[!UICONTROL Catalog, Search]**.
1. Ouvrez la page produit simple et confirmez que le prix spécial est visible.
1. Ouvrez la page de produit configurable.
1. Sélectionnez le produit bleu.

<u>Résultats attendus</u> :

Le prix spécial est visible de la même manière qu&#39;il l&#39;est pour le produit simple.

<u>Résultats réels</u> :

1. Le prix complet s’affiche lorsqu’un produit configurable est sélectionné.
1. Il y a un décalage entre les sections *Aussi bas que...* (99,90 $) et le prix réel (99,90 $ + 59,10 $ = 159,00 $).

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
