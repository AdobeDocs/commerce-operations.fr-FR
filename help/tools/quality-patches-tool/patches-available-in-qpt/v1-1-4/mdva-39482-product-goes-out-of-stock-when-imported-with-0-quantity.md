---
title: '"MDVA-39482 : le produit est en rupture de stock s’il est importé avec une quantité "0" avec des commandes en arrière-plan activées"'
description: Le MDVA-39482 corrige le problème de rupture de stock du produit s’il est importé avec une quantité "0" lorsque les MSI et les commandes de sauvegarde sont activés et que le seuil d’rupture de stock est défini sur une valeur moins élevée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID de correctif est MDVA-39482. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39482 : le produit est en rupture de stock s’il est importé avec une quantité &quot;0&quot; avec des commandes en arrière-plan activées.

Le MDVA-39482 corrige le problème de rupture de stock du produit s’il est importé avec une quantité &quot;0&quot; lorsque les MSI et les commandes de sauvegarde sont activés et que le seuil d’rupture de stock est défini sur une valeur moins élevée. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 est installé. L’ID de correctif est MDVA-39482. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le produit est en rupture de stock s’il est importé avec une quantité &quot;0&quot; lorsque les MSI et les commandes en arrière-plan sont activés et que le seuil en rupture de stock est défini sur une valeur moins élevée.

<u>Conditions préalables</u> :

1. Les MSI et les exemples de données doivent être installés.
1. Accédez à **Magasins** > **Configurations** > **Catalogue** > **Inventaire** :
   * Définissez les commandes d’arrière-plan sur &quot;Autoriser une valeur inférieure à 0&quot;.
   * Définissez le seuil en rupture de stock sur &quot;-10&quot;.

<u>Étapes à reproduire</u> :

1. Assurez-vous que le SKU est **En stock** et a une quantité **24-MB01**.
1. Importez le fichier CSV de la source Stock. Veillez à sélectionner &quot;Sources de stock&quot; dans le type d’entité :

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Vérifiez l’état des stocks du produit une fois que les sources de stock ont été importées.

<u>Résultats attendus</u> :

24-MB01 est **En stock** dans Storefront.

<u>Résultats réels</u> :

24-MB01 est **Out-of-Stock** dans Storefront.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) .
