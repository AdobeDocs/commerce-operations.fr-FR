---
title: 'ACSD-56790 : l’option **[!UICONTROL move out of stock to bottom]** ne fonctionne pas lors du tri des produits dans le  [!DNL Visual Merchandiser]'
description: Appliquez le correctif ACSD-56790 pour résoudre le problème d’Adobe Commerce en raison duquel l’option Déplacer le stock vers le bas ne fonctionne pas lors du tri des produits dans le marchandiseur visuel.
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790 : **[!UICONTROL move out of stock to bottom]** option ne fonctionne pas lors du tri des produits dans le [!DNL Visual Merchandiser]

Le correctif ACSD-56790 corrige le problème en raison duquel l’option Déplacer le stock vers le bas ne fonctionne pas lors du tri des produits dans le [!DNL Visual Merchandiser]. Ce correctif est disponible lorsque la version 1.1.44 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-56790. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’option **[!UICONTROL move out of stock to bottom]** ne fonctionne pas lors du tri des produits dans le [!DNL Visual Merchandiser]

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** et créez les attributs suivants.
1. Créez un nouveau site web : **non principal**.
1. Créez un **Boutique non principale** sur ce nouveau site Web.
1. Créez deux magasins :

   * Tout d’abord dans la **Boutique du site web principal**.
   * Deuxième dans le **Magasin non principal**.

1. Créez deux sources :
   * Lettres.
   * Nombres.

1. Créer deux stocks :
   * Première main - canaux de vente : site web principal - sources attribuées : lettres.
   * Deuxième non-principal - canaux de vente : non-principal - sources affectées : nombres.

1. Créez trois produits simples sur les deux sites web, tous dans la catégorie Par défaut, tous affectés aux deux sources :

   * ProduitA - Qté *10* en lettres, Qté *0* en chiffres.
   * Produit1 - Qté *0* en lettres, Qté *10* en chiffres.
   * ProduitA1 - Qté *10* en lettres, Qté *10* en chiffres.

1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** et sélectionnez **[!UICONTROL Default category]**.
1. Remplacez la portée par **First**.
1. Développez les Produits dans la section Catégorie .
1. Sélectionnez l’ordre de tri : **[!UICONTROL move out of stock to bottom]**

<u>Résultats attendus</u> :

La liste des produits avec les produits **en rupture de stock** est déplacée vers le bas.

<u>Résultats réels</u> :

Le chargement des produits échoue. Une page redirige vers le tableau de bord d’administration avec le message d’erreur : `Invalid security or form key. Please refresh the page`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
