---
title: 'ACSD-53750 : erreur « Canal rompu ou connexion fermée » lors de la réindexation multi-thread catalog_product_price'
description: Appliquez le correctif ACSD-53750 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur de *canal rompu ou de connexion fermée* se produit lors de la réindexation multi-thread catalog_product_price.
feature: Products
role: Admin, Developer
exl-id: 6c2f092f-a98e-4990-839c-a7291635f8af
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-53750 : erreur *canal rompu ou connexion fermée* lors de la réindexation de `catalog_product_price` multithread

Le correctif ACSD-53750 corrige le problème où une erreur *Canal rompu ou connexion fermée* se produit lors de la réindexation de `catalog_product_price` multithread. Ce correctif est disponible lorsque la version 1.1.37 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53750. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*Canal rompu ou connexion fermée* l’erreur se produit lors de la réindexation de `catalog_product_price` multithread.

<u>Procédure à suivre </u> :

1. Configurez RabbitMq.
1. Générez des données d’exemple à l’aide du fichier `small.xml` joint.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** et définissez **[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**.
1. Définissez le mode Dimension pour les index qui prennent en charge ce mode. Par ex., `catalog_product_price_website_and_customer_group` ou `customer_group`.

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. Exécutez la réinitialisation des indexeurs pour `catalog_product_price`.

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. Exécutez l’indexeur pour le réinitialiser à l’aide de plusieurs threads.

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>Résultats attendus</u> :

Aucune erreur ne se produit.

<u>Résultats réels</u> :

L&#39;erreur suivante est due à une connexion AMQP : *tuyau rompu ou connexion fermée*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
