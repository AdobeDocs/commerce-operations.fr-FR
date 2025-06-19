---
title: 'MDVA-43491 : le libellé de l’image de base ne se met pas à jour lors de l’importation au format CSV'
description: Le correctif MDVA-43491 corrige le problème en raison duquel « base_image_label » n’est pas mis à jour lors d’une importation via un fichier CSV pour un site web multi-magasin. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43491. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491 : le libellé de l’image de base ne se met pas à jour lors de l’importation au format CSV

Le correctif MDVA-43491 corrige le problème en raison duquel le `base_image_label` n’est pas mis à jour lors d’une importation via un fichier CSV pour un site web multi-magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43491. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le `base_image_label` n’est pas mis à jour lors de l’importation à l’aide d’un fichier CSV pour un site web multi-magasin.

<u>Conditions préalables</u> :

Un ou plusieurs sites web, magasins et vues de magasin existants autres que ceux par défaut.

<u>Procédure à suivre </u> :

1. Créez un produit.

   * Chargez une image.
   * Attribuez le produit aux sites web nouvellement créés.

1. Exportez le produit au format CSV.
1. Mettez à jour la `base_image_label` de chaque vue de magasin en dupliquant la ligne par défaut du fichier CSV.
1. Importez le fichier CSV. Les libellés de chaque boutique seront correctement mis à jour. Cela peut être vérifié dans l’onglet **Images et vidéos** de la page de modification du produit.
1. Exportez à nouveau le fichier CSV et mettez à jour la colonne `base_image_label` avec des valeurs différentes.
1. Importez à nouveau le fichier CSV.
1. Ouvrez le produit dans l’interface d’administration et vérifiez si l’étiquette a été mise à jour pour chaque vue de magasin.

<u>Résultats attendus</u> :

Le texte secondaire (libellé de l’image) est mis à jour avec la valeur spécifique au magasin conformément au fichier CSV.

<u>Résultats réels</u> :

Le texte de remplacement (libellé de l’image) n’est pas mis à jour avec la valeur `base_image_label` dans le fichier CSV.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
