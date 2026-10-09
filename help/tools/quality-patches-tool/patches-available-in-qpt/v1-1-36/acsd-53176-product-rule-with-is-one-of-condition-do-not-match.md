---
title: 'ACSD-53176 : la règle de produit avec la condition « est l’un des » ne correspond pas.'
description: Appliquez le correctif ACSD-53176 pour résoudre le problème d’Adobe Commerce en raison duquel la règle de produit associée « est l’une des » ne fonctionne pas correctement pour « Produits à faire correspondre ».
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%
---
# ACSD-53176 : la règle de produit avec `is one of` condition ne correspond pas

Le correctif ACSD-53176 corrige le problème en raison duquel la condition de `is one of` de la règle de produit associée ne fonctionne pas correctement pour **Products to Match**. Ce correctif est disponible lorsque la version 1.1.36 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53176. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La condition de `is one of` de la règle de produit associée ne fonctionne pas correctement pour **Products to Match**.

<u>Procédure à suivre </u> :

1. Créez 3 à 4 produits.
1. Créez une règle de produit associée.

   Définissez la règle pour qu’elle corresponde à deux produits ou plus :
   * `SKU is one of "S1,S2".`

   Définissez la règle pour afficher deux éléments ou plus :
   * `Product SKU is one of constant value "S2,S3".`

1. Ouvrez le produit S1 sur le Storefront.

<u>Résultats attendus</u> :

Les produits associés « S2 » et « S3 » sont affichés sur les pages de produits « S1 » et « S2 ».

<u>Résultats réels</u> :

Les produits associés ne s’affichent pas sur les pages de produits.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
