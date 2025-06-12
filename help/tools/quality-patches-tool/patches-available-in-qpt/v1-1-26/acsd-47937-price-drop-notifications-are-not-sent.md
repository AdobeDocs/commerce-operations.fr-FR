---
title: 'ACSD-47937 : notifications de baisse de prix non envoyées en raison de la mise en cache au niveau de l’application'
description: Appliquez le correctif ACSD-47937 pour résoudre le problème d’Adobe Commerce où les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937 : notifications de baisse de prix non envoyées en raison de la mise en cache au niveau de l’application

Le correctif ACSD-47937 corrige le problème où les notifications de baisse de prix ne sont pas toujours envoyées en raison de la mise en cache au niveau de l’application. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47937. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 et 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.5 et 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients ne reçoivent pas d’e-mail de baisse du prix du produit pour les modifications ultérieures du prix du produit.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL Product Alert]** pour les *[!UICONTROL Price Changes]* et les *[!UICONTROL Back in Stock]* dans **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Activez **[!UICONTROL Display Out of Stock Products]**.
1. Créez un produit simple (ABC) avec qté = 0.
1. Créez un client à partir du storefront et abonnez-vous au produit ci-dessus pour obtenir des alertes sur les produits en cas de chute des prix.
1. Démarrer l’alerte produit pour les clients.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Baissez le prix du produit ABC.
1. Déclenchez l’icône d’alerte du produit .

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Baissez à nouveau le prix du produit ABC.
1. Déclenchez l’icône d’alerte du produit .

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Si vous ne connaissez pas [!DNL n98] outil, vous pouvez l’exécuter `bin/magento cron:run command` que d’habitude et surveiller `cron_schedule` tableau pour vous assurer que `catalog_product_alert` tâche obtient le statut Succès .

<u>Résultats attendus</u> :

Le deuxième e-mail de baisse de prix est envoyé.

<u>Résultats réels</u> :

Le deuxième e-mail de baisse de prix n’est pas envoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
