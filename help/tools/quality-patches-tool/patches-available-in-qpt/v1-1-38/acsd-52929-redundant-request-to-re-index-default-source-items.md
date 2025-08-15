---
title: 'ACSD-52929 : requête redondante pour réindexer les éléments sources par défaut'
description: Appliquez le correctif ACSD-52929 pour résoudre le problème d’Adobe Commerce en cas de demande redondante de réindexation des éléments sources par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929 : requête redondante pour réindexer les éléments sources par défaut

Le correctif ACSD-52929 corrige le problème de redondance des demandes de réindexation des éléments sources par défaut lorsque l’indexeur d’inventaire est configuré en mode asynchrone. Ce correctif est disponible lorsque la version 1.1.38 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52929. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les demandes de réindexation des éléments sources par défaut sont redondantes lorsque l’indexeur d’inventaire est configuré en mode asynchrone.

<u>Procédure à suivre </u> :

1. Configurez [!DNL RabbitMQ].
1. Activez la stratégie de réindexation asynchrone en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** et définissez **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Créez une source d’inventaire personnalisée.
1. Connectez-vous au tableau de bord [!DNL RabbitMQ] et accédez à l’onglet files d’attente .
1. Vérifiez `inventory.indexer.sourceItem` file d’attente et qu’elle ne comporte aucun message.
1. Ouvrez un produit simple à partir du serveur principal, ajoutez des *[!UICONTROL stock only]* à la source personnalisée et enregistrez le produit.
1. Chargez la file d’attente `inventory.indexer.sourceItem` dans le tableau de bord [!DNL RabbitMQ], puis vérifiez les messages.

<u>Résultats attendus</u> :

Il n’y a qu’un seul message dans la file d’attente pour la source personnalisée.

<u>Résultats réels</u> :

Deux messages s’affichent dans la file d’attente : l’un pour la source par défaut et l’autre pour la source personnalisée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
