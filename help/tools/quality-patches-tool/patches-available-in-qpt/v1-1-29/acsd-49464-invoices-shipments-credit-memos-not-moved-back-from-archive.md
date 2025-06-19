---
title: 'ACSD-49464 : factures, expéditions et avoirs non retirés de l''archive'
description: Appliquez le correctif ACSD-49464 pour résoudre le problème d’Adobe Commerce en raison duquel les factures, les expéditions et les avoirs ne sont pas retirés de l’archive lorsque l’orderId est différent.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464 : factures, expéditions et avoirs non retirés de l&#39;archive

Le correctif ACSD-49464 corrige le problème en raison duquel les factures, les expéditions et les avoirs ne sont pas retirés de l’archive lorsque l’ID de commande est différent. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49464. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les factures, les livraisons et les avoirs ne sont pas retirés de l&#39;archive lorsque l&#39;ID de commande est différent.

<u>Procédure à suivre </u> :

1. Activez l&#39;archivage des commandes, des factures, des expéditions et des avoirs.
1. Créez et exécutez une commande, y compris l&#39;expédition, la facture et l&#39;avoir.
1. Assurez-vous que les identifiants d&#39;expédition, de facture et d&#39;avoir ne sont pas identiques au numéro de commande.
1. Déplacez l’ordre vers l’archive.
1. Restaurez la commande archivée pour la gestion des commandes.
1. Vérifiez les détails de la facture, de l’expédition et de l’avoir dans les pages respectives [!UICONTROL Invoice], [!UICONTROL Shipping] et grille de [!UICONTROL Credit Memo].

<u>Résultats attendus</u> :

Les enregistrements associés d&#39;origine sont restaurés lorsque la commande est déplacée de la liste d&#39;archives vers la gestion des commandes.

<u>Résultats réels</u> :

* Aucun enregistrement pour l&#39;expédition, la facture et les avoirs si tous les ID sont différents.
* Si la commande et les enregistrements associés ont le même ID, les enregistrements sont renvoyés.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
