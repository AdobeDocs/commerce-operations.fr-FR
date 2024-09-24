---
title: "MDVA-39993 : les modifications du stock effectuées par le biais de l’API ne sont pas répercutées sur storefront"
description: Le correctif MDVA-3993 résout le problème en raison duquel les modifications d’inventaire effectuées via l’API ne sont pas répercutées sur le storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-39993. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993 : Les modifications du stock effectuées par le biais de l’API ne sont pas répercutées sur le storefront.

Le correctif MDVA-3993 résout le problème en raison duquel les modifications d’inventaire effectuées via l’API ne sont pas répercutées sur le storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-39993. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.3.7-p2 et 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications d’inventaire effectuées par le biais de l’API ne sont pas répercutées sur la page du produit storefront.

<u>Conditions préalables</u> :

Modules d’inventaire installés.

<u>Étapes à reproduire</u> :

1. Assurez-vous que la file d’attente est définie pour s’exécuter avec cron et que cron est installé et en cours d’exécution.
1. Créez un produit configurable (COC001), avec deux couleurs (noir et rouge) et deux tailles (M et L).
1. Créez une option en rupture de stock (COC001-Red-M).
1. Chargez la page de produit configurable sur le storefront et essayez de cliquer sur chaque couleur. Lorsque vous cliquez sur **Rouge**, la taille **M** doit être dépassée car elle est en rupture de stock.
1. Faites en sorte que COC001-Red-M soit en stock à l’aide du point de terminaison API suivant et de la charge utile :

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

1. Vérifiez ce produit simple à partir du serveur principal et vérifiez qu’il est mis à jour vers In Stock.
1. Chargez le produit configurable à partir de l’interface frontale et cliquez sur chaque couleur. Notez la taille **M** lorsque vous cliquez sur **Rouge**.

<u>Résultats attendus</u> :

L’option COC001-Red-M n’est pas dépassée, car nous l’avons mise à jour vers In Stock via l’API.

<u>Résultats réels</u> :

L&#39;option COC001-Red-M est toujours dépassée, même si elle est en stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
