---
title: 'ACSD-47920 : un utilisateur invité peut passer des commandes via l’API REST même lorsque l’[!UICONTROL Allow Guest Checkout] est désactivée'
description: Appliquez le correctif ACSD-47920 pour résoudre le problème d’Adobe Commerce où les commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même lorsque l’[!UICONTROL Allow Guest Checkout] est désactivé.
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920 : un utilisateur invité peut passer des commandes via l’API REST même lorsque l’**[!UICONTROL Allow Guest Checkout]** est désactivée

Le correctif ACSD-47920 corrige le problème où les commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même lorsque le **[!UICONTROL Allow Guest Checkout]** est désactivé. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47920. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des commandes peuvent être passées via l’API Rest en tant qu’utilisateur invité, même si l’**[!UICONTROL Allow Guest Checkout]** est désactivé.

<u>Procédure à suivre </u> :

1. Accédez à Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > et définissez la **[!UICONTROL Allow Guest Checkout]** sur _Non_.
1. Utilisez l’API REST pour ajouter un produit à un panier et passer une commande.

<u>Résultats attendus</u> :

L’API de passage en caisse des invités renvoie un *[!UICONTROL Sorry, guest checkout is not available]* d’erreur si **[!UICONTROL Allow Guest Checkout]** est définie sur _Non_.

<u>Résultats réels</u> :

L’API de passage en caisse des invités permet de passer une commande même si **[!UICONTROL Allow Guest Checkout]** est défini sur _Non_.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
