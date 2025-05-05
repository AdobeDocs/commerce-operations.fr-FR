---
title: 'MDVA-42584 : statut du stock du produit configurable non mis à jour automatiquement'
description: Le correctif MDVA-42584 résout le problème en raison duquel l’état du stock du produit configurable n’est pas mis à jour automatiquement lorsque son produit simple est mis à jour. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID de correctif est MDVA-42584. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584 : statut du stock du produit configurable non mis à jour automatiquement

Le correctif MDVA-42584 résout le problème en raison duquel l’état du stock du produit configurable n’est pas mis à jour automatiquement lorsque son produit simple est mis à jour. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID de correctif est MDVA-42584. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état du stock du produit configurable dans le serveur principal n’est pas mis à jour automatiquement lorsque son produit simple est défini sur **In Stock** via l’API ou l’importation.

<u>Conditions préalables</u> :

MSI installé.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable, **InvCheck001**, avec deux options : **InvCheck001-M** et **InvCheck01-L**.
1. Les deux produits simples doivent avoir une quantité et être **En stock** afin que le produit configurable soit également **En stock** sur le serveur principal.
1. Maintenant, mettez à jour les produits simples et définissez Quantité sur **0** et État du stock sur **Out of Stock**.
1. Actualisez le produit configurable et vérifiez que l’état du stock est mis à jour sur **Out of Stock**.
1. Utilisez le point d’entrée API suivant et définissez le produit simple **InvCheck001-M** sur **In Stock** avec Quantity > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Accédez au serveur principal et vérifiez la quantité et l’état du stock du produit simple **InvCheck001-M**. Il est mis à jour vers **En stock**.
1. Actualisez le produit configurable et vérifiez l’état du stock.

<u>Résultats attendus</u> :

L’état du stock du produit configurable **InvCheck001** dans le serveur principal est automatiquement mis à jour vers **In Stock**.

<u>Résultats réels</u> :

L’état du stock du produit configurable est toujours **En rupture de stock**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
