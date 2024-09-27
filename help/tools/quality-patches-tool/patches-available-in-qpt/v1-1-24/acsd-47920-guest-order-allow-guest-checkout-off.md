---
title: '''ACSD-47920 : un utilisateur invité peut passer des commandes via l''API REST même si [!UICONTROL Allow Guest Checkout] est désactivé'''
description: Appliquez le correctif ACSD-47920 pour résoudre le problème Adobe Commerce en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité même lorsque l’événement [!UICONTROL Allow Guest Checkout] est désactivé.
feature: REST, Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920 : un utilisateur invité peut passer des commandes via l&#39;API REST même lorsque **[!UICONTROL Allow Guest Checkout]** est désactivé.

Le correctif ACSD-47920 corrige le problème en raison duquel les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité, même lorsque l’ **[!UICONTROL Allow Guest Checkout]** est désactivé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 est installé. L’ID de correctif est ACSD-47920. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les commandes peuvent être placées via l’API REST en tant qu’utilisateur invité, même si l’option **[!UICONTROL Allow Guest Checkout]** est désactivée.

<u>Étapes à reproduire</u> :

1. Accédez à Admin Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > et définissez le **[!UICONTROL Allow Guest Checkout]** sur _Non_.
1. Utilisez l’API REST pour ajouter un produit à un panier et passer une commande.

<u>Résultats attendus</u> :

L’API de passage en caisse des invités renvoie une erreur *[!UICONTROL Sorry, guest checkout is not available]* si **[!UICONTROL Allow Guest Checkout]** est défini sur _Non_.

<u>Résultats réels</u> :

L’API de passage en caisse des invités permet de passer une commande même si **[!UICONTROL Allow Guest Checkout]** est défini sur _Non_.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
