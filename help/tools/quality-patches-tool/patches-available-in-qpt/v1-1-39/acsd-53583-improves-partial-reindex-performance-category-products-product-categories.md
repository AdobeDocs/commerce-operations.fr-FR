---
title: 'ACSD-53583 : amélioration des performances de réindexation partielle pour les indexeurs [!UICONTROL Category Products] et [!UICONTROL Product Categories]'
description: Appliquez le correctif ACSD-53585 pour améliorer les performances de réindexation partielle pour les indexeurs de catégories de produits et de catégories de produits.
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
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
source-wordcount: '409'
ht-degree: 0%
---
# ACSD-53583 : amélioration des performances de réindexation partielle pour les indexeurs de catégories de produits et de catégories de produits

Le correctif ACSD-53583 améliore les performances de réindexation partielle des indexeurs *Produits de catégorie* et *Catégories de produits*. Ce correctif est disponible lorsque la version 1.1.39 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53583. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3
* Non compatible avec le module [!DNL Live Search]. Pour appliquer ce correctif à [!DNL Live Search] installation, demandez un correctif ACSD-55719 supplémentaire.

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réindexation partielle prend plus de temps que la réindexation complète.

<u>Procédure à suivre </u> :

1. Convertissez tous les indexeurs en *Mettre à jour selon le calendrier*.
1. Générer des données avec le [!DNL Performance Toolkit] (profil moyen).
1. Apportez des modifications à tous les produits et catégories afin qu’ils se trouvent dans la liste d’attente de l’index et que tous les index soient inactifs.
1. Effectuez une réindexation partielle pour les indexeurs *Produits de catégorie* et *Catégories de produits*.

<u>Résultats attendus</u> :

La réindexation partielle est appelée une fois par produit et prend presque le même temps que la réindexation complète, car tous les produits et toutes les catégories ont été modifiés.

<u>Résultats réels</u> :

La réindexation partielle est appelée plusieurs fois par produit et prend plus de temps que la réindexation complète.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
