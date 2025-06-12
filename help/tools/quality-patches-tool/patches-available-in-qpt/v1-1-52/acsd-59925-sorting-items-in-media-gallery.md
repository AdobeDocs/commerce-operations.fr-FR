---
title: 'ACSD-59925 : tri des éléments dans [!UICONTROL Media Gallery] par position dans GraphQL'
description: Appliquez le correctif ACSD-59925 pour résoudre le problème d’Adobe Commerce en raison duquel les éléments du [!UICONTROL Media Gallery] ne sont pas triés par position, ce qui entraîne un ordre d’affichage incorrect.
feature: Media, GraphQL
role: Admin, Developer
exl-id: a4dd840f-44d2-40dc-b0e1-13d55b688204
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59925 : tri des éléments du [!UICONTROL Media Gallery] par position dans GraphQL

Le correctif ACSD-59925 corrige le problème où les éléments du [!UICONTROL Media Gallery] ne sont pas triés par position, ce qui entraîne un ordre d’affichage incorrect. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-59925. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les éléments du [!UICONTROL Media Gallery] ne sont pas triés par position, ce qui entraîne un ordre d’affichage incorrect.

<u>Procédure à suivre </u> :

1. Créez/modifiez le produit.
1. Ajoutez au moins deux images et enregistrez-les.
1. Modifiez le même produit, mais cette fois, faites glisser la dernière image vers la première position.
1. Enregistrez le produit.
1. Réindexez.
1. Accédez au client GraphQL.
1. Exécutez la requête GraphQL :

   ```GraphQL
   {
     products(filter: { sku: { eq: "24-MB01" } }) {
        items {
          name
          sku
          url_key
          stock_status
          media_gallery {
             __typename
             ... on ProductVideo {
               video_content {
                 video_url
                 video_title
                 __typename
               }
               __typename
             }
             ... on ProductImage {
               url
               __typename
             }
               position
               disabled
            }
         }
         total_count
         page_info {
         page_size
        }
      }
    }
   ```

<u>Résultats attendus</u> :

Les éléments de la `media_gallery` sont triés par position.

<u>Résultats réels</u> :

Les éléments de la `media_gallery` ne sont pas triés par position.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
