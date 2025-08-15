---
title: 'MDVA-42584 : statut des stocks du produit configurable non mis à jour automatiquement'
description: Le correctif MDVA-42584 résout le problème où l'état du stock du produit configurable n'est pas mis à jour automatiquement lorsque son produit simple est mis à jour. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-42584. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584 : statut des stocks du produit configurable non mis à jour automatiquement

Le correctif MDVA-42584 résout le problème où l&#39;état du stock du produit configurable n&#39;est pas mis à jour automatiquement lorsque son produit simple est mis à jour. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 est installé. L’ID du correctif est MDVA-42584. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’état du stock du produit configurable sur le serveur principal n’est pas mis à jour automatiquement lorsque son produit simple est défini sur **En stock** par le biais de l’API ou de l’importation.

<u>Conditions préalables</u> :

MSI installé.

<u>Procédure à suivre </u> :

1. Créez un produit configurable, **InvCheck001**, avec deux options : **InvCheck001-M** et **InvCheck001-L**.
1. Les deux produits simples doivent avoir une Quantité et ils doivent être **En stock** de sorte que le produit configurable soit également **En stock** en arrière-plan.
1. Maintenant, mettez à jour les produits simples et définissez Quantité sur **0** et État du stock sur **En rupture de stock**.
1. Actualisez le produit configurable et vérifiez que l’état du stock est mis à jour à **En rupture de stock**.
1. Utilisez le point d’entrée d’API suivant et définissez le produit simple **InvCheck001-M** sur **En stock** avec une quantité > 0.

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

1. Accédez au serveur principal et vérifiez la quantité et l’état du stock du produit simple **InvCheck001-M**. Il est mis à jour à **En stock**.
1. Actualisez le produit configurable et vérifiez l’état du stock.

<u>Résultats attendus</u> :

Le statut de stock du produit configurable **InvCheck001** dans le serveur principal est automatiquement mis à jour à **En stock**.

<u>Résultats réels</u> :

Le statut de stock du produit configurable est toujours **En rupture de stock**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
