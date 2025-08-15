---
title: 'ACSD-51857 : la tâche cron lente de « aggregate_sales_report_bestsellers_data » affecte les performances'
description: Appliquez le correctif ACSD-51857 pour résoudre le problème d’Adobe Commerce en raison duquel la tâche cron lente « aggregate_sales_report_bestsellers_data » affecte les tables de base de données « sales_order » et « sales_order_item » volumineuses.
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857 : la lenteur de la tâche cron d’`aggregate_sales_report_bestsellers_data` affecte les performances

Le correctif ACSD-51857 corrige le problème où les tâches cron lentes `aggregate_sales_report_bestsellers_data` affectent les tables de base de données `sales_order` et `sales_order_item` volumineuses. Ce correctif est disponible lorsque la version 1.1.34 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51857. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances de la tâche cron de `aggregate_sales_report_bestsellers_data` sont lentes sur les tables de base de données `sales_order` et `sales_order_item`.

Pour résoudre ce problème, la requête de données principale qui récupère les données du rapport a été réécrite dans un formulaire plus efficace. Elle utilise désormais une sous-requête pour déterminer le sous-ensemble de données.

Afin que la sous-requête fonctionne aussi rapidement que possible, un nouvel index a été ajouté pour la table de base de données `sales_order` : `SALES_ORDER_STORE_STATE_CREATED` basé sur les colonnes `store_id`, `state` et `created_at`.

<u>Conditions préalables</u>

Assurer un grand nombre de commandes par jour.

<u>Procédure à suivre</u>

1. Exécutez la tâche cron `aggregate_sales_report_bestsellers_data`.
1. Vérifiez les données à afficher dans le tableau de bord de l’administrateur, sous l’onglet **[!UICONTROL Bestsellers]** .

<u>Résultats attendus</u> :

*[!UICONTROL Quantity per source]* sous l’onglet **[!UICONTROL Configuration]** ne doit pas être vide.

<u>Résultats réels</u> :

*[!UICONTROL Quantity per source]* sous l’onglet **[!UICONTROL Configuration]** est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
