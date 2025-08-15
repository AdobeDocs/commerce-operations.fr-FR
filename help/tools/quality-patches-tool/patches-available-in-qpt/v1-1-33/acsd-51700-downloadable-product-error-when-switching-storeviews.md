---
title: 'ACSD-51700 : erreur lors du changement d’affichage de la boutique sur la page d’édition de produit téléchargeable'
description: Appliquez le correctif ACSD-51700 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit lors du changement d’affichage de la boutique sur une page de modification de produit téléchargeable par l’administrateur.
feature: Products
role: Admin
exl-id: dd3da026-ac72-440c-8632-8a3ca27fc134
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51700 : erreur lors du changement d’affichage de la boutique sur la page d’édition de produit téléchargeable

Le correctif ACSD-51700 corrige le problème où une erreur se produit lors du changement d’affichage de la boutique sur une page de modification de produit téléchargeable par l’administrateur. Ce correctif est disponible lorsque la version 1.1.33 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51700. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

## Problème

Une erreur se produit lors du changement d’affichage de la boutique sur une page de modification de produit téléchargeable dans l’administration.

<u>Procédure à suivre </u> :

1. Créez un produit téléchargeable avec un nom, une [!DNL SKU] et un prix. N’ajoutez aucun lien et enregistrez le produit.
1. Basculez de toutes les vues de magasin vers la vue de magasin par défaut.
1. Créez un lien pour le produit téléchargeable et enregistrez-le.
1. Basculez de la vue de magasin par défaut à toutes les vues de magasin.

<u>Résultats attendus</u> :

Les produits liés sont visibles.

<u>Résultats réels</u> :

L’erreur suivante s’affiche :

*Fonctionnalité obsolète : number_format() : la transmission de la valeur null au paramètre #1 ($num) de type flottant est obsolète dans vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php sur la ligne 228*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
