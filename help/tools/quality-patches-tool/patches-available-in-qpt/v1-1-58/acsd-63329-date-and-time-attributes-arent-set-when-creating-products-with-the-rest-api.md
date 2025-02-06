---
title: 'ACSD-63329 : les attributs Date et Heure ne sont pas définis lors de la création de produits avec l’API REST'
description: Appliquez le correctif ACSD-63329 pour résoudre le problème Adobe Commerce où les valeurs par défaut ne sont pas définies pour les champs de date et d’heure lors de la création de produits avec l’API REST.
feature: REST
Role: Admin, Developers
source-git-commit: a7d719399425016da26c1065725a377bb82795f4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# ACSD-63329 : les valeurs par défaut des champs date et heure ne sont pas définies lors de la création de produits avec l’API REST

Le correctif ACSD-63329 corrige le problème où les valeurs par défaut n’étaient pas définies pour les champs de date et d’heure lors de la création d’un nouveau produit à l’aide de l’API REST : `/rest/default/V1/products`. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63329. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les valeurs par défaut ne sont pas définies pour les champs date et heure lors de la création de produits avec l’API REST : `/rest/default/V1/products`

<u>Procédure à suivre </u> :

1. Créez un attribut **[!UICONTROL Product]**, définissez sa valeur par défaut sur `12/31/2020` et définissez la **[!UICONTROL Catalog Input Type for Store Owner]** sur ***[!UICONTROL Date]*** ou ***[!UICONTROL Date and Time]***.
1. Créez un autre attribut de type texte et définissez la valeur par défaut sur ***valeur de test***.
1. Créez un produit à l’aide d’une requête de POST API REST à `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Vérifiez les valeurs enregistrées pour les attributs mentionnés ci-dessus.

<u>Résultats attendus</u> :

La valeur par défaut doit être enregistrée dans les attributs de type **[!UICONTROL Date/Datetime]** lors de la création d’un produit à l’aide de l’API .

<u>Résultats réels</u> :

La valeur par défaut est enregistrée pour l’attribut **[!UICONTROL Text]**, mais pas pour l’attribut **[!UICONTROL Date type]**. La valeur de l’attribut **[!UICONTROL Date]** est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
