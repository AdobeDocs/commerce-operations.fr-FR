---
title: "ACSD-47988 : export de produit supprime les balises d’HTML de la description du produit du créateur de pages"
description: Appliquez le correctif ACSD-47988 pour résoudre le problème Adobe Commerce en raison duquel l’exportation du produit supprime les balises d’HTML de la description du produit du créateur de pages.
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-47988 : exportation de produits supprime les balises d’HTML de la description du produit du créateur de pages

Le correctif ACSD-47988 corrige le problème en raison duquel l’exportation de produit supprime les balises d’HTML de la description du produit du créateur de pages. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 est installé. L’ID de correctif est ACSD-47988. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation de produits supprime les balises d’HTML de la description du produit du créateur de pages.

<u>Étapes à reproduire</u> :

1. Créez des produits avec un certain HTML dans la description. Utilisez l’élément d’HTML du créateur de pages pour insérer des balises d’HTML.
1. Exportez les produits à l’aide de la fonctionnalité d’import/export d’Adobe Commerce.
1. Importez le fichier CSV exporté.
1. Ouvrez le produit et vérifiez les éléments d’HTML sous la description.

<u>Résultats attendus</u> :

Les balises d’HTML restent dans la description du produit après l’importation du même contenu.

<u>Résultats réels</u> :

Les balises d’HTML sont supprimées après l’importation.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
