---
title: 'MDVA-42689 : erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits lors de l’importation'
description: Le correctif MDVA-42689 résout le problème où les utilisateurs obtiennent une erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits pendant l’importation. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-42689. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%
---
# MDVA-42689 : erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits lors de l’importation

Le correctif MDVA-42689 résout le problème où les utilisateurs obtiennent une erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits pendant l’importation. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID du correctif est MDVA-42689. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Adobe Commerce renvoie une erreur de violation de contrainte d’intégrité lors de la mise à jour des catégories de produits lors de l’importation.

<u>Procédure à suivre </u> :

1. Configurez deux sites web.
1. Créez des sous-catégories sous la catégorie racine jusqu’à deux niveaux sur la page de catégorie. Par exemple, Catégorie racine > **Engrenage** > **Montres**.
1. Créez deux produits simples et affectez les deux produits à la même catégorie **Engrenage** > **Montres**.
1. Attribuez un produit simple aux deux sites web.
1. Enregistrez le produit.
1. Préparez un fichier CSV à importer. Il doit y avoir deux enregistrements de produit avec des vues de magasin différentes. L’un des produits doit appartenir à ces deux vues de magasin.
1. Importez maintenant le fichier CSV en accédant à **Système** > **Importer** > **Type d’entité** (Produits).

<u>Résultats attendus</u> :

Le fichier CSV est importé sans erreur.

<u>Résultats réels</u> :

Adobe Commerce renvoie l’erreur suivante :

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
