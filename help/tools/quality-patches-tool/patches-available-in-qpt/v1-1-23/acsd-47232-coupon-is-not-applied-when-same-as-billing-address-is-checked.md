---
title: 'ACSD-47232 : le coupon n’est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché'
description: Appliquez le correctif ACSD-47232 pour résoudre le problème d’Adobe Commerce en raison duquel le coupon n’est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché.
feature: Orders, Shipping/Delivery
role: Admin
exl-id: d8050f6e-00a9-4aa3-bb8b-1631e0e7a714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-47232 : le coupon n’est pas appliqué lorsque [!UICONTROL Same as Billing Address] est coché

Le correctif ACSD-47232 corrige le problème où le coupon n’est pas appliqué lorsque **[!UICONTROL Same as Billing Address]** est coché. Ce correctif est disponible lorsque la version 1.1.23 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47232. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le coupon n’est pas appliqué lorsque **[!UICONTROL Same as Billing Address]** est coché.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce.
1. Créez un produit simple avec un poids = *8*.
1. Créez un nouveau client avec l’adresse de facturation et d’expédition par défaut.
1. Créez une règle de prix de panier avec un coupon.
   * Dans **[!UICONTROL Conditions]** sections, ajoutez *Poids total égal ou supérieur à 5*
1. Essayez de créer une nouvelle commande dans l’administrateur [!UICONTROL Commerce].
   * Utiliser le client créé à l’instant
   * Ajouter un produit
   * Essayez d’appliquer le coupon

<u>Résultats attendus</u> :

Le coupon est appliqué.

<u>Résultats réels</u> :

Vous obtenez une erreur similaire à celle-ci : *Le code du coupon de 123 n’est pas valide. Vérifiez le code et réessayez.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
