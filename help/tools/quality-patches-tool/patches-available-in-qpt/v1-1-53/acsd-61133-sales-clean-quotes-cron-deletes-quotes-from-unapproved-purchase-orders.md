---
title: "ACSD-61133: &grave;sales_clean_citations&grave; cron supprime les guillemets des commandes non approuvées"
description: Appliquez le correctif ACSD-61133 pour résoudre le problème Adobe Commerce en raison duquel le cron "sales_clean_citations" supprime les guillemets des commandes non approuvées.
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 67b1dd3d4814b487d47a25697ed21d60f1e4e378
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133 : `sales_clean_quotes` le cron supprime les guillemets des commandes non approuvées

Le correctif ACSD-61133 corrige le problème en raison duquel le cron `sales_clean_quotes` supprime les guillemets des commandes non approuvées. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé. L’ID de correctif est ACSD-61133. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 et 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`sales_clean_quotes` cron supprime les guillemets des commandes non approuvées. Le *[bon de commande B2B]* ne peut pas être converti dans l’ordre du guillemet associé à la commande achetée, car le cron le supprime.

<u>Conditions préalables</u> :

Les modules Adobe Commerce [!UICONTROL B2B] sont installés et activés.

<u>Étapes à reproduire</u> :

1. Activez la fonctionnalité *[!UICONTROL B2B Purchase Order]* .
1. Créez une société.
1. Créez un *[!UICONTROL Purchase Order]*.
1. Attendez que le guillemet expire et soit supprimé par le cron. La période d’expiration de la citation peut être définie avec **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**.
1. Convertissez *[!UICONTROL Purchase Order]* à l&#39;ordre par le biais de *[!UICONTROL My Purchase Order in Customer Dashboard]* ou avec une mutation [!DNL GraphQL] `placeOrderForPurchaseOrder`.

<u>Résultats attendus</u> :

Le guillemet associé à l’actif *[!UICONTROL Purchase Order]* n’est pas supprimé comme expiré par le cron. La commande est correctement placée sur le storefront ou via [!DNL GraphQL].

<u>Résultats réels</u> :

La commande n’est pas placée et une erreur s’affiche sur le storefront ou est renvoyée dans la réponse [!DNL GraphQL].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
