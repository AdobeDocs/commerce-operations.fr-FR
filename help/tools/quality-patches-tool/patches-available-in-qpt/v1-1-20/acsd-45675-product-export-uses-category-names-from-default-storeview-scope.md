---
title: 'ACSD-45675 : l’exportation de produits utilise des noms de catégories provenant de la portée d’affichage du magasin par défaut'
description: Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation du produit utilise des noms de catégorie de la portée d’affichage du magasin par défaut. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 est installé. L’ID du correctif est ACSD-45675. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
source-git-commit: b1f7739688a538b25b738efc337fa81f15a5bac8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-45675 : l’exportation de produits utilise des noms de catégories provenant de la portée d’affichage du magasin par défaut

Le correctif ACSD-45675 corrige le problème en raison duquel l’exportation du produit utilise des noms de catégorie de la portée d’affichage du magasin par défaut. Ce correctif est disponible lorsque la version 1.1.20 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-45675. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation de produits utilise des noms de catégorie de la portée d’affichage du magasin par défaut.

<u>Procédure à suivre </u> :

1. Créez un **[!UICONTROL Thai]** d’affichage de magasin personnalisé dans le magasin principal.
1. **[!UICONTROL Thai]** l’affichage par défaut du magasin du site web principal.
1. Créez la structure de catégories suivante sous **[!UICONTROL Default Category]** :

   *[!UICONTROL Default category/Tea/Black]*

1. Sélectionnez le **[!UICONTROL Tea]** de catégorie et modifiez la **[!UICONTROL Scope]** en **[!UICONTROL Thai]**.
1. Définissez le **[!UICONTROL Category Name]** comme **[!UICONTROL ชาดำ]**.
1. Créez un **[!UICONTROL SP001]** de produit simple et affectez-lui le **[!UICONTROL Black]** de catégorie.
1. Assurez-vous que la commande cron ne s’exécute pas.
1. Effectuez une exportation de produit. Filtrez par SKU et sélectionnez **[!UICONTROL SP001]**.
1. Vérifiez la colonne **[!UICONTROL categories]** dans le fichier CSV exporté.

<u>Résultats attendus</u> :

Comme aucun magasin n’a été sélectionné lors de l’exportation, vous devriez obtenir un chemin de catégorie comme celui-ci : *[!UICONTROL Default Category/Tea/Black]*.

<u>Résultats réels</u> :

Le chemin d’accès à la catégorie comporte des langues mixtes : *[!UICONTROL Default Category/ชาดำ/Black]*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tools] > Utilisation ](/help/tools/quality-patches-tool/usage.md) dans le guide de l’outil de correctifs de qualité.
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
