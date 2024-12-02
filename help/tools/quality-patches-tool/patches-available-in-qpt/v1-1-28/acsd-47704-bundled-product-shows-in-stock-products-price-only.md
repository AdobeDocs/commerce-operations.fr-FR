---
title: 'ACSD-47704 : Le produit groupé affiche le prix de dans les produits en stock uniquement'
description: Appliquez le correctif ACSD-47704 pour résoudre le problème d’Adobe Commerce en raison duquel un produit fourni indique uniquement le prix de dans les produits boursiers.
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704 : Le produit groupé affiche le prix de dans les produits en stock uniquement

Le correctif ACSD-47704 corrige le problème en raison duquel les prix des segments de clients sont incorrectement mis en cache entre les groupes de clients. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 est installé. L’ID de correctif est ACSD-47704. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix d’un produit en lot dont la fonction de tarification dynamique est activée est incorrect en raison de l’inclusion des articles en stock uniquement.

<u>Étapes à reproduire</u> :

1. Accédez au panneau d’administration de Commerce.
1. Accédez à **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Définissez **[UICONROL Dynamic Price]** sur **[!UICONTROL Yes]**.
1. Regrouper des éléments :
   * Définissez **[!UICONTROL Ship bundle items]** sur **[!UICONTROL Together]**
   * Sélectionner **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Case à cocher Marquer obligatoire
      * Ajoutez n’importe quel produit simple en stock ; par exemple, Joust Duffle Bag SKU 24-MB01. Avant d’ajouter le produit, notez son prix - 34 $
   * Quantité par défaut : 1
   * Sélectionner **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Case à cocher Marquer obligatoire
      * Ajoutez n’importe quel produit simple en stock, différent du produit ajouté à l’étape précédente ; par exemple : Strive Shoulder Pack 24-MB04. Avant d’ajouter le produit, notez son prix - 32 $
      * Quantité par défaut : 1
1. Enregistrez le produit.
1. Accédez au storefront et recherchez le produit créé lors des étapes précédentes. Notez son prix - 66 $
(66 = 32 + 34).
Actuellement, le prix du produit groupé est égal à la somme des prix de ses options.
1. Accédez au panneau d’administration de Commerce. Accédez à **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Recherchez l’un des produits simples affectés en tant qu’option au produit groupé plus tôt :
SKU 24-MB01 et un prix de 34 $.
1. Remplacez sa quantité par 0.
1. Enregistrez le produit.
1. Accédez au storefront et recherchez le produit du bundle créé lors des étapes précédentes. Notez son prix - 32 $. Auparavant, le prix était de 66 $, ce qui représentait la somme de 34 $ de la SKU 24-MB01 et de 32 $ de la SKU 24-MB04. Maintenant que le produit 24-MB01 est en rupture de stock, le prix du lot est indiqué comme 32 $. C&#39;est le prix de l&#39;autre produit, qui est une option en stock.

<u>Résultats attendus</u> :

Le prix des produits groupés pour lesquels la fonction de tarification dynamique est activée est calculé de manière cohérente, que les options soient en stock ou en rupture de stock.

<u>Résultats réels</u> :

Le prix du produit groupé avec la fonction de tarification dynamique activée est mal calculé. Elle ne prend en compte que les options en stock, ce qui se traduit par un affichage inférieur à celui réel lorsque l’une des options est en rupture de stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
