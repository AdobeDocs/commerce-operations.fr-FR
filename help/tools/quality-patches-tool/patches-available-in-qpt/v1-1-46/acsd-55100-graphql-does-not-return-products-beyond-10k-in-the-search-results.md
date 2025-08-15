---
title: 'ACSD-55100: [!DNL GraphQL] ne renvoie pas de produits au-delà de 10k dans les résultats de recherche'
description: Appliquez le correctif ACSD-55100 pour résoudre le problème d’Adobe Commerce en raison duquel le GraphQL ne renvoie pas de produits au-delà de *10 000* dans les résultats de la recherche.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# ACSD-55100 : [!DNL GraphQL] ne renvoie pas de produits au-delà de 10k dans les résultats de recherche

>[!NOTE]
>
>Un correctif mis à jour ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) a été publié pour résoudre le même problème pour les versions 2.4.6 à 2.4.6-p8. Pour plus d’informations, voir [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

Le correctif ACSD-55100 corrige le problème où [!DNL GraphQL] ne renvoie pas de produits au-delà de *10k* dans les résultats de recherche. Ce correctif est disponible lorsque la version 1.1.46 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-55100. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL GraphQL] ne renvoie pas de produits au-delà de *10k* dans les résultats de recherche.

<u>Conditions préalables</u> :

En cas de **[!DNL OpenSearch]**, assurez-vous d’utiliser la dernière version disponible.

Pour résoudre le problème signalé, la fonctionnalité Point dans le temps est introduite, qui est disponible après **[!DNL OpenSearch]** 2.5.0 et nécessite la version 2.2 du package `opensearch-project/opensearch-php`.

Cependant, il existe un conflit avec la `magento/magento-cloud-metapackage` , qui spécifie une dépendance sur le package `opensearch-project/opensearch-php` qui doit être inférieure à la version 2.0.1.


Cette dépendance empêche la mise à jour du package [opensearch-project/opensearch-php] vers la dernière version 2.2.

Par conséquent, le système rencontre l’erreur suivante et renvoie des résultats nuls pour les produits supérieurs à 10 000 **.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dépendance existante rend difficile l’ajout direct d’une version au fichier `composer.json` et la mise à jour du package `opensearch-project/opensearch-php` vers la version 2.2.

Pour résoudre le problème, incluez la ligne suivante dans votre fichier `composer.json` principal sous le bloc exiger . Ensuite, redéployez pour mettre à jour le package problématique vers la dernière version.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Procédure à suivre </u> :

1. Générez le catalogue avec des produits *15k*.
1. Envoyez le [!DNL GraphQL] :

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Résultats attendus</u> :

Total_count = *15k*
Vous devriez être en mesure de montrer tous les produits.

<u>Résultats réels</u> :

Total_count = *10k*
Vous ne pouvez plus afficher d&#39;autres produits après le lot *10k*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
