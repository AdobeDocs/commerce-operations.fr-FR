---
title: 'MDVA-32776 : statut des stocks non mis à jour avec le placement de la commande'
description: Le correctif MDVA-32776 corrige le problème en raison duquel le statut du stock n’est pas mis à jour lorsqu’une commande est passée mais n’est pas envoyée. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-32776. Notez que le problème a été résolu dans Adobe Commerce 2.4.2.
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776 : statut des stocks non mis à jour avec le placement de la commande

Le correctif MDVA-32776 corrige le problème en raison duquel le statut du stock n’est pas mis à jour lorsqu’une commande est passée mais n’est pas envoyée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 est installé. L’ID du correctif est MDVA-32776. Notez que le problème a été résolu dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut du stock n&#39;est pas mis à jour lorsqu&#39;une commande est passée mais non expédiée.

<u>Conditions préalables</u> :

1. Le module Inventaire est installé.
1. Afficher les produits en rupture de stock est défini sur *Oui*.

   Pour définir, accédez à **Magasins** > **Configuration** > **Catalogue** > **Inventaire** > **Afficher les produits en rupture de stock** = *Yes*.

<u>Procédure à suivre </u> :

1. Créez deux produits simples avec qté = 11 et 22.
1. Créez un produit regroupé à l’aide des produits simples créés à l’étape 1.
1. Ajoutez des produits groupés au panier en définissant l’une des quantités de produit sur 11 et en provoquant une rupture de stock de l’autre produit simple.
1. Effectuez le passage en caisse et passez la commande.

<u>Résultats attendus</u> :

Les produits regroupés affichent des étiquettes `out-of-stock` lorsque les produits simples associés sont en rupture de stock.

<u>Résultats réels</u> :

1. Le produit simple avec qty = 11 est en rupture de stock.
1. Le produit regroupé n’affiche pas de message *en rupture de stock* pour le produit avec une quantité = 11. Cependant, l’ajout de ce produit au panier génère un message d’erreur *rupture de stock*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
