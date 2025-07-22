---
title: 'ACSD-65777 : champ « types » manquant pour les types d’images de produit dans la requête GraphQL « MediaGallery »'
description: Appliquez le correctif ACSD-65777 pour résoudre le problème Adobe Commerce en raison duquel le champ « types » était manquant pour les types d’images de produit dans la requête GraphQL « MediaGallery ».
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777 : champ de **[!UICONTROL types]** manquant pour les types d’images de produit dans la requête `MediaGallery` GraphQL

Le correctif ACSD-65777 corrige le problème en raison duquel le champ **[!UICONTROL types]** était manquant pour les types d’images de produit dans la requête `MediaGallery` GraphQL. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65777. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le champ **[!UICONTROL types]** est manquant pour les types d’images de produit lors de la récupération de données multimédia via la requête GraphQL `MediaGallery`.

<u>Procédure à suivre </u> :

1. Créez un produit.
1. Chargez une image sur le produit.
1. Récupérez les données multimédia à l’aide du GraphQL suivant.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>Résultats attendus</u> :

L’interface de GraphQL `media_gallery` doit inclure le champ **[!UICONTROL types]** .

<u>Résultats réels</u> :

Le `media_gallery` ne contient pas le champ de **[!UICONTROL types]** multimédia.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
