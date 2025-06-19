---
title: 'ACSD-50345 : problèmes reCAPTCHA lors de l’extraction'
description: Appliquez le correctif ACSD-50345 pour résoudre le problème d’Adobe Commerce où les validations reCAPTCHA v2 et v3 ont échoué lors du passage des commandes et pendant le passage en caisse.
feature: Checkout, Orders
role: Admin
exl-id: eae9a6ad-0999-4581-b3c0-7667ee7beb54
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-50345 : problèmes reCAPTCHA lors de l’extraction

Le correctif ACSD-50345 corrige le problème en raison duquel les validations reCAPTCHA v2 et v3 échouent lors du passage des commandes et lors du passage en caisse. Ce correctif est disponible lorsque la version 1.1.31 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50345. Veuillez noter que le problème a été partiellement résolu dans Adobe Commerce 2.4.6 et qu&#39;il est prévu de le résoudre entièrement dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

**Cas #1**

Google reCAPTCHA v2 ne se recharge pas après l&#39;envoi d&#39;un paiement en échec.

<u>Procédure à suivre</u>

1. Configurez **[!UICONTROL Google reCAPTCHA v2]** (*je ne suis pas un robot*).
1. Activez le **[!UICONTROL reCAPTCHA]** pour l’extraction.
1. Essayez de passer une commande sans cliquer sur **[!UICONTROL reCAPTCHA]**.
1. Une fois que l’utilisateur reçoit le message d’erreur pour le reCAPTCHA manquant (*échec de la validation de reCAPTCHA, veuillez réessayer*), cliquez sur le **[!UICONTROL reCAPTCHA]** et essayez de passer une commande.

<u>Résultats attendus</u>

La commande ne sera pas passée avec un reCAPTCHA incorrect.

<u>Résultats réels</u>

Une erreur est générée. *La validation reCAPTCHA a échoué, veuillez réessayer* et *Aucun panier de ce type avec l’ID = 4*

**Cas #2**

Google reCAPTCHA v3 Invisible ne fonctionne pas lors de l’extraction et la commande ne peut pas être passée. `PlaceOrder` événement n’est pas déclenché.

<u>Procédure à suivre</u>

1. Configurez le **[!UICONTROL reCAPTCHA v3 Invisible]** à partir du **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. Activez **[!UICONTROL reCAPTCHA v3 Invisible]** pour passer en caisse ou passer une commande sous l’onglet **[!UICONTROL Storefront]** .
1. Essayez de passer une commande avec le mode de paiement [!UICONTROL Check/Money order].

<u>Résultats attendus</u>

La commande doit être passée avec le **[!UICONTROL reCAPTCHA]** activé.

<u>Résultats réels</u>

Après avoir cliqué sur le bouton **[!UICONTROL Place Order]** , il est désactivé et rien ne se passe plus.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
