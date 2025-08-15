---
title: 'ACSD-64118 : les demandes d’enregistrement de produit simultanées pour un même produit entraînent une incohérence des données et des entrées en double'
description: Appliquez le correctif ACSD-64118 pour résoudre le problème d’Adobe Commerce où des requêtes simultanées d’enregistrement et de mise à jour du même produit entraînent une incohérence des données ou des produits dupliqués.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: e014645e-72b2-4b3d-8b44-3daca502c950
source-git-commit: 5c84dc5c27f6e57b4116bc1a3d4fb001b55b63f1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-64118 : les demandes d’enregistrement de produit simultanées pour un même produit entraînent une incohérence des données et des entrées en double

Le correctif ACSD-64118 corrige le problème lorsque des requêtes simultanées d’enregistrement et de mise à jour d’un même produit entraînent une incohérence des données ou des produits dupliqués. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64118. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les requêtes simultanées d’enregistrement et de mise à jour d’un même produit entraînent une incohérence des données ou la duplication de produits.

<u>Procédure à suivre </u> :

1. Configurez le multiprocessus pour les consommateurs dans `env.php` :

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Ajoutez une boutique supplémentaire et une nouvelle boutique sur le site web principal.
1. Envoyez une requête d’API en bloc au point d’entrée storeview par défaut `/rest/default/async/bulk/V1/products` avec la payload suivante pour créer un produit :

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Utilisez la même payload pour envoyer une requête d’API en bloc au nouveau point d’entrée Storereview `/rest/store/async/bulk/V1/products` de mettre à jour le produit.
1. Videz le cache.
1. Exécutez les traitements cron.
1. Consultez le tableau `catalog_product_entity` pour connaître les entrées du produit des étapes précédentes.

<u>Résultats attendus</u> :

* Une seule entrée pour le SKU du produit doit être présente dans le tableau `catalog_product_entity`.
* La première requête d’API REST doit créer une entrée de base de données et toutes les requêtes suivantes doivent mettre à jour cette entrée de base de données.

<u>Résultats réels</u> :

Plusieurs entrées pour le même SKU sont présentes dans le tableau `catalog_product_entity`.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
