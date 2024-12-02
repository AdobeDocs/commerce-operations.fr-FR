---
title: 'ACSD-56616 : Affichage storefront de produits groupés lors d’une simple pénurie de stock'
description: Appliquez le correctif ACSD-56616 pour résoudre le problème Adobe Commerce en raison duquel les produits regroupés apparaissent de manière inattendue sur le storefront lorsque tous les produits simples associés sont en rupture de stock.
feature: Products
role: Admin, Developer
exl-id: 8b225d9d-1898-4c4d-81be-7b92cbf7d06f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-56616 : Affichage storefront de produits groupés lors d’une simple pénurie de stock.

Le correctif ACSD-56616 corrige le problème en raison duquel les produits regroupés apparaissent de manière inattendue sur le storefront lorsque tous les produits simples associés sont en rupture de stock. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 est installé. L’ID de correctif est ACSD-56616. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Affichage incorrect de la vitrine des produits groupés lors d’une simple pénurie de stock.

<u>Étapes à reproduire</u> :

1. Créez un site web/magasin/storefront.
1. Créez une source.
1. Créez un nouveau stock et affectez-le au site web nouvellement créé.
1. Configurez les indexeurs à mettre à jour selon le calendrier.
1. Générez deux produits simples, S1 (qty = 1) et S2 (qty = 1), et affectez-les au nouveau stock et au nouveau site web.
1. Créez un produit *bundled1* et associez-le au nouveau site web, en le plaçant dans la catégorie *CAT*.
1. Définissez deux options de liste déroulante requises et liez le produit simple *S1* à l’option1 et *S2* à l’option2.
1. Enregistrez les produits.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** et activez l’option *Ajouter le code de magasin à l’URL* = *Oui*.
1. Ouvrez le storefront et achetez le produit fourni.
1. Exécutez cron deux fois.
1. Revenez à la catégorie *CAT*.

<u>Résultats attendus</u> :

Le produit *bundle1* est en rupture de stock.

<u>Résultats réels</u> :

Le produit *bundle1* est visible avec price = *$0*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
