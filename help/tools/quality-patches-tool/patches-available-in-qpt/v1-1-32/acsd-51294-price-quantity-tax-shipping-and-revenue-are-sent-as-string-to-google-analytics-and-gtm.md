---
title: 'ACSD-51294 : prix, quantité, taxe, expédition, recettes envoyées sous forme de chaîne à  [!DNL Google Analytics] et GTM'
description: Appliquez le correctif ACSD-51294 pour résoudre le problème Adobe Commerce en raison duquel le prix, la quantité, la taxe, l’expédition et les recettes sont envoyés sous forme de chaîne à  [!DNL Google Analytics] et à GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51294 : prix, quantité, taxe, expédition, recettes envoyées sous forme de chaîne à [!DNL Google Analytics] et GTM.

Le correctif ACSD-51294 corrige le problème en raison duquel le prix, la quantité, la taxe, l’expédition et les recettes sont envoyés sous forme de chaîne à [!DNL Google Analytics] et à GTM. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.32 est installé. L’ID de correctif est ACSD-51294. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix, la quantité, la taxe, l’expédition et les recettes sont envoyés sous la forme d’une chaîne à [!DNL Google Analytics] et à GTM.

<u>Étapes à reproduire</u> :

1. Configurez [!DNL Google Tag Manager] en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Créez un produit simple.
3. Effectuez le paiement avec ce produit.
4. Vérifiez la variable JavaScript `dataLayer` sur la page de succès du passage en caisse.

<u>Résultats attendus</u>

Les valeurs de prix et de quantité sont numériques.

<u>Résultats réels</u>

Les valeurs de prix et de quantité sont des chaînes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].
