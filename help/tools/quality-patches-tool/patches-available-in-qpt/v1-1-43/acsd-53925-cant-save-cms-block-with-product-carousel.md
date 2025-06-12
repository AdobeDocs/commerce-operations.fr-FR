---
title: 'ACSD-53925 : impossible d’enregistrer le bloc CMS avec [!UICONTROL Product Carousel]'
description: Appliquez le correctif ACSD-53925 pour résoudre le problème d’Adobe Commerce en raison duquel l’administrateur ne peut pas enregistrer un bloc CMS avec le carrousel de produit lorsque le mode de dimensions pour « catalog_product_price » est défini sur site web.
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-53925 : impossible d’enregistrer le bloc CMS avec *[!UICONTROL Product Carousel]*

Le correctif ACSD-53925 corrige le problème en raison duquel l’administrateur ne peut pas enregistrer un bloc CMS avec *[!UICONTROL Product Carousel]* lorsque le mode de dimensions pour `catalog_product_price` est défini sur Site web. Ce correctif est disponible lorsque la version 1.1.43 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53925. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’administrateur ne peut pas enregistrer un bloc CMS avec *[!UICONTROL Product Carousel]* lorsque le mode dimensions pour `catalog_product_price` est défini sur Site web.

<u>Procédure à suivre </u> :

1. Créez deux produits simples :
   * simple1 - 10 $
   * simple2 - 20 $
1. Créez une offre groupée « *bundle1-dyn* » avec deux options basées sur des SKU de produit simples.
1. Définissez le mode Dimensions pour l’indexeur de prix de produit :

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Blocks]**, puis créez un bloc CMS.
1. Modifiez le contenu à l’aide de [!DNL Page Builder] :
   * Ajouter un élément *[!UICONTROL Row]*
   * Ajouter un élément *[!UICONTROL Products]*
   * Sélectionner un *[!UICONTROL Product Carousel]*
   * Saisir le SKU du produit - *bundle1-dyn*
1. Enregistrez le bloc CMS.

<u>Résultats attendus</u> :

L’utilisateur peut ajouter un carrousel de produit sans erreur.

<u>Résultats réels</u> :

* Un message s’affiche dans l’interface utilisateur : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*
* `var/log/exception.log` contient l&#39;erreur suivante :

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
