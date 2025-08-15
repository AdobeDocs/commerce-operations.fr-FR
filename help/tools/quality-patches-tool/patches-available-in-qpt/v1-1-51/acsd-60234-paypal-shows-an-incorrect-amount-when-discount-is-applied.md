---
title: 'ACSD-60234: [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée'
description: Appliquez le correctif ACSD-60234 pour résoudre le problème d’Adobe Commerce où  [!DNL PayPal]  affiche un montant incorrect lorsque la remise est appliquée via le mode de paiement.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234 : [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée

Le correctif ACSD-60234 corrige le problème où [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée via le mode de paiement. Ce correctif est disponible lorsque la version 1.1.51 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-60234. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée par le biais du mode de paiement.

<u>Procédure à suivre </u> :

1. Configurez les *[!DNL PayPal Express]* dans **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] peut être [!UICONTROL Yes] ou [!UICONTROL NO], le problème se reproduit dans les deux scénarios.
1. Créez un *[!UICONTROL Cart Rule]* dans **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Condition : si toutes ces conditions sont vraies : *[!UICONTROL Payment Method]* est *[!DNL PayPal Express Checkout]*.
   * Actions : toutes les actions.
1. Créez un produit.
1. Accédez à la vitrine, ajoutez le produit au panier, puis passez à l’étape **[!UICONTROL Payment Method]** du passage en caisse.
1. Veillez à sélectionner *[!DNL PayPal Express]* et à vérifier que la remise est correctement appliquée.
1. Cliquez sur le bouton **[!DNL PayPal]** .
1. Connectez-vous et observez le contenu de la fenêtre contextuelle.

<u>Résultats attendus</u> :

Le montant à payer transmis à [!DNL PayPal] inclut la remise telle qu’elle figure dans le panier.

<u>Résultats réels</u> :

Le montant total à payer n&#39;inclut pas la remise.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
