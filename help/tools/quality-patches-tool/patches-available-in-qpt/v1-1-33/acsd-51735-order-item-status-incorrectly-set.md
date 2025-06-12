---
title: 'ACSD-51735 : le statut de l''article de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est égal à 0'
description: Appliquez le correctif ACSD-51735 pour résoudre le problème d’Adobe Commerce où le statut de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est de 0.
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-51735 : le statut de l&#39;article de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est de 0

Le correctif ACSD-51735 corrige le problème en raison duquel le statut de l’article de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est égal à 0. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50895. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut de l&#39;article de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produits est égal à 0.

<u>Conditions préalables</u> :

* Les modules Adobe Commerce Inventory management (MSI) sont installés.
* Les reliquats sont activés dans **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Procédure à suivre </u> :

1. Créez un nouveau stock.
1. Créez une nouvelle source.
1. Affectez le site web par défaut au nouveau stock et affectez la nouvelle source.
1. Créez un produit.

   * Définissez la quantité source par défaut sur 10 et la nouvelle quantité source sur 0.

1. Ajoutez le produit au panier sur la vitrine.
1. Observez l’avertissement de backorder lors du passage en caisse, indiquant que le produit provient d’une nouvelle source.
1. Passez la commande.
1. Ouvrez la commande dans Admin et vérifiez l’état de la commande en attente.

<u>Résultats attendus</u> :

La commande indique que la Qté 1 est en reliquat.

<u>Résultats réels</u> :

La commande indique que la Qté 1 est commandée, et non en différé.

>[!MORELIKETHIS]
>
>[Le statut de l&#39;article de commande est incorrectement défini sur *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
