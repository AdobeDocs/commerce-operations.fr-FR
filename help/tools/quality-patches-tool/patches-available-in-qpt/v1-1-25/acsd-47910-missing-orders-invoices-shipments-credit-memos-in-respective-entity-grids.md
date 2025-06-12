---
title: 'ACSD-47910 : commandes, factures, expéditions et avoirs manquants dans les grilles d''entités respectives'
description: Appliquez le correctif ACSD-47910 pour résoudre le problème Adobe Commerce en raison duquel il manque des commandes, des factures, des expéditions et des avoirs dans les grilles d'entité respectives.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910 : commandes, factures, expéditions et avoirs manquants dans les grilles d&#39;entité respectives

Le correctif ACSD-47910 corrige le problème en raison duquel il manque des commandes, des factures, des expéditions et des avoirs dans les grilles d&#39;entités respectives. Ce correctif est disponible lorsque la version 1.1.25 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47910. La version dans laquelle ce problème sera résolu n’est pas encore disponible.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Commandes, factures, expéditions et avoirs manquants dans les grilles d&#39;entité respectives.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL Asynchronous indexing]** sous **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Passez deux commandes.
1. Exécutez la commande cron pour synchroniser ces commandes avec la grille.
1. Ouvrez l&#39;une des commandes et préparez-la à être facturée. NE PAS SOUMETTRE LA FACTURE POUR LE MOMENT.
1. Effectuez une nouvelle commande prête à être placée sur le serveur frontal. NE CLIQUEZ PAS ENCORE SUR LE BOUTON PASSER UNE COMMANDE.
1. Ajoutez un `sleep(30)` dans le `foreach` à `NotSyncedDataProvider::L43`.
1. Exécutez `bin/magento cron:run`.
1. Passez maintenant la nouvelle commande.
1. Facture la commande précédente.
1. Exécutez à nouveau le cron en attendant que la nouvelle commande soit synchronisée.
1. Accédez à la grille de commande dans l’Admin.

<u>Résultats attendus</u> :

La nouvelle commande doit apparaître dans la grille de commande.

<u>Résultats réels</u> :

La mise à jour de commande précédente a été synchronisée dans la grille (**[!UICONTROL status: Processing]**). La nouvelle commande n’apparaît jamais sur la grille.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
