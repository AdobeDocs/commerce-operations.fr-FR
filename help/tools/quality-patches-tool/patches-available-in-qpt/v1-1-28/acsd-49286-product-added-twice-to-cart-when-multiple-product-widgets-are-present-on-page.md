---
title: "ACSD-49286 : produit ajouté deux fois au panier en présence de plusieurs widgets de produit"
description: Appliquez le correctif ACSD-49286 pour résoudre le problème Adobe Commerce en raison duquel le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286 : produit ajouté deux fois au panier en présence de plusieurs widgets de produit

Le correctif ACSD-49286 corrige le problème en raison duquel le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-49286. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit est ajouté deux fois à un panier lorsque plusieurs widgets de produit sont présents sur la page.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur et accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Dans la section de contenu, cliquez sur **[!UICONTROL Edit]** à l’aide de [!DNL Page Builder].
1. Ajoutez deux éléments de ligne à **[!UICONTROL Content]**.
1. Ajoutez des produits aux deux éléments de ligne.
1. Dans la première ligne, définissez l’aspect du produit sur [!UICONTROL Product Grid] et sélectionnez n’importe quelle catégorie à afficher.
1. Dans la deuxième ligne, définissez l’aspect du produit sur [!UICONTROL Product Carousel] et sélectionnez toute autre catégorie à afficher.
1. Accédez au storefront **[!UICONTROL Home Page]** et ajoutez un produit à partir de la grille de produits.
1. Ajoutez un autre produit de [!UICONTROL Product Carousel].

<u>Résultats attendus</u> :

La quantité de produit ne doit pas doubler après l’ajout d’un produit au panier à partir de [!UICONTROL Product Grid].

<u>Résultats réels</u> :

La quantité de produit double après l’ajout d’un produit au panier à partir de [!UICONTROL Product Grid].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure. 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
