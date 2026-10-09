---
title: 'MDVA-40545 : seul le premier nœud d’une page est récupéré'
description: Le correctif MDVA-40545 résout le problème où seul le premier nœud d’une page est récupéré, même s’il existe plusieurs nœuds pour la même page. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-40545. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: CMS, Cache
role: Admin
exl-id: f87344e9-5a63-4c38-af2b-1500ef053dec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%
---
# MDVA-40545 : seul le premier nœud d’une page est récupéré

Le correctif MDVA-40545 résout le problème où seul le premier nœud d’une page est récupéré, même s’il existe plusieurs nœuds pour la même page. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5 est installé. L’ID du correctif est MDVA-40545. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Seul le premier nœud d’une page est récupéré, même s’il existe plusieurs nœuds pour la même page.

<u>Procédure à suivre </u> :

1. Dans le panneau d’administration, accédez à **Hiérarchie** et ajoutez deux éléments/nœuds de menu.
1. Ajoutez la même page CMS à chaque nœud.
1. Effacez le cache et vérifiez le serveur frontal.
1. Vérifiez le lien et le chemin de navigation pour le premier sous-menu ajouté.
1. Vérifiez le lien et le chemin de navigation pour le deuxième sous-menu ajouté.

<u>Résultats attendus</u> :

Les chemins de navigation et les liens du deuxième sous-menu sont pertinents pour le deuxième nœud.

<u>Résultats réels</u> :

Les chemins de navigation et les liens du deuxième sous-menu sont identiques à ceux du premier sous-menu.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
