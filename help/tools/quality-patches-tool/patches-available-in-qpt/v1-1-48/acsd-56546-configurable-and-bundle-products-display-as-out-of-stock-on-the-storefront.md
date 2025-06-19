---
title: 'ACSD-56546 : les produits configurables et groupés s''affichent comme étant en rupture de stock sur le storefront'
description: Appliquez le correctif ACSD-56546 pour résoudre le problème d’Adobe Commerce où les produits configurables et groupés s’affichent comme étant en rupture de stock sur le storefront lorsque l’option de configuration *[!UICONTROL Display Out of Stock Products]* est désactivée.
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546 : les produits configurables et groupés s&#39;affichent comme étant en rupture de stock sur le storefront

Le correctif ACSD-56546 corrige le problème où les produits configurables et groupés s’affichent comme étant en rupture de stock sur le storefront. Ce correctif est disponible lorsque la version 1.1.48 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56546. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables et groupés s’affichent comme étant en rupture de stock sur le storefront lorsque *[!UICONTROL Display Out of Stock Products]* option est désactivée.

<u>Procédure à suivre </u> :

1. Définissez l’option **[!UICONTROL Display Out of Stock Products]** sur *Non*.
1. Créez un site web, un magasin et une révision de magasin.
1. Créez une source et un stock, puis affectez-les au second site web.
1. Créez un *produit configurable* avec deux produits enfants. Attribuez les deux produits enfants aux deux sources et aux deux sites web.
1. Mettez à jour le premier produit enfant pour qu&#39;il ait *qty=0* dans les deux sources.
1. Mettez à jour le deuxième produit enfant et désactivez-le sur le deuxième site web.
1. Effectuez une réindexation complète.
1. Vérifiez la catégorie qui contient le produit configurable sur le deuxième site web.

<u>Résultats attendus</u> :

Les produits configurables en rupture de stock ne sont pas visibles sur le storefront.

<u>Résultats réels</u> :

Les produits configurables en rupture de stock sont visibles sur le storefront même lorsque l’option *[!UICONTROL Display Out of Stock Products]* est désactivée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
