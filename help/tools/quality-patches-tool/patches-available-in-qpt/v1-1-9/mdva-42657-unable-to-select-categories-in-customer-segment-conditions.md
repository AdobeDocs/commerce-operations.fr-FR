---
title: 'MDVA-42657 : impossible de sélectionner des catégories dans les conditions de segment client'
description: Le correctif MDVA-42657 résout le problème en raison duquel l’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions du segment client. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-42657. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%
---
# MDVA-42657 : impossible de sélectionner des catégories dans les conditions de segment client

Le correctif MDVA-42657 résout le problème en raison duquel l’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions du segment client. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID du correctif est MDVA-42657. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut pas sélectionner de catégories dans les conditions de segment client.

<u>Procédure à suivre </u> :

1. Accédez à **Clients** > **Segments**.
1. Créez un segment.
1. Accédez au segment nouvellement créé et cliquez sur **Conditions** dans le volet de navigation de gauche.
1. Cliquez sur le signe plus vert.
1. Sélectionnez Historique du produit sous Produits.
1. Remplacez « vu » par « ordonné ».
1. Remplacez « ALL » par « ANY ».
1. Cliquez sur le signe plus vert imbriqué et sélectionnez Catégorie.
1. Cliquez sur le signe **...**, puis sur l’icône du sélecteur (à gauche de la coche).
1. Ouvrez la console de développement du navigateur.
1. Cochez les cases d’une ou de plusieurs catégories et notez l’erreur JavaScript générée dans la console.
1. Cliquez sur le bouton **Enregistrer**.
1. Revenez à la condition et vérifiez si les catégories sélectionnées sont enregistrées.

<u>Résultats attendus</u> :

Les catégories sélectionnées sont enregistrées et sélectionnées lors de l’affichage/de la modification des conditions du segment.

<u>Résultats réels</u> :

Les catégories sélectionnées sont manquantes et n&#39;ont pas été enregistrées correctement. L’erreur suivante s’affiche dans la console :

```text
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
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
