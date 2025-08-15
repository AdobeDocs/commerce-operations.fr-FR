---
title: 'ACSD-58163 : [!UICONTROL Cart Price Rule] n’applique pas de remise provenant du panier [!UICONTROL Customer Segment] correspondant sans code de coupon'
description: Appliquez le correctif ACSD-58163 pour résoudre le problème d’Adobe Commerce où le [!UICONTROL Cart Price Rule] n’applique pas de remise pour un invité du panier de [!UICONTROL Customer Segment] correspondant sans code de coupon.
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163 : [!UICONTROL Cart Price Rule] n’applique pas de remise provenant du panier [!UICONTROL Customer Segment] correspondant sans code de coupon

Le correctif ACSD-58163 corrige le problème où le [!UICONTROL Cart Price Rule] n’applique pas de remise du panier de [!UICONTROL Customer Segment] correspondant sans code de coupon. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-58163. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!UICONTROL Cart Price Rule] n’applique pas de réduction pour un invité du panier d’[!UICONTROL Customer Segment] correspondant sans code de coupon.

<u>Procédure à suivre </u> :

1. Créer un segment client :
   * Pour les visiteurs.
   * À la condition qu’un produit figure dans le panier.

1. Créez un *[!UICONTROL Cart Price Rule]* :
   * Sans code de coupon.
   * Avec la condition à faire correspondre au segment client visiteur.

1. Créez un produit simple.
1. Ouvrez le storefront en tant qu’invité.
1. Ajoutez un produit simple au panier.
1. Accédez au panier.

<u>Résultats attendus</u> :

*[!UICONTROL Cart Price Rule]* remise est appliquée.

<u>Résultats réels</u> :

*[!UICONTROL Cart Price Rule]* remise n&#39;est pas appliquée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
