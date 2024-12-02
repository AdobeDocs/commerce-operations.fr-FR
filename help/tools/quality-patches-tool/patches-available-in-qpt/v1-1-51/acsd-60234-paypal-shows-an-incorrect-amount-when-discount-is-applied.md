---
title: 'ACSD-60234: [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée'
description: Appliquez le correctif ACSD-60234 pour résoudre le problème Adobe Commerce où  [!DNL PayPal]  affiche un montant incorrect lorsque la remise est appliquée par le biais du mode de paiement.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234 : [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée

Le correctif ACSD-60234 corrige le problème où [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée par le biais du mode de paiement. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé. L’ID de correctif est ACSD-60234. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée par le biais du mode de paiement.

<u>Étapes à reproduire</u> :

1. Configurez *[!DNL PayPal Express]* dans **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] peut être [!UICONTROL Yes] ou [!UICONTROL NO], le problème se reproduit dans les deux scénarios.
1. Créez un *[!UICONTROL Cart Rule]* dans **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Condition : si toutes ces conditions sont vraies : *[!UICONTROL Payment Method]* est *[!DNL PayPal Express Checkout]*.
   * Actions : toute action.
1. Créez un produit.
1. Accédez au storefront, ajoutez le produit au panier, puis à l’étape **[!UICONTROL Payment Method]** du passage en caisse.
1. Veillez à sélectionner *[!DNL PayPal Express]* et à vérifier que la remise est correctement appliquée.
1. Cliquez sur le bouton **[!DNL PayPal]** .
1. Connectez-vous et observez le contenu de la fenêtre contextuelle.

<u>Résultats attendus</u> :

Le montant à payer transmis à [!DNL PayPal] inclut la remise telle qu&#39;elle est dans le panier.

<u>Résultats réels</u> :

Le montant total à payer n&#39;inclut pas la remise.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
