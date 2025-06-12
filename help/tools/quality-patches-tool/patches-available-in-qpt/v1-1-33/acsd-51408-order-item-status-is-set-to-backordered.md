---
title: 'ACSD-51408 : le statut de l''article de commande est incorrectement défini sur [!UICONTROL backordered]'
description: Appliquez le correctif ACSD-51408 pour résoudre le problème d’Adobe Commerce où le statut de l’élément de commande est incorrectement défini sur [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 51abb4c6-5618-43a5-89ca-a3879be2c3c4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-51408 : le statut de l&#39;article de commande est incorrectement défini sur *[!UICONTROL backordered]*

Le correctif ACSD-51408 corrige le problème en raison duquel le statut de l’élément de commande est incorrectement défini sur [!UICONTROL backordered]. Ce correctif est disponible lorsque la version 1.1.33 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51408. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut de l&#39;élément de commande est incorrectement défini sur *[!UICONTROL backordered]*.

<u>Conditions préalables</u> :

Les modules Adobe Commerce B2B et Inventory management (MSI) sont installés.

<u>Procédure à suivre </u> :

1. Créez un site web, un magasin et une vue de magasin.
1. Créez une nouvelle source.
1. Créez un nouveau stock lié au nouveau site web créé à l’étape 1 et attribuez la source créée à l’étape 2.
1. Créez une entreprise et affectez-la au nouveau site web créé à l’étape 1.
1. Créez un nouveau client et affectez-le à la société créée à l’étape 4.
1. Créez un produit, affectez-le au nouveau site web et définissez la **[!UICONTROL default stock]** = *0* et la **[!UICONTROL new stock]** sur une valeur supérieure à *0*.
1. Activez **[!UICONTROL backorders]**.
1. Activez **[!UICONTROL Check/Money Order]** mode de paiement pour la nouvelle étendue de site web.
1. Activez le **[!UICONTROL Flat Rate shipping method]** pour la nouvelle portée du site web.
1. Créez une commande à partir de **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Sélectionnez le nouveau client créé à l’étape 5.
1. Sélectionnez le nouveau magasin créé à l’étape 1.
1. Choisissez le produit créé à l’étape 6.
1. Renseignez les informations de la commande, y compris les modes de paiement et d’expédition.
1. Soumettez la commande.
1. Vérifiez le *Statut de l’élément*.

<u>Résultats attendus</u>

L&#39;article peut être expédié à partir du stock. Le statut de l’élément est *[!UICONTROL ordered]*.

<u>Résultats réels</u>

Le statut de l’élément est *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[Le statut de l&#39;article de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est de 0,](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
