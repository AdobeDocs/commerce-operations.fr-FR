---
title: 'ACSD-56415 : ralentissement des performances des [!UICONTROL Partial Price Indexing] en raison de la requête « DELETE »'
description: Appliquez le correctif ACSD-56415 pour résoudre le problème d’Adobe Commerce où les performances du [!UICONTROL Partial Price Indexing] sont ralenties en raison d’une requête « DELETE » lorsque la base de données contient de nombreuses données de prix partielles à indexer.
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-56415 : les performances de [!UICONTROL Partial Price Indexing] sont ralenties en raison d’une requête `DELETE`

Le correctif ACSD-56415 corrige le problème où les performances de la [!UICONTROL Partial Price Indexing] sont ralenties en raison d&#39;une requête `DELETE` lorsque la base de données a beaucoup d&#39;index de données de prix partiels. Ce correctif est disponible lorsque la version 1.1.45 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56023. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances de [!UICONTROL Partial Price Indexing] sont ralenties en raison d’une requête `DELETE` lorsque la base de données contient un grand nombre d’index de données de prix partiels.

<u>Procédure à suivre </u> :

1. Créez *300000 sites web de produits* et *10* à l’aide du profil de performances étendu.
1. Connectez-vous au Panneau d’administration.
1. Créez *10 groupes de clients*.
1. Exécutez la requête ci-dessous pour ajouter des produits à la table `_cl` :

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. Exécutez la commande ci-dessous pour déclencher le processus d’indexation partielle des prix :

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>Résultats attendus</u> :

La requête SQL DELETE `main_table` FROM `catalog_product_index_price` est exécutée rapidement.

<u>Résultats réels</u> :

La requête SQL DELETE `main_table` FROM `catalog_product_index_price` est exécutée très lentement.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [ Mises à niveau et correctifs > Appliquer des correctifs ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
