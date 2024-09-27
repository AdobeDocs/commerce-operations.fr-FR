---
title: '''ACSD-47232 : le coupon n''est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché'''
description: Appliquez le correctif ACSD-47232 pour résoudre le problème Adobe Commerce où le coupon n’est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché.
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232 : le coupon n&#39;est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché

Le correctif ACSD-47232 corrige le problème lorsque le coupon n&#39;est pas appliqué lorsque **[!UICONTROL Same as Billing Address]** est coché. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 est installé. L’ID de correctif est ACSD-47232. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le coupon n&#39;est pas appliqué lorsque **[!UICONTROL Same as Billing Address]** est coché.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce.
1. Créez un produit simple avec un poids = *8*.
1. Créez un client avec l’adresse de facturation et de livraison par défaut.
1. Créez une règle de prix de panier avec un coupon.
   * Dans les sections **[!UICONTROL Conditions]**, ajoutez *Poids total égal ou supérieur à 5*
1. Essayez de créer une nouvelle commande dans l’administrateur [!UICONTROL Commerce].
   * Utilisez le client créé tout à l’heure
   * Ajout d’un produit
   * Essayer d&#39;appliquer le coupon

<u>Résultats attendus</u> :

Le coupon est appliqué.

<u>Résultats réels</u> :

Vous obtenez une erreur similaire à la suivante : *Le code de bon 123 n’est pas valide. Vérifiez le code et réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
