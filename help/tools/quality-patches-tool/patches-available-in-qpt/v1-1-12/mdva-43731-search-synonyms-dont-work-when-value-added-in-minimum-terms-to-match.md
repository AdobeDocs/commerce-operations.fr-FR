---
title: 'MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans « Termes minimum à faire correspondre »'
description: Le correctif MDVA-43731 corrige le problème où les synonymes de recherche cessent de fonctionner lorsqu’une valeur est ajoutée dans « Termes minimum à faire correspondre ». Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-43731. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%
---
# MDVA-43731 : les synonymes de recherche ne fonctionnent pas lorsque la valeur est ajoutée dans « Termes minimum à faire correspondre »

Le correctif MDVA-43731 corrige le problème où les synonymes de recherche cessent de fonctionner lorsqu’une valeur est ajoutée dans « Termes minimum à faire correspondre ». Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID du correctif est MDVA-43731. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les synonymes de recherche ne fonctionnent plus lorsqu’une valeur est ajoutée dans « Termes à faire correspondre au minimum ».

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec des exemples de données.
1. Configurez Elasticsearch7 comme moteur de recherche.
1. Recherchez le mot « Veste ». Une liste de produits s’affiche.
1. Ajoutez le paramètre [4&lt;60%] dans **Configuration** > **Catalogue** > **Recherche de catalogue** > **Nombre minimum de termes à faire correspondre**.
1. Effacez le cache de configuration et effectuez une réindexation.
1. Recherchez à nouveau le mot « Veste » et notez qu’une liste de produits s’affiche.
1. Accédez à **Marketing** > **SEO et recherche** > **Synonymes de recherche**.
1. Créez des synonymes de recherche en ajoutant les synonymes suivants : veste, bagtecs, express plus.
1. Effectuez une réindexation.
1. Effectuez une recherche de produits à l’aide de l’un des synonymes. Par ex., veste.

<u>Résultats attendus</u> :

Vous obtenez la même liste de produits qu’auparavant dans les résultats de la recherche.

<u>Résultats réels</u> :

Aucun produit ne s’affiche dans les résultats de la recherche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
