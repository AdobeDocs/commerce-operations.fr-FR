---
title: 'MDVA-43102 : la quantité vendable n''a pas été mise à jour correctement'
description: Le correctif MDVA-43102 corrige le problème où la quantité vendable n'est pas mise à jour correctement lorsqu'un remboursement est effectué via l'API REST. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43102. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102 : la quantité vendable n&#39;a pas été mise à jour correctement

Le correctif MDVA-43102 corrige le problème où la quantité vendable n&#39;est pas mise à jour correctement lorsqu&#39;un remboursement est effectué via l&#39;API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43102. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité vendable n’est pas mise à jour correctement lorsqu’un remboursement est effectué à l’aide de l’API REST.

<u>Procédure à suivre </u> :

1. Ajoutez un article au panier.
1. Vérifiez la quantité en stock et la quantité commercialisable.
1. Créer une commande.
1. Créez une facture si nécessaire.
1. Envoyez une requête REST pour rembourser la facture à l’aide de la payload suivante :

   * méthode/commande/`<order_id>`/remboursement hors ligne
   * méthode en ligne/facture/`<invoice_id>`/remboursement

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. N&#39;expédiez pas les articles.
1. Comparez la quantité en stock et la quantité vendable de la précédente. Elles doivent toutes deux être mises à jour de la même quantité.

<u>Résultats attendus</u> :

La quantité commercialisable est mise à jour correctement lorsqu&#39;un remboursement est émis avant l&#39;expédition de la commande et que le produit est retourné au stock.

<u>Résultats réels</u> :

La quantité vendable n&#39;est pas mise à jour lorsqu&#39;un remboursement est émis avant l&#39;expédition de la commande et que le produit est retourné au stock.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
