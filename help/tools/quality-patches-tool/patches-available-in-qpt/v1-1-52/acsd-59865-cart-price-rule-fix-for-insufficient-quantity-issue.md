---
title: 'ACSD-59865 : [!UICONTROL Cart Price Rule] ne parvient pas à annuler les règles précédentes en raison d''une quantité de produit insuffisante'
description: Appliquez le correctif ACSD-59865 pour résoudre le problème d’Adobe Commerce où la valeur *l’étape de quantité de remise* dans *la remise de montant fixe*,* *le pourcentage de la remise sur le prix du produit* et *l’achat X obtient Y* [!UICONTROL Cart Price Rules] n’annule plus l’action des règles précédentes.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865 : [!UICONTROL Cart Price Rule] ne parvient pas à annuler les règles précédentes en raison d&#39;une quantité de produit insuffisante

Le correctif ACSD-59865 corrige le problème où la valeur *[!UICONTROL Discount quantity step]* en *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* et *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] n’annule plus l’action des règles précédentes. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59865. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La [!UICONTROL Cart Price Rule] ne parvient pas à annuler les règles précédemment appliquées en raison d’une quantité de produit insuffisante dans le panier.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** et cliquez sur **[!UICONTROL Add New rule]**.
   * Définir **[!UICONTROL Rule Name]** = *Test - 1*
   * Sélectionnez tous les *Sites web* et *Groupes de clients*.
   * Définir **[!UICONTROL Priority]** = *0*
   * Accédez à la section **[!UICONTROL Actions]** :
      * Définir **[!UICONTROL Apply]** = *pourcentage de remise sur le prix du produit*
      * Définir **[!UICONTROL Discount amount]** = *10*
      * Définir **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Définir **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Définissez **[!UICONTROL Discard subsequent rules]** sur *Non*
1. Effacez le cache.
1. Accédez à la vitrine , ajoutez un article au panier, puis passez à *passage en caisse/panier*.
1. Vérifiez que la remise de *10 %* est appliquée à votre panier.
1. Revenez à la **[!UICONTROL Cart Price Rules]** et créez une règle.
   * Définir **[!UICONTROL Rule Name]** = *Test - 2*
   * Sélectionner tous les **[!UICONTROL Websites]** et **[!UICONTROL Customer Groups]**
   * Définir **[!UICONTROL Priority]** = *2*
   * Accédez à la section **[!UICONTROL Actions]** :
      * Définir **[!UICONTROL Apply]** = *pourcentage de remise sur le prix du produit*
      * Définir **[!UICONTROL Discount amount]** = *20*
      * Définir **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Définir **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Effacez le cache.
1. Retournez sur la vitrine.
1. Mettez à jour le panier pour actualiser les règles. Vérifiez que la remise de *10 %* n&#39;est plus appliquée.
1. Ajoutez des articles au panier jusqu’à ce que la quantité atteigne la valeur *Étape* requise pour la deuxième règle.

<u>Résultats attendus</u> :

La première [!UICONTROL Cart Price Rule] est appliquée lorsque les conditions de la deuxième règle sont remplies.

<u>Résultats réels</u> :

Les règles de prix sont appliquées telles que configurées dans le tableau de bord d’administration.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
