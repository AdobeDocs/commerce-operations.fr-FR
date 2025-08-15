---
title: 'ACSD-49042 : produit avec arriéré infini ne peut pas être commandé depuis le storefront'
description: Appliquez le correctif ACSD-49042 pour résoudre le problème d’Adobe Commerce en raison duquel un produit avec une commande en souffrance infinie ne peut pas être commandé depuis le storefront.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49042 : produit avec arriéré infini ne peut pas être commandé depuis le storefront

Le correctif ACSD-49042 corrige le problème où un produit avec une commande infinie ne peut pas être commandé depuis le storefront. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49042. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur se produit lorsqu’un produit avec une commande en souffrance infinie ne peut pas être commandé depuis le storefront.

<u>Procédure à suivre </u> :

1. Définissez les paramètres de configuration suivants :
   * **[!UICONTROL Display Out of Stock Products]** défini sur *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** défini sur *[!UICONTROL Allow Qty Below 0]*.
1. Ajoutez une nouvelle **[!DNL custom stock]** et un nouveau **[!DNL custom source]**.
1. Attribuez un produit au **[!DNL custom source]** et assurez-vous qu’un numéro d’inventaire est défini pour lui (par exemple : *10*).
1. Sur la page de modification du produit, ouvrez **[!UICONTROL Advanced Inventory]**. Définissez le **[!UICONTROL minimum quantity]** dans le panier (par exemple : *160*). La quantité doit être supérieure au stock.
1. Allez à la vitrine et achetez un produit pour créer une réservation.
1. Remplacez le **[!UICONTROL product quantity]** par *0*. Le point essentiel est d’enregistrer le produit sur le **[!DNL Admin panel]** en cas de réservation.
1. Ouvrez le **[!UICONTROL product page]** sur le storefront et essayez d’ajouter le produit au panier.

<u>Résultats attendus</u> :

Il est possible d’ajouter le produit au panier, car les reliquats pour une quantité inférieure à *0* sont autorisés.

<u>Résultats réels</u> :

Le produit s’affiche comme étant en rupture de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
