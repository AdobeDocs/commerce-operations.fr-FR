---
title: "ACSD-45675 : l’exportation de produits utilise des noms de catégorie de l’étendue de vue de magasin par défaut"
description: Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation de produits utilise des noms de catégorie de la portée d’affichage de magasin par défaut. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 est installé. L’ID de correctif est ACSD-45675. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-45675 : l’exportation de produits utilise des noms de catégorie de l’étendue de vue de magasin par défaut.

Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation de produits utilise des noms de catégorie de la portée d’affichage de magasin par défaut. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 est installé. L’ID de correctif est ACSD-45675. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation de produits utilise des noms de catégorie provenant de la portée de la vue de magasin par défaut.

<u>Étapes à reproduire</u> :

1. Créez une vue de magasin personnalisée **[!UICONTROL Thai]** dans le magasin principal.
1. Faites de **[!UICONTROL Thai]** la vue de magasin par défaut du site web principal.
1. Créez la structure de catégorie suivante sous **[!UICONTROL Default Category]** :

   *[!UICONTROL Default category/Tea/Black]*

1. Sélectionnez la catégorie **[!UICONTROL Tea]** et remplacez **[!UICONTROL Scope]** par **[!UICONTROL Thai]**.
1. Définissez le **[!UICONTROL Category Name]** sur **[!UICONTROL ชาดำ]**.
1. Créez un produit simple **[!UICONTROL SP001]** et affectez la catégorie **[!UICONTROL Black]**.
1. Vérifiez que le cron ne s’exécute pas.
1. Exportez un produit. Filtrez par SKU et sélectionnez **[!UICONTROL SP001]**.
1. Vérifiez la colonne **[!UICONTROL categories]** dans le fichier CSV exporté.

<u>Résultats attendus</u> :

Comme aucun magasin n’a été sélectionné lors de l’exportation, vous devez obtenir un chemin de catégorie du type : *[!UICONTROL Default Category/Tea/Black]*.

<u>Résultats réels</u> :

Le chemin de catégorie comporte plusieurs langues : *[!UICONTROL Default Category/ชาดำ/Black]*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tools] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans [!DNL QPT], reportez-vous à la section [Correctifs disponibles dans [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) du guide de l’outil Correctifs de qualité.
