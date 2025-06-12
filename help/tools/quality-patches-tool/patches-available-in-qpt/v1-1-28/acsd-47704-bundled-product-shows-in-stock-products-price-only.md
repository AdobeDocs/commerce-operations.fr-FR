---
title: 'ACSD-47704 : Le produit groupé affiche uniquement le prix des produits en stock'
description: Appliquez le correctif ACSD-47704 pour résoudre le problème d’Adobe Commerce où un produit groupé affiche uniquement le prix des produits en stock.
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704 : Le produit groupé affiche uniquement le prix des produits en stock

Le correctif ACSD-47704 corrige le problème de mise en cache incorrecte des prix des segments clients entre les groupes de clients. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-47704. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix d’un produit groupé avec la tarification dynamique activée est incorrect, car seuls les articles en stock sont inclus.

<u>Procédure à suivre </u> :

1. Accédez au panneau d’administration Commerce.
1. Accédez à **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Définissez **[UICONROL Dynamic Price]** sur **[!UICONTROL Yes]**.
1. Éléments groupés :
   * Définir **[!UICONTROL Ship bundle items]** sur **[!UICONTROL Together]**
   * Sélectionner un **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Cocher la case obligatoire
      * Ajoutez tout produit simple en stock, par exemple, Joust Duffle Bag SKU 24-MB01. Avant d&#39;ajouter le produit, notez son prix - 34 $
   * Quantité par défaut : 1
   * Sélectionner un **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Cocher la case obligatoire
      * Ajoutez tout produit simple en stock, différent du produit ajouté à l&#39;étape précédente ; par exemple - Strive Shoulder Pack 24-MB04. Avant d&#39;ajouter le produit, notez son prix - 32 $
      * Quantité par défaut : 1
1. Enregistrer le produit.
1. Accédez à la vitrine et recherchez le produit créé lors des étapes précédentes. Notez son prix - 66 $
(66 = 32 + 34).
Actuellement, le prix du produit groupé est égal à la somme des prix de ses options.
1. Accédez au panneau d’administration Commerce. Accédez à **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Recherchez l’un des produits simples affectés en tant qu’option au produit groupé plus tôt :
SKU 24-MB01 et un prix de 34$.
1. Remplacez sa quantité par 0.
1. Enregistrez le produit.
1. Accédez au storefront et recherchez le bundle du produit créé lors des étapes précédentes. Notez son prix - 32 $. Auparavant, son prix était de 66 $, soit la somme de 34 $ du SKU 24-MB01 et de 32 $ du SKU 24-MB04. Maintenant que le produit 24-MB01 est en rupture de stock, le prix du bundle est indiqué comme 32 $. C&#39;est le prix de l&#39;autre produit, qui est une option en stock.

<u>Résultats attendus</u> :

Le prix des produits groupés pour lesquels la tarification dynamique est activée est calculé de manière cohérente, que les options soient en stock ou en rupture de stock.

<u>Résultats réels</u> :

Le prix du lot de produits pour lequel la tarification dynamique est activée est mal calculé. Elle ne prend en compte que les options en stock, ce qui entraîne l’affichage d’un montant inférieur au montant réel lorsque l’une des options est en rupture de stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
