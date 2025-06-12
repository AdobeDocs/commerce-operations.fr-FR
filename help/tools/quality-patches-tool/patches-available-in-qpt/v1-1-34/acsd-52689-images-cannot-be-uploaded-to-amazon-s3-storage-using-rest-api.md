---
title: 'ACSD-52689 : les images ne peuvent pas être chargées vers le stockage Amazon S3 via l’API REST'
description: Appliquez le correctif ACSD-52689 pour résoudre le problème d’Adobe Commerce en raison duquel les images ne peuvent pas être chargées vers le stockage Amazon S3 via l’API REST.
feature: REST, Storage, Iaas
role: Admin
exl-id: 4d7a8ea7-2856-4b40-a922-fdd356dcaea4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-52689 : les images ne peuvent pas être chargées vers le stockage Amazon S3 via l’API REST

Le correctif ACSD-52689 corrige le problème en raison duquel les images ne peuvent pas être chargées dans le stockage Amazon S3 à l’aide de l’API REST. Ce correctif est disponible lorsque la version 1.1.34 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52689. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images ne peuvent pas être chargées dans le stockage Amazon S3 à l’aide de l’API REST

<u>Procédure à suivre </u> :

1. Configurez REMOTE_STORAGE pour le compartiment Amazon S3.
1. Ajoutez une image au produit à l’aide de l’API Bulk.

   ```POST .../rest/all/async/bulk/V1/products/bySku/media```

   ```
   [
       {
           "sku": "p1",
           "entry": {
               "media_type": "image",
               "position": 0,
               "disabled": false,
               "types": [
                   "image",
                   "thumbnail",
                   "small_image",
                   "swatch_image"
               ],
               "content": {
                "type": "image\/jpeg",
                   "name": "adobe_commerce_test_3",
                   "base64_encoded_data": "/9j/4AAQSkZJRgABAQAAAQABA..."
               }
           }
       }
   ]
   ```

1. Attendez que l’opération en bloc soit traitée.

<u>Résultats attendus</u>

L’image doit être téléchargée dans le compartiment Amazon S3.

<u>Résultats réels</u>

L’image n’est pas automatiquement chargée dans le compartiment Amazon S3.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
