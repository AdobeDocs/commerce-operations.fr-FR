---
title: 'ACSD-47332 : échec de cron avec une erreur signalée uniquement entre 00:00 et 00:59 UTC'
description: Appliquez le correctif ACSD-47332 pour résoudre le problème d’Adobe Commerce en raison duquel cron échoue avec une erreur qui n’est signalée que lorsqu’elle est exécutée entre 00:00 et 00:59 UTC.
feature: Configuration
role: Admin
exl-id: ffe6c8f7-0e4c-4a22-853a-45d708bf8164
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-47332 : échec de cron avec une erreur signalée uniquement lors de l’exécution entre 00:00 et 00:59 UTC

Le correctif ACSD-47332 corrige le problème d’échec de cron avec une erreur qui n’est signalée que lorsqu’il est exécuté entre 00:00 et 00:59 UTC. Ce correctif est disponible lorsque la version 1.1.22 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47332. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La commande Cron échoue avec une erreur qui est signalée uniquement lors de l’exécution entre 00:00 et 00:59 UTC.

<u>Procédure à suivre </u> :

1. Exécutez le CRON `catalog_index_refresh_price` entre 00:00 et 00:59 UTC.

<u>Résultats attendus</u> :

Cron n’affiche aucune erreur.

<u>Résultats réels</u> :

La commande cron échoue avec l’erreur suivante.

```SQL
SQLSTATE[HY093]: Invalid parameter number: number of bound variables does not match number of tokens, query was: SELECT `cat`.`entity_id` FROM `c
  atalog_product_entity_datetime` AS `attr`
   LEFT JOIN `catalog_product_entity` AS `cat` ON cat.row_id= attr.row_id AND (cat.created_in <= 1 AND cat.updated_in > 1) WHERE (attr.attribute_id
   = '79') AND (attr.store_id = '0') AND (attr.value = DATE_FORMAT('2022-10-02', '%Y-%m-%d %H:%i:%s'))
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
