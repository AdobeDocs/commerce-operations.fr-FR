---
title: 'ACSD-46770 : l’e-mail de confirmation de commande est envoyé même lorsque [!UICONTROL Email Order Confirmation] n’est pas coché'
description: Appliquez le correctif ACSD-46770 pour résoudre le problème d’Adobe Commerce où les e-mails de confirmation de commande sont envoyés même lorsque [!UICONTROL Email Order Confirmation] n’est pas sélectionné.
feature: Communications, Orders
role: Admin
exl-id: d25ca121-7551-417c-b598-d8ed3a3da969
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-46770 : l’e-mail de confirmation de commande est envoyé même lorsque **[!UICONTROL Email Order Confirmation]** n’est pas coché

Le correctif ACSD-46770 corrige le problème où les commandes peuvent être passées via l’API REST en tant qu’utilisateur invité, même lorsque **[!UICONTROL Email Order Confirmation]** n’est pas sélectionné. Ce correctif est disponible lorsque la version 1.1.24 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46770. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un e-mail de confirmation de commande est envoyé même lorsque **[!UICONTROL Email Order Confirmation]** n’est pas sélectionné.

<u>Procédure à suivre </u> :

1. Créez un compte client.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Order]** et cliquez sur **[!UICONTROL Create New Order]**.
1. Sélectionnez le client, ajoutez les produits à la commande, indiquez l’adresse, puis sélectionnez les Modes d’expédition et de paiement.
1. Avant d’envoyer la commande, désélectionnez la case **[!UICONTROL Email Order confirmation]**.
1. Cliquez sur **[!UICONTROL Submit Order]** pour créer la commande.

<u>Résultats attendus</u> :

Un e-mail de confirmation de commande ne doit pas être envoyé si le **[!UICONTROL Email Order Confirmation]** est désélectionné.

<u>Résultats réels</u> :

Un e-mail de confirmation de commande est envoyé, quelle que soit la case à cocher **[!UICONTROL Email Order Confirmation]** désélectionnée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
