---
title: 'ACSD-54680 : impossible de traiter le devis B2B d’un produit avec plusieurs sources affectées'
description: Appliquez le correctif ACSD-54680 pour résoudre le problème d’Adobe Commerce en raison duquel le devis B2B d’un produit avec plusieurs sources affectées ne peut pas être traité.
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680 : impossible de traiter le devis B2B pour un produit avec plusieurs sources affectées.

Le correctif ACSD-54680 corrige le problème en raison duquel le devis B2B d’un produit avec plusieurs sources affectées ne peut pas être traité. Ce correctif est disponible lorsque la version 1.1.40 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-54680. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de traiter le devis B2B pour un produit avec plusieurs sources affectées.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** et créez deux nouvelles sources : **Source 1** et **Source 2**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** et créez un stock : **Stock A**, affectez-le au site web principal, puis affectez-lui **Source 1** et **Source 2**.
1. Créez un produit Simple, attribuez **Source 1** et **Source 2**, puis définissez Qté = *2* pour chaque source. (la quantité commercialisable du produit doit donc être de *4*).
1. Créez un compte d’entreprise.
1. Accédez à la **[!UICONTROL Storefront]** et connectez-vous au compte d’entreprise .
1. Ajoutez le produit simple au panier avec qty = *4*.
1. Ouvrez le *[!UICONTROL Shopping cart]* et cliquez sur **[!UICONTROL Request a quote]** bouton .
1. Ajoutez un nom de commentaire et de citation, puis cliquez sur **[!UICONTROL Send a Request]** bouton.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Ouvrir le devis récemment envoyé.

<u>Résultats attendus</u> :

Les articles cités contiennent le produit commandé.

<u>Résultats réels</u> :

La section de page des articles cités est vide et il n&#39;est pas possible de traiter le devis.
`var/log/system.log` contient

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
