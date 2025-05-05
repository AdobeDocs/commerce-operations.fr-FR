---
title: 'ACSD-61805 : corrige le problème de stock sur le storefront après la mise à jour du statut de la commande en souffrance via l’API REST'
description: Appliquez le correctif ACSD-61805 pour résoudre le problème Adobe Commerce où les produits restent en rupture de stock sur le storefront après la mise à jour du statut de la commande en attente via l’API REST
feature: REST, Catalog Management, Inventory
role: Admin, Developer
source-git-commit: abad1a2f2a1bdc2c1a4b6f821e6b02190a5ebe83
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-61805 : corrige le problème de stock sur le storefront après la mise à jour du statut de la commande en souffrance via l’API REST

Le correctif ACSD-61805 corrige le problème où les produits restent en rupture de stock sur le storefront après la mise à jour du statut de la commande en attente via l’API REST. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61805. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits restent en rupture de stock sur le storefront après la mise à jour du statut de la commande en souffrance via l’API REST.

<u>Procédure à suivre </u> :

1. Installez une instance propre avec des exemples de données.
1. Créez une nouvelle source de stock.
1. Créez un nouveau stock de stock et affectez-lui la nouvelle source.
1. Affectez la nouvelle source au produit 24-MB01.
1. Définissez **[!UICONTROL Source Item Status]** sur `In Stock` pour les deux sources de produits.
1. Définissez la quantité (**[!UICONTROL QTY]**) sur *0* pour les deux quantités de produit.
1. Enregistrez le produit.
1. Récupérez le jeton administrateur à partir de cette URL de point d’entrée : `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Mettez à jour le produit en utilisant le point d’entrée : `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Exécutez deux fois les tâches cron (une fois pour créer des planifications et une fois pour exécuter la planification) :

   ```bash
   bin/magento cron:run
   ```

1. Accédez au serveur frontal et vérifiez le produit.

<u>Résultats attendus</u> :

Le produit doit être *En stock*.

<u>Résultats réels</u> :

Le produit est *en rupture de stock*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
