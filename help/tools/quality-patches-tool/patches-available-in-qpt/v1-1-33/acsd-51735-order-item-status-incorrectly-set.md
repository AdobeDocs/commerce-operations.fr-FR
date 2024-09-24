---
title: 'ACSD-51735 : l’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est 0'
description: Appliquez le correctif ACSD-51735 pour résoudre le problème Adobe Commerce en raison duquel l’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est 0.
feature: Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-51735 : l’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est 0

Le correctif ACSD-51735 corrige le problème en raison duquel l’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est 0. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 est installé. L’ID de correctif est ACSD-50895. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Ordered]* lorsque le stock de produit est de 0.

<u>Conditions préalables</u> :

* Les modules Adobe Commerce Inventory management (MSI) sont installés.
* Les commandes d’arrière-plan sont activées dans **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Étapes à reproduire</u> :

1. Créez un nouveau stock.
1. Créez une source.
1. Affectez le site web par défaut au nouveau stock et affectez la nouvelle source.
1. Créez un produit.

   * Définissez la quantité source par défaut sur 10 et la nouvelle quantité source sur 0.

1. Ajoutez le produit au panier sur le storefront.
1. Observez l’avertissement de commande arrière lors du passage en caisse, indiquant que le produit provient d’une nouvelle source.
1. Placez la commande.
1. Ouvrez la commande dans Admin, puis vérifiez l’état de l’en-tête.

<u>Résultats attendus</u> :

L’ordre indique que la quantité 1 est en ordre inverse.

<u>Résultats réels</u> :

L’ordre indique que la Qté 1 est classée, et non en ordre inverse.

>[!MORELIKETHIS]
>
>[L’état de l’élément de commande est incorrectement défini sur *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
