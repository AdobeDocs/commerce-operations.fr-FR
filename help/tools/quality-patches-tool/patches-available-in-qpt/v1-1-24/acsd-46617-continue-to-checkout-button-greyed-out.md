---
title: 'Bouton ACSD-46617 : **[!UICONTROL Continue to Checkout]** grisé lorsque le sous-total est supérieur au montant minimum de commande configuré.'
description: Appliquez le correctif ACSD-46617 pour résoudre le problème Adobe Commerce où le bouton **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Bouton ACSD-46617 : &quot;[!UICONTROL Continue to Checkout]&quot; grisé lorsque le sous-total est supérieur à &quot;[!UICONTROL Minimum Order Amount]&quot;

Ce correctif ACSD-46617 résout le problème où le bouton **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-46617. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le bouton **[!UICONTROL Continue to Checkout]** est grisé même si le sous-total est supérieur au montant minimum de commande configuré.

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur Adobe Commerce > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** et définissez les options suivantes :
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
1. Créez un produit au prix de 25 €.
1. Ajoutez le produit au panier.
1. Accédez au panier, sélectionnez la méthode $5 **[!UICONTROL Flat Rate shipping]** et appliquez le code de coupon.
1. Accédez au passage en caisse, effectuez l’expédition et accédez à la section **[!UICONTROL Paytment]** .
1. Retournez dans le panier.

<u>Résultats attendus</u> :

Aucune erreur n’est liée au montant minimum de la commande, car le total général de 2,4 $ est supérieur au montant requis de 2 $.

<u>Résultats réels</u> :

* Une erreur s’est produite lors de la création du montant minimum de commande, même si le total général de 2,4 $ est supérieur au montant minimum de commande de 2 $.
* Le bouton **[!UICONTROL Continue to Checkout]** est grisé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
