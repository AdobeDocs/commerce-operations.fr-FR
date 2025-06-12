---
title: 'ACSD-49286 : produit ajouté deux fois au panier lorsque plusieurs widgets de produit sont présents'
description: Appliquez le correctif ACSD-49286 pour résoudre le problème d’Adobe Commerce en raison duquel le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286 : produit ajouté deux fois au panier lorsque plusieurs widgets de produit sont présents

Le correctif ACSD-49286 corrige le problème en raison duquel le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49286. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Dans la section du contenu, cliquez sur **[!UICONTROL Edit]** à l’aide de [!DNL Page Builder].
1. Ajoutez deux éléments de ligne à **[!UICONTROL Content]**.
1. Ajoutez des produits dans les deux éléments de ligne.
1. Dans la première ligne, définissez l’apparence du produit sur [!UICONTROL Product Grid] et sélectionnez n’importe quelle catégorie à afficher.
1. Dans la deuxième ligne, définissez l’apparence du produit sur [!UICONTROL Product Carousel] et sélectionnez toute autre catégorie à afficher.
1. Accédez au **[!UICONTROL Home Page]** storefront et ajoutez un produit à partir de la grille de produits.
1. Ajoutez un autre produit à partir de [!UICONTROL Product Carousel].

<u>Résultats attendus</u> :

La quantité de produit ne doit pas doubler après l’ajout d’un produit au panier à partir de [!UICONTROL Product Grid].

<u>Résultats réels</u> :

La quantité de produits double après l’ajout d’un produit au panier à partir de [!UICONTROL Product Grid].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud . 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
