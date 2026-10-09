---
title: 'ACSD-49973 : amélioration des performances de récupération des produits groupés via [!DNL GraphQL]'
description: Appliquez le correctif ACSD-49973 pour résoudre le problème d’Adobe Commerce en raison duquel les performances se dégradent lors de la récupération des produits groupés via [!DNL GraphQL].
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%
---
# ACSD-49973 : amélioration des performances de récupération des produits groupés via [!DNL GraphQL]

Le correctif ACSD-49973 améliore les performances de récupération des produits groupés via [!DNL GraphQL]. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-49973. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les performances se dégradent lors de la récupération de produits groupés via [!DNL GraphQL].

<u>Conditions préalables</u> :

Créez 2 000 produits groupés à l’aide de la boîte à outils [&#x200B; Performance](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html?lang=fr).

<u>Procédure à suivre </u> :

1. Activez l’enregistreur de requêtes [!DNL DB] :

   ```shell
   bin/magento dev:query-log:enable
   ```

1. Exécutez la requête [!DNL GraphQL] suivante :

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Recherchez `var/log/db.log` requêtes dans la table `catalog_product_bundle_selection`.

<u>Résultats attendus</u> :

Les requêtes de la table `catalog_product_bundle_selection` ne doivent pas être présentes dans le `var/log/db.log`.

<u>Résultats réels</u> :

2 000 requêtes sont déclenchées en même temps pour `catalog_product_bundle_selection` table, ce qui entraîne une dégradation des performances.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
