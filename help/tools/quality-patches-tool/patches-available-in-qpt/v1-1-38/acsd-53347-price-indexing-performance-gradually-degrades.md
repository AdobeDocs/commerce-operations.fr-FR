---
title: 'ACSD-53347 : Les performances d''indexation des prix se dégradent progressivement au fil du temps'
description: Appliquez le correctif ACSD-53347 pour résoudre le problème d’Adobe Commerce où les performances se dégradent progressivement lors de la réindexation des prix pour un catalogue de produits volumineux.
feature: Price Indexer
role: Admin
exl-id: 8986b685-55e4-47c7-852c-aca18e3b02e9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b0d35b91-b9b0-5983-b37c-f35bd2650b53
    internal-label: Price Indexer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%
---
# ACSD-53347 : Les performances d&#39;indexation des prix se dégradent progressivement au fil du temps

Le correctif ACSD-53347 corrige le problème en raison duquel les performances se dégradent progressivement lors de la réindexation des prix pour un catalogue de produits volumineux. Ce correctif est disponible lorsque la version 1.1.38 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-53347. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de la réindexation des prix d’un catalogue de produits volumineux, les performances des requêtes exécutées pendant le processus d’indexation se dégradent progressivement.

<u>Procédure à suivre </u> :

1. Créez un catalogue simple volumineux et affectez des options personnalisées à ces produits (les options personnalisées utilisent une table temporaire lors de l’indexation).
1. Créez au moins 200 groupes de clients pour améliorer la visibilité du problème.
1. Créez dix sites web ou plus et attribuez tous les produits à chacun d’eux.
1. Notez que les produits importés sont presque identiques, ne différant que par leur SKU et leur nom.
1. Activez **[!UICONTROL DB Logging]**.
1. Exécutez la commande `bin/magento index:reindex catalog_product_price`.
1. Recherchez *DELETE FROM`catalog_product_index_price_opt_agr_temp`* dans le `db.log`.

<u>Résultats attendus</u> :

L’exécution des *requêtes de base de données* s’exécute efficacement.

<u>Résultats réels</u> :

Les performances des requêtes *DB* sur les tables temporaires deviennent lentes au fil du temps. Par conséquent, l&#39;indexation des prix prend beaucoup de temps.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
