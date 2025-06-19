---
title: 'ACSD-55610 : la commande partiellement annulée a un montant de remise incorrect'
description: Appliquez le correctif ACSD-55610 pour résoudre le problème d’Adobe Commerce en raison duquel une commande partiellement annulée bénéficie d’un montant de remise incorrect.
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: b7b94c9d-e027-4601-837b-d70b7ff8bd2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55610 : la commande partiellement annulée a un montant de remise incorrect

Le correctif ACSD-55610 corrige le problème où une commande partiellement annulée a un montant de remise incorrect. Ce correctif est disponible lorsque la version 1.1.43 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-55610. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une commande partiellement annulée a un montant de remise incorrect.

<u>Procédure à suivre </u> :

1. Créez une règle de prix de panier.

   * *[!UICONTROL Rule Name]* : *Vente d&#39;hiver*
   * *[!UICONTROL Active]* = *Oui*
   * *[!UICONTROL Websites]* = *Site web principal*
   * Choisissez tous les groupes de clients.
   * Sélectionnez un coupon spécifique.
   * *[!UICONTROL Coupon Code]* : *WINTER10*
   * *[!UICONTROL Conditions]* : *[!UICONTROL If ALL of these conditions are TRUE]* : *Sous-Total(Excl. Taxe) est égal ou supérieur à 75*
   * Appliquez *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]* : *10*
   * *[!UICONTROL Discard subsequent rules]* : *Oui*

1. Créez trois produits dont le prix est défini sur 100.
1. Ajoutez les trois produits au panier.
1. Appliquez le coupon.
1. Passez la commande.
1. Facturer un article de la commande et l&#39;expédier.
1. Annulez les deux autres éléments.
1. Vérifiez la colonne `base_discount_canceled` .

<u>Résultats attendus</u> :

Le montant de la remise en `base_discount_cancelled` est correctement reflété.

<u>Résultats réels</u> :

La `base_discount_cancelled` n&#39;est pas correcte.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
