---
title: 'MDVA-42790 : les attributs de prix de produit ne peuvent pas être mis à jour pour un site web spécifique via l’API REST'
description: Le correctif MDVA-42790 corrige le problème en raison duquel les utilisateurs ne sont pas en mesure de mettre à jour les attributs de prix de produit pour des sites web spécifiques via l’API REST. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-42790. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: REST, Attributes, Orders, Products
role: Admin
exl-id: bb8dc764-d2d5-4e00-884a-2b4c1a567f58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42790 : les attributs de prix de produit ne peuvent pas être mis à jour pour un site web spécifique via l’API REST

Le correctif MDVA-42790 corrige le problème en raison duquel les utilisateurs ne sont pas en mesure de mettre à jour les attributs de prix de produit pour des sites web spécifiques via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-42790. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas mettre à jour les attributs de prix de produit pour des sites web spécifiques via l’API REST.

<u>Procédure à suivre </u> :

1. Dans l’administration, accédez à **Magasins** > **Configuration** > **Catalogue** > **Prix** > et définissez **Périmètre du prix du catalogue** sur Site web.
1. Mettre à jour le prix spécial d’un produit groupé en utilisant l’API REST, `POST rest/V1/products/`.

   ```JSON
   {
     "product": {
       "id": 46,
       "sku": "24-WG080",
       "name": "Sprite Yoga Companion Kit",
       "attribute_set_id": 4,
       "price": 10,
       "status": 1,
       "visibility": 1,
       "type_id": "bundle",
       "weight": 0,
       "custom_attributes": [
         {
           "attribute_code": "special_price",
           "value": "2"
         }
       ]
     }
   }
   ```

<u>Résultats attendus</u> :

Le prix spécial est mis à jour pour le produit groupé lorsque la variable **Périmètre du prix du catalogue** est définie sur Site Web.

<u>Résultats réels</u> :

Le prix spécial n’est pas mis à jour pour le produit groupé lorsque la **Périmètre du prix du catalogue** est définie sur Site Web.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
