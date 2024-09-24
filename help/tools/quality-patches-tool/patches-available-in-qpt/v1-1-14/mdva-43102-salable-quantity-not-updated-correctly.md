---
title: '''MDVA-43102 : La quantité vendable n''est pas correctement mise à jour'''
description: Le correctif MDVA-43102 corrige le problème en raison duquel la quantité vendable n’est pas correctement mise à jour lorsqu’un remboursement est effectué via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID de correctif est MDVA-43102. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Variables
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102 : La quantité vendable n&#39;a pas été correctement mise à jour.

Le correctif MDVA-43102 corrige le problème en raison duquel la quantité vendable n’est pas correctement mise à jour lorsqu’un remboursement est effectué via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID de correctif est MDVA-43102. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité vendable n&#39;est pas mise à jour correctement lorsqu&#39;un remboursement est effectué à l&#39;aide de l&#39;API REST.

<u>Étapes à reproduire</u> :

1. Ajoutez un élément au panier.
1. Vérifiez le stock Qté et le Salable Qté.
1. Créez une commande.
1. Créez une facture si nécessaire.
1. Envoyez une demande REST pour rembourser la facture en utilisant la payload suivante :

   * méthode/commande hors ligne/`<order_id>`/remboursement
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

1. N’expédiez pas les éléments.
1. Comparez la quantité de stock et la quantité vendable d&#39;avant. Elles doivent toutes deux être mises à jour de la même manière.

<u>Résultats attendus</u> :

La quantité vendable est mise à jour correctement lorsqu’un remboursement est émis avant l’expédition de la commande, et que le produit est renvoyé au stock.

<u>Résultats réels</u> :

La quantité vendable n’est pas mise à jour lorsqu’un remboursement est émis avant l’expédition de la commande et que le produit est renvoyé au stock.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
