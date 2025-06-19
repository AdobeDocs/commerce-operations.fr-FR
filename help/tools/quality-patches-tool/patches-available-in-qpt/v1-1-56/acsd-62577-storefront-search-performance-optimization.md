---
title: 'ACSD-62577 : optimisation des performances de recherche Storefront'
description: Appliquez le correctif ACSD-62577 pour résoudre le problème d’Adobe Commerce où les performances de recherche de storefront sont dégradées en raison de la lenteur de l’exécution des requêtes due à une table « search_query » volumineuse.
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577 : optimisation des performances de recherche Storefront

Le correctif ACSD-62577 corrige le problème en ralentissant les performances des requêtes de recherche storefront en optimisant les index de requête et de table. Ce correctif est disponible avec la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). L’ID du correctif est ACSD-62577. Notez que le problème devait être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6, 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les tables `search_query` volumineuses ralentissent considérablement les recherches de storefront, augmentant les temps de réponse front-end en raison de requêtes inefficaces et du manque d’index de table optimisés.

<u>Procédure à suivre </u> :

1. Configurez Adobe Commerce Developer à l’aide de l’`small.xml` Performance Toolkit.
1. Accédez à la ligne de commande SQL et supprimez la table `search_query` à l&#39;aide des commandes suivantes :

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Renseignez la table `search_query` avec un grand nombre d’enregistrements, par exemple : 4 millions d’enregistrements.
1. Déclenchez la réindexation et videz les caches.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Activez les journaux de débogage de la base de données :

   ```
   bin/magento dev:query-log:enable  
   ```

1. Rechercher un terme dans la barre de recherche de storefront, par exemple,
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Vérifiez la `db.log` du temps d&#39;exécution de la requête pour le SQL suivant :

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>Résultats attendus</u> :

Le temps d’exécution de la requête est optimisé, ce qui entraîne une augmentation moins significative du temps de réponse lors du traitement de tables de `search_query` volumineuses.

<u>Résultats réels</u> :

Le temps d’exécution de la requête augmente considérablement en raison d’une gestion inefficace de la grande table `search_query` :

```
TIME: 10.8520 seconds  
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
