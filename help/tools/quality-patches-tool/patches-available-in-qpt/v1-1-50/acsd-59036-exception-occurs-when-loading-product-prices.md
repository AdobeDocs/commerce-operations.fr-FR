---
title: 'ACSD-59036 : une exception se produit lors du chargement des prix de produit avec des limites inférieure et supérieure définies sur 0 $'
description: Appliquez le correctif ACSD-59036 pour résoudre le problème d’Adobe Commerce où une exception se produit lors du chargement des prix des produits avec des limites inférieure et supérieure définies sur *$0*.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-59036 : une exception se produit lors du chargement des prix de produit avec des limites inférieure et supérieure définies sur *$0*

Le correctif ACSD-59036 corrige le problème où une exception se produit lors du chargement des prix de produits avec des limites inférieure et supérieure définies sur *$0*. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59036. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une exception se produit lors du chargement des prix de produit avec des limites inférieure et supérieure définies sur *$0*.

Le problème se produit car l’algorithme ne tient pas compte des valeurs NULL lors du chargement de la requête avec des plages de prix. Pour corriger ce problème, nous pouvons vérifier si les plages inférieure et supérieure sont NULL et, si elles le sont, attribuer une valeur de *0* pour les deux limites. Cela permet d’éviter la génération d’erreurs.

<u>Procédure à suivre </u> :

1. Créez des produits simples *13*.
1. Affectez tous les produits *13* à une catégorie.
1. Fixez le prix d&#39;un produit à 1322,94 $**.
1. Fixez le prix de tous les autres produits à *$0*.
1. Configurez [!DNL OpenSearch] comme moteur de recherche.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** et définissez le nombre de **[!UICONTROL PLP]** sur *16*.
1. Définissez **[!UICONTROL Price Navigation Step Calculation]** sur *Automatique (égalisation du nombre de produits)*.
1. Exécutez la réindexation complète.
1. Ouvrez la page *[!UICONTROL Category]*.

<u>Résultats attendus</u> :

La page *[!UICONTROL Category]* affiche tous les produits.

<u>Résultats réels</u> :

Une erreur se produit :

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
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
