---
title: 'ACSD-50234 : nom de client incorrect dans l’e-mail de confirmation pour les commandes passées à l’aide de  [!DNL PayPal]'
description: Appliquez le correctif ACSD-50234 pour résoudre le problème d’Adobe Commerce où le nom du client s’affiche incorrectement dans l’e-mail de confirmation pour les commandes passées à l’aide de  [!DNL PayPal].
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234 : nom de client incorrect dans l’e-mail de confirmation pour les commandes passées à l’aide de [!DNL PayPal]

Le correctif ACSD-50234 corrige le problème d’affichage incorrect du nom du client dans l’e-mail de confirmation pour les commandes passées à l’aide de [!DNL PayPal]. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-50234. Notez que le problème a été résolu dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’e-mail de confirmation pour les commandes passées à l’aide de [!DNL PayPal] indique un nom de client incorrect.

<u>Procédure à suivre</u>

1. Activez **[!UICONTROL PayPal Express Checkout]**.
1. Accédez au serveur frontal en tant qu’invité.
1. Ajoutez des produits au panier.
1. Effectuez le paiement en utilisant **[!UICONTROL PayPal Express Checkout]** comme mode de paiement.
1. Vérifiez l’e-mail de confirmation de commande.

<u>Résultats attendus</u>

L&#39;e-mail de confirmation de commande, l&#39;e-mail de facturation et tous les e-mails relatifs à l&#39;expédition sont adressés au nom du client.

<u>Résultats réels</u>

L’e-mail de confirmation de commande, l’e-mail de facture et tous les e-mails liés à l’expédition sont adressés à *Invité*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
