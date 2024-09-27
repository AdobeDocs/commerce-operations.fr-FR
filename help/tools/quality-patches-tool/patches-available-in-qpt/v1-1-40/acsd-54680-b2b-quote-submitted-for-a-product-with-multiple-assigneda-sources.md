---
title: "ACSD-54680 : Citation B2B pour un produit avec plusieurs sources affectées impossible à traiter"
description: Appliquez le correctif ACSD-54680 pour résoudre le problème Adobe Commerce en raison duquel le devis B2B pour un produit avec plusieurs sources affectées ne peut pas être traité.
feature: B2B
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680 : Il n’est pas possible de traiter les guillemets B2B d’un produit avec plusieurs sources affectées.

Le correctif ACSD-54680 corrige le problème en raison duquel le devis B2B d’un produit avec plusieurs sources affectées ne peut pas être traité. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.40 est installé. L’ID de correctif est ACSD-54680. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Il n’est pas possible de traiter les guillemets B2B d’un produit avec plusieurs sources affectées.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** et créez deux nouvelles sources : **Source 1** et **Source 2**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** et créez un nouveau Stock : **Stock A**, affectez-le au site web principal, puis affectez **Source 1** et **Source 2** à ce dernier.
1. Créez un produit Simple, affectez **Source 1** et **Source 2**, puis définissez Qty = *2* pour chaque source. (la quantité vendable du produit doit donc être *4*).
1. Créez un compte d’entreprise.
1. Accédez à **[!UICONTROL Storefront]** et connectez-vous au compte de la société.
1. Ajoutez le produit simple au panier avec qty = *4*.
1. Ouvrez le *[!UICONTROL Shopping cart]* et cliquez sur le bouton **[!UICONTROL Request a quote]**.
1. Ajoutez un nom de commentaire et de guillemet cliquez sur le bouton **[!UICONTROL Send a Request]** .
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Ouvrez une citation récemment envoyée.

<u>Résultats attendus</u> :

Les articles cités contiennent le produit commandé.

<u>Résultats réels</u> :

La section de page éléments entre guillemets est vide et il n’est pas possible de traiter le guillemet.
`var/log/system.log` contient

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
