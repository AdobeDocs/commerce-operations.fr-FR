---
title: 'ACSD-56616 : affichage en vitrine des produits groupés en cas de simple rupture de stock'
description: Appliquez le correctif ACSD-56616 pour résoudre le problème d’Adobe Commerce où des produits groupés apparaissent de manière inattendue sur le storefront lorsque tous les produits simples associés sont en rupture de stock.
feature: Products
role: Admin, Developer
exl-id: 8b225d9d-1898-4c4d-81be-7b92cbf7d06f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-56616 : affichage en vitrine des produits groupés en cas de simple rupture de stock.

Le correctif ACSD-56616 corrige le problème d’apparition inattendue de produits groupés sur le storefront lorsque tous les produits simples associés sont en rupture de stock. Ce correctif est disponible lorsque la version 1.1.45 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56616. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Affichage incorrect de la vitrine des produits groupés lors d’une simple pénurie de stock.

<u>Procédure à suivre </u> :

1. Créez un site web/magasin/storefront.
1. Créez une nouvelle source.
1. Créez un nouveau stock et affectez-le au site web nouvellement créé.
1. Configurez les indexeurs pour qu’ils se mettent à jour selon le calendrier.
1. Générez deux produits simples, S1 (qté = 1) et S2 (qté = 1), et affectez-les au nouveau stock et au nouveau site web.
1. Créez un produit *groupé1* et associez-le à un nouveau site web, en le plaçant dans la catégorie *CAT*.
1. Définissez deux options de liste déroulante requises et liez le produit simple *S1* à l’option1 et *S2* à l’option2.
1. Enregistrez les produits.
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** et activez *Ajouter le code de magasin à l’URL* = *Oui*.
1. Ouvrez le storefront et achetez le produit groupé.
1. Exécutez cron deux fois.
1. Revenez à la catégorie *CAT*.

<u>Résultats attendus</u> :

Le produit *bundle1* est en rupture de stock.

<u>Résultats réels</u> :

Le produit *bundle1* est visible avec un prix = *$0*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
