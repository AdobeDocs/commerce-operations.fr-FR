---
title: 'ACSD-63574 : l’ajout d’[!UICONTROL Bundle Product] liste à bloquer via [!DNL Page Builder] entraîne une erreur'
description: Appliquez le correctif ACSD-63574 pour résoudre le problème d’Adobe Commerce où l’ajout de **[!UICONTROL Bundle Product]** avec les options « Case à cocher » ou « Sélection multiple » à un bloc via [!DNL Page Builder] entraîne une erreur.
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: b2e6a3a61dbd3cd3b76e968ff8cdad664663fc4b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574 : l’ajout d’[!UICONTROL Bundle Product] liste à bloquer via [!DNL Page Builder] génère une erreur

Le correctif ACSD-63574 corrige le problème où l’ajout de **[!UICONTROL Bundle Product]** avec des options `Checkbox` ou `Multi Select` à un bloc via [!DNL Page Builder] génère une erreur. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63574. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p10

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’ajout de **[!UICONTROL Bundle Product]** à un bloc à l’aide de [!DNL Page Builder], l’aperçu du widget de produit se rompt et affiche le message d’erreur *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*. Ce problème se produit spécifiquement lorsque le produit groupé comprend des types d’options `Checkbox` ou `Multi Select` et que `indexer dimension mode` est défini sur `website_and_customer_group`. Le journal des exceptions affiche l’erreur suivante :

     »
    report.CRITICAL: PDOException: SQLSTATE[42S02]: table ou vue de base introuvable : 1146 La table &#39;db_name.catalog_product_index_price_cg0_ws0&#39; n&#39;existe pas dans /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
     »

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Dans le panneau de gauche, développez **[!UICONTROL Catalog]** et sélectionnez **[!UICONTROL Catalog]** dans les options ci-dessous.
1. Faites défiler jusqu’à la section **[!UICONTROL Price]** et définissez **[!UICONTROL Catalog Price Scope]** sur **[!UICONTROL Global]**.
1. Définissez `Indexer dimension mode` sur `website_and_customer_group` à l’aide de la commande ci-dessous :

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Créez un **[!UICONTROL Bundle Product]** avec un type d’option de lot `Checkbox` ou `Multi Select`, puis affectez le produit à une catégorie.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**.
1. Sélectionnez la catégorie à laquelle le produit créé est affecté et essayez de **[!UICONTROL Save]**.

<u>Résultats attendus</u> :

Produit ajouté sans erreur.

<u>Résultats réels</u> :

Impossible d’ajouter un produit via [!DNL Page Builder] lorsque le type d’option **[!UICONTROL Bundle Product]** est `Checkbox` ou `Multi Select` et que `indexer dimension mode` est défini sur `website_and_customer_group`. Il renvoie l’erreur suivante : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*.


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
