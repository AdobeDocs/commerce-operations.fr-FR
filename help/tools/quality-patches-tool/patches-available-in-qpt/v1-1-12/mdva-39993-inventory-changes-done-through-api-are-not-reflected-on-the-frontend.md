---
title: 'MDVA-39993 : les modifications d’inventaire effectuées par le biais de l’API ne sont pas répercutées sur le storefront'
description: Le correctif MDVA-39993 résout le problème où les modifications d’inventaire effectuées via l’API ne sont pas répercutées sur le storefront. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-39993. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993 : les modifications d’inventaire effectuées par le biais de l’API ne sont pas répercutées sur le storefront

Le correctif MDVA-39993 résout le problème où les modifications d’inventaire effectuées via l’API ne sont pas répercutées sur le storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-39993. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.3.7-p2 et 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications d’inventaire effectuées par le biais de l’API ne sont pas reflétées sur la page du produit storefront.

<u>Conditions préalables</u> :

Modules d’inventaire installés.

<u>Procédure à suivre </u> :

1. Assurez-vous que la file d’attente est définie pour s’exécuter avec cron et que cron est installé et en cours d’exécution.
1. Créez un produit configurable (COC001), avec deux couleurs (noir et rouge) et deux tailles (M et L).
1. Rendre une option en rupture de stock (COC001-Rouge-M).
1. Chargez la page produit configurable sur le storefront et essayez de cliquer sur chaque couleur. Lorsque vous cliquez sur **Rouge**, la taille **M** doit être barrée, car elle est en rupture de stock.
1. Effectuez la mise en stock de COC001-Red-M à l’aide du point d’entrée d’API et de la payload suivants :

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Vérifiez ce produit simple à partir du serveur principal et assurez-vous qu’il est mis à jour vers En stock.
1. Chargez le produit configurable à partir du front-end et cliquez sur chaque couleur. Remarquez la taille **M** lorsque vous cliquez sur **Rouge**.

<u>Résultats attendus</u> :

L’option COC001-Red-M n’est pas barrée, car nous l’avons mise à jour sur En stock via l’API.

<u>Résultats réels</u> :

L’option COC001-Red-M est toujours barrée, même si elle est en stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
