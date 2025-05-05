---
title: "ACSD-51700 : erreur lors du changement d’affichage des magasins sur la page de modification des produits téléchargeable"
description: Appliquez le correctif ACSD-51700 pour résoudre le problème Adobe Commerce qui se produit lorsqu’une erreur se produit lors du changement d’affichage de magasin sur une page de modification de produit téléchargeable dans l’administrateur.
feature: Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51700 : erreur lors du changement d’affichage des magasins sur la page de modification des produits téléchargeable

Le correctif ACSD-51700 corrige le problème d’erreur qui se produit lors du changement de vues de magasin sur une page de modification de produit téléchargeable dans l’administrateur. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.33 est installé. L’ID de correctif est ACSD-51700. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p1

## Problème

Une erreur se produit lors du changement de vues de magasin sur une page de modification de produit téléchargeable dans l’administrateur.

<u>Étapes à reproduire</u> :

1. Créez un produit téléchargeable avec le nom, le [!DNL SKU] et le prix. N’ajoutez aucun lien et enregistrez le produit.
1. Basculez de toutes les vues de magasin vers la vue de magasin par défaut.
1. Créez un lien pour le produit téléchargeable et enregistrez-le.
1. Passez de la vue de magasin par défaut à toutes les vues de magasin.

<u>Résultats attendus</u> :

Les produits liés sont visibles.

<u>Résultats réels</u> :

L&#39;erreur suivante s&#39;affiche :

*Fonctionnalité obsolète : number_format() : la transmission de la valeur null au paramètre #1 ($num) de type float est obsolète dans vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php sur la ligne 228*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
