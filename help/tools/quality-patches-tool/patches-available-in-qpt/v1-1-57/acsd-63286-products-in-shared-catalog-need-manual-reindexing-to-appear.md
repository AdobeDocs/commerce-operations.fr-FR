---
title: 'ACSD-63286 : les produits affectés au catalogue partagé nécessitent une réindexation manuelle pour apparaître'
description: Appliquez le correctif ACSD-63286 pour résoudre le problème d’Adobe Commerce où les produits affectés à un catalogue partagé via l’API n’apparaissent pas sur le storefront tant qu’une réindexation manuelle n’a pas été exécutée.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286 : les produits affectés au catalogue partagé nécessitent une réindexation manuelle pour apparaître

Le correctif ACSD-63286 corrige le problème où les produits affectés à un catalogue partagé via l’API n’apparaissent pas sur le storefront tant qu’une réindexation manuelle n’est pas exécutée. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63286. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque les produits sont affectés à un catalogue partagé via l’API, ils n’apparaissent pas sur le serveur frontal après l’exécution des tâches cron d’indexation partielle et de consommateur. Cependant, elles apparaissent après une réindexation complète manuelle.

<u>Procédure à suivre </u> :

1. Configurez [!DNL RabbitMQ] comme service de file d’attente.
1. Créez un catalogue partagé et affectez-le à une entreprise.
1. Créez un produit simple et affectez-le à une catégorie.
1. Exécutez la réindexation partielle.

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Utilisez la requête d’API suivante pour affecter le produit créé au `pub/rest/all/V1/sharedCatalog/<id>/assignProducts` de catalogue partagé :

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Exécutez la commande cron suivante pour effacer les files d’attente et exécuter la réindexation partielle.

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Connectez-vous au serveur frontal en tant qu’utilisateur d’entreprise.
1. Vérifiez la page de catégorie front-end. Les nouveaux produits affectés ne sont pas visibles.
1. Exécutez une réindexation manuelle :

   ```
   bin/magento index:reindex
   ```

<u>Résultats attendus</u> :

Le produit s’affiche sur le serveur frontal sans réindexation manuelle.

<u>Résultats réels</u> :

Le produit s’affiche sur le serveur frontal uniquement après une réindexation manuelle.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
