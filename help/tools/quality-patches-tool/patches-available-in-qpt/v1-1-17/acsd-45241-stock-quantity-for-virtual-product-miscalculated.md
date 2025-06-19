---
title: 'ACSD-45241 : erreur de calcul de la quantité de stock du produit virtuel'
description: Le correctif ACSD-45241 corrige le problème où la quantité de stock du produit virtuel est mal calculée après la création d'un avoir. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-45241. Notez que le problème a été résolu dans Adobe Commerce 2.4.4.
feature: Orders, Products
role: Admin
exl-id: 447a84f0-aab4-4bb1-9f06-c056c006cd69
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241 : erreur de calcul de la quantité de stock du produit virtuel

Le correctif ACSD-45241 corrige le problème où la quantité de stock du produit virtuel est mal calculée après la création d&#39;un avoir. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID du correctif est ACSD-45241. Notez que le problème a été résolu dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité de stock d&#39;un produit virtuel est mal calculée après la création d&#39;un avoir.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec un produit virtuel en tant que produit enfant dans Commerce Admin.
1. Assurez-vous que les deux produits créés à l’étape 1 sont en stock.
1. Marquez la quantité du produit virtuel créé à l&#39;étape 1 sur 100 et conservez également la quantité vendable sur 100.
1. Ajoutez le produit au panier.
1. Commandez le produit virtuel créé à l&#39;étape 1.
1. Conserver le statut de la commande comme « En attente ». Pas besoin de traiter le paiement.
1. Enregistrement `order_created` créé en `inventory_reservation`. La quantité de produit virtuel affiche 100 avec une quantité vendable égale à 99.
1. Ouvrez la commande et accédez à **Facture** > **Soumettre la facture**.
1. Enregistrement `invoice_created` créé en `inventory_reservation`. La quantité de produit virtuel est maintenant de 99 et la quantité vendable est également de 99.
1. Créez un avoir sans sélectionner **Retour aux stocks**.

<u>Résultats attendus</u> :

Aucun nouvel enregistrement n&#39;est créé dans `inventory_reservation` et la quantité de stock du produit virtuel reste inchangée.

<u>Résultats réels</u> :

Un enregistrement `creditmemo_created` est créé dans `inventory_reservation` et la quantité de stock de produits virtuels est ajustée à 98 avec la quantité vendable à 99.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
