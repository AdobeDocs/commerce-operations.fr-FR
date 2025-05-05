---
title: 'ACSD-59865 : [!UICONTROL Cart Price Rule] ne parvient pas à annuler les règles précédentes en raison d’une quantité insuffisante de produits.'
description: Appliquez le correctif ACSD-59865 pour résoudre le problème Adobe Commerce en raison duquel la valeur *Étape de quantité du rabais* dans *Remise de prix fixe* *Pourcentage de remise sur le prix du produit* et *Acheter X obtenir Y* [!UICONTROL Cart Price Rules] n’annule plus l’action des règles précédentes.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865 : [!UICONTROL Cart Price Rule] ne parvient pas à annuler les règles précédentes en raison d’une quantité insuffisante de produits.

Le correctif ACSD-59865 corrige le problème où la valeur *[!UICONTROL Discount quantity step]* dans *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* et *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] n’annule plus l’action des règles précédentes. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 est installé. L’ID de correctif est ACSD-59865. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule] ne parvient pas à annuler les règles précédemment appliquées en raison d’une quantité insuffisante de produits dans le panier.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant qu’administrateur.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** et cliquez sur **[!UICONTROL Add New rule]**.
   * Définissez **[!UICONTROL Rule Name]** = *Test - 1*
   * Sélectionnez tous les *sites web* et *groupes de clients*
   * Set **[!UICONTROL Priority]** = *0*
   * Accédez à la section **[!UICONTROL Actions]** :
      * Définissez **[!UICONTROL Apply]** = *Pourcentage de remise sur le prix du produit*
      * Définissez **[!UICONTROL Discount amount]** = *10*
      * Set **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Set **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Définissez **[!UICONTROL Discard subsequent rules]** sur *Non*
1. Effacez le cache.
1. Accédez à Storefront, ajoutez un élément au panier, puis passez à *checkout/cart*.
1. Vérifiez que la remise *10%* est appliquée à votre panier.
1. Revenez à **[!UICONTROL Cart Price Rules]** et créez une nouvelle règle.
   * Définissez **[!UICONTROL Rule Name]** = *Test - 2*
   * Sélectionnez tous les **[!UICONTROL Websites]** et **[!UICONTROL Customer Groups]**
   * Set **[!UICONTROL Priority]** = *2*
   * Accédez à la section **[!UICONTROL Actions]** :
      * Définissez **[!UICONTROL Apply]** = *Pourcentage de remise sur le prix du produit*
      * Définissez **[!UICONTROL Discount amount]** = *20*
      * Set **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Set **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Effacez le cache.
1. Revenez à Storefront.
1. Mettez à jour le panier pour actualiser les règles. Vérifiez que la remise *10%* n&#39;est plus appliquée.
1. Ajoutez des éléments à votre panier jusqu’à ce que la quantité corresponde à la valeur *Step* requise pour la deuxième règle.

<u>Résultats attendus</u> :

Le premier [!UICONTROL Cart Price Rule] est appliqué lorsque les conditions de la deuxième règle sont remplies.

<u>Résultats réels</u> :

Les règles de prix sont appliquées comme configurées dans le tableau de bord de l&#39;administrateur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
