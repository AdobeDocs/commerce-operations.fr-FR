---
title: 'ACSD-53098 : les produits du catalogue partagé ne sont pas reflétés sur le serveur frontal'
description: Appliquez le correctif ACSD-53098 pour résoudre le problème d’Adobe Commerce en raison duquel les produits affectés à un catalogue partagé ne sont pas reflétés sur le serveur frontal lors de l’exécution d’un index partiel.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 25230086-13b5-4b16-b50f-931e9e3d7102
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%
---
# ACSD-53098 : les produits du catalogue partagé ne sont pas reflétés sur le serveur frontal

Le correctif ACSD-53098 corrige le problème où les produits affectés à un catalogue partagé ne se reflètent pas sur le serveur frontal lors de l’exécution d’un index partiel. Ce correctif est disponible lorsque la version 1.1.38 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53098. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits affectés à un catalogue partagé via l’API ne s’affichent pas sur le serveur frontal une fois que l’indexeur partiel exécute la tâche cron, suivie de la tâche cron du client.

<u>Procédure à suivre </u> :

1. Configurez [!DNL RabbitMQ] comme service de file d’attente.
1. Basculez les indexeurs en mode **[!UICONTROL Update on Schedule]**.
1. Créez un catalogue partagé et affectez-le à une entreprise.
1. Créez un produit simple et affectez-le à une catégorie. Exécutez la réindexation partielle :

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Utilisez la requête d’API suivante pour affecter le produit créé au catalogue partagé.

   ```text
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Exécutez la commande cron suivante pour effacer les files d’attente et exécuter la réindexation partielle :

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Connectez-vous au serveur frontal en tant qu’utilisateur de l’entreprise.
1. Vérifiez la page de catégorie front-end.

<u>Résultats attendus</u> :

Les nouveaux produits affectés apparaissent sur le front-end.

<u>Résultats réels</u> :

Les nouveaux produits affectés n’apparaissent pas sur le serveur frontal.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
