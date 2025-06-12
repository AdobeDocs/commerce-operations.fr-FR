---
title: 'ACSD-51431 : le statut de l''indexeur est *[!UICONTROL Working]* même s''il n''y a aucune entrée dans le journal des modifications'
description: Appliquez le correctif ACSD-51431 pour résoudre le problème d’Adobe Commerce où le statut de l’indexeur est *[!UICONTROL Working]* même s’il n’y a aucune entrée dans le journal des modifications.
feature: Logs, Price Indexer
role: Admin
exl-id: c87c059b-f435-468d-a7fe-e6786fdba1f8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431 : le statut de l&#39;indexeur est *[!UICONTROL Working]* même s&#39;il n&#39;y a aucune entrée dans le journal des modifications

Le correctif ACSD-51431 corrige le problème de performances en raison duquel le statut de l’indexeur est *[!UICONTROL Working]* même s’il n’existe aucune entrée dans le journal des modifications. Ce correctif est disponible lorsque la version 1.1.33 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51431. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut de l&#39;indexeur est *[!UICONTROL Working]* même s&#39;il n&#39;existe aucune entrée dans le journal des modifications.

<u>Procédure à suivre </u> :

1. Définissez **[!UICONTROL indexers]** sur [!UICONTROL Update on Schedule].
1. Configurez la tâche cron pour qu’elle s’exécute toutes les minutes.
1. Enregistrez les modifications apportées à différents produits simultanément.
1. `bin/magento indexer:status` dans quelques minutes.

<u>Résultats attendus</u> :

Les modifications sont traitées et les indexeurs ont le statut *[!UICONTROL Ready]*. Le statut du *[!UICONTROL Schedule]* est *[!UICONTROL idle (0 in the backlog)]*.

<u>Résultats réels</u> :

Les modifications sont traitées et les indexeurs ont le statut *[!UICONTROL Ready]*. Cependant, le statut de *[!UICONTROL Schedule]* s’affiche *[!UICONTROL working (0 in the backlog)]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
