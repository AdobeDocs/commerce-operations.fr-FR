---
title: 'ACSD-57074 : l’attribut personnalisé *Oui/Non* avec le préfixe « price _* » dans l’attribut « attribute_code » ne fonctionne pas avec l’indexation'
description: Appliquez le correctif ACSD-57074 pour résoudre le problème d’Adobe Commerce en raison duquel l’attribut personnalisé *Oui/Non* avec le préfixe « price _* » de l’attribut « attribute_code » ne fonctionne pas avec l’indexation.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-57074 : *Oui/Non* l’attribut personnalisé avec préfixe `price_*` dans `attribute_code` attribut ne fonctionne pas avec l’indexation

Le correctif ACSD-57074 corrige le problème en raison duquel l’attribut personnalisé *Oui/Non* avec `price_*` préfixe dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation. Ce correctif est disponible lorsque la version 1.1.47 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-57074. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut personnalisé *Oui/Non* avec `price_*` préfixe dans l’attribut `attribute_code` ne fonctionne pas avec l’indexation.

<u>Procédure à suivre </u> :

1. Créez un attribut de produit personnalisé avec les options suivantes :
   * *[!UICONTROL Catalog Input Type]* : *Oui/Non*
   * *[!UICONTROL Scope]* : *StoreView*
   * *[!UICONTROL Use in Search]* : *Oui*
1. Attribuez l’attribut au jeu d’attributs par défaut.
1. Créez un produit avec l’attribut que nous avons créé.
1. Affectez le produit que nous venons de créer à une catégorie.
1. Exécutez la réindexation complète.

<u>Résultats attendus</u> :

Le produit s’affiche dans la catégorie affectée.

<u>Résultats réels</u> :

Le produit n’apparaît pas sur la page de catégorie principale.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
