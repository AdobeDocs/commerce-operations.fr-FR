---
title: 'ACSD-51857 : La tâche cron lente de &grave;aggregate_sales_report_bestsellers_data&grave; affecte les performances'
description: Appliquez le correctif ACSD-51857 pour résoudre le problème Adobe Commerce en raison duquel la tâche cron lente "aggregate_sales_report_bestsellers_data" affecte les grandes tables de base de données "sales_order" et "sales_order_item".
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857 : la tâche cron lente de `aggregate_sales_report_bestsellers_data` affecte les performances

Le correctif ACSD-51857 corrige le problème en raison duquel la tâche cron lente `aggregate_sales_report_bestsellers_data` affecte les tables de base de données `sales_order` et `sales_order_item` volumineuses. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 est installé. L’ID de correctif est ACSD-51857. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances des tâches Cron de `aggregate_sales_report_bestsellers_data` sont lentes sur les tables de base de données `sales_order` et `sales_order_item`.

Pour résoudre ce problème, la requête de données principale qui récupère les données du rapport a été réécrite dans un formulaire plus efficace. Elle utilise désormais une sous-requête pour déterminer le sous-ensemble de données.

Pour que la sous-requête fonctionne aussi vite que possible, un nouvel index a été ajouté pour la table de base de données `sales_order` : `SALES_ORDER_STORE_STATE_CREATED` basé sur les colonnes `store_id`, `state` et `created_at`.

<u>Conditions préalables</u>

Assurez-vous qu’un grand nombre de commandes sont commandées quotidiennement.

<u>Étapes à reproduire</u>

1. Exécutez la tâche cron `aggregate_sales_report_bestsellers_data`.
1. Vérifiez les données à afficher dans le tableau de bord Admin, sous l’onglet **[!UICONTROL Bestsellers]**.

<u>Résultats attendus</u> :

*[!UICONTROL Quantity per source]* sous l’onglet **[!UICONTROL Configuration]** ne doit pas être vide.

<u>Résultats réels</u> :

*[!UICONTROL Quantity per source]* sous l’onglet **[!UICONTROL Configuration]** est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
