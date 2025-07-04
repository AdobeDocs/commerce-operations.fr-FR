---
title: 'ACP2E-3789 : fichiers multimédias dupliqués lors de la mise à jour du produit via WebAPI'
description: Appliquez le correctif ACP2E-3789 pour résoudre le problème d’Adobe Commerce où les mises à jour de produit via des fichiers multimédias en double WebAPI sont fournies lorsqu’un ID de média est fourni.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789 : fichiers multimédias dupliqués lors de la mise à jour du produit via WebAPI

Le correctif ACP2E-3789 corrige le problème de mise à jour du produit par le biais de fichiers multimédias en double WebAPI lorsqu’un ID de média est fourni. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3789. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour d’un produit via WebAPI avec un ID de média entraîne la duplication des fichiers médias par le système au lieu de les remplacer, la création de nouveaux fichiers avec chaque appel API et une accumulation d’images qui surcharge le répertoire `/pub/media/catalog/products/cache/`.

<u>Procédure à suivre </u> :

1. Créez un produit et ajoutez une image.
1. Obtenez des informations détaillées sur les produits en utilisant l’API REST à l’adresse `base_url/rest/V1/products/<sku>`.
1. Effectuez une requête PUT pour mettre à jour le produit en conservant les `media_gallery_entrie` inchangées (même nom et même fichier d’image).
1. Vérifiez le répertoire `pub/media/catalog/product/xx/yy` avant et après la mise à jour.

<u>Résultats attendus</u> :

Le fichier image est remplacé lorsque l’ID de média est inclus dans la requête.

<u>Résultats réels</u> :

L’image est dupliquée avec un nouveau nom (par exemple, wb04-blue-1.jpg), ce qui entraîne une accumulation de fichier inutile.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
