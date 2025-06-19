---
title: 'ACSD-46617 : **[!UICONTROL Continue to Checkout]** bouton grisé lorsque le sous-total est supérieur au montant minimum de commande configuré'
description: Appliquez le correctif ACSD-46617 pour résoudre le problème d’Adobe Commerce où le bouton **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617 : le bouton « [!UICONTROL Continue to Checkout] » est grisé lorsque le sous-total est supérieur à « [!UICONTROL Minimum Order Amount] »

Ce correctif ACSD-46617 résout le problème où le bouton **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant de commande minimum configuré. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46617. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le bouton **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré.

<u>Procédure à suivre </u> :

1. Accédez à Admin Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** et définissez les éléments suivants :
   * [!UICONTROL Enable] : *[!UICONTROL Yes]*
   * &#x200B;

     [!UICONTROL Minimum Amount]: *2*

1. Créez un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code] : *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions] : *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions] :
      * [!UICONTROL Apply] : *[!UICONTROL Percent of product price discount]*
      * &#x200B;

        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount] : *[!UICONTROL Yes]*
1. Créez un produit au prix de 25 $.
1. Ajoutez le produit au panier.
1. Accédez au panier, sélectionnez la méthode $5 **[!UICONTROL Flat Rate shipping]** et appliquez le code de coupon.
1. Accédez à la commande, effectuez l’expédition, puis accédez à la section **[!UICONTROL Paytment]** .
1. Revenez au panier.

<u>Résultats attendus</u> :

Il n&#39;y a pas d&#39;erreur liée au montant minimum de la commande, car le total général de 2,4 $ est supérieur au montant requis de 2 $.

<u>Résultats réels</u> :

* Il y a une erreur liée au montant minimum de la commande même lorsque le total général de 2,4 $ est supérieur au montant minimum de la commande de 2 $.
* Le bouton **[!UICONTROL Continue to Checkout]** est grisé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
