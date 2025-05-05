---
title: "ACSD-45241 : mal calculé la quantité en stock d'un produit virtuel"
description: Le correctif ACSD-45241 corrige le problème en raison duquel la quantité de stock du produit virtuel est mal calculée après la création d’un avoir de crédit. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID de correctif est ACSD-45241. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.4.
feature: Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241 : erreur de calcul de la quantité en stock d’un produit virtuel

Le correctif ACSD-45241 corrige le problème en raison duquel la quantité de stock du produit virtuel est mal calculée après la création d’un avoir de crédit. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID de correctif est ACSD-45241. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité d’actions d’un produit virtuel est mal calculée après la création d’une note de crédit.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec un produit virtuel en tant que produit enfant dans l’administrateur Commerce.
1. Assurez-vous que les deux produits créés à l’étape 1 sont en stock.
1. Marquez la quantité pour le produit virtuel créé à l’étape 1 comme 100 et conservez également la quantité vendable 100.
1. Ajoutez le produit au panier.
1. passer une commande avec le produit virtuel créé à l’étape 1.
1. Conservez l’état de la commande comme &quot;En attente&quot;. Pas besoin de traiter le paiement.
1. `order_created` enregistrement créé dans `inventory_reservation`. La quantité de produit virtuelle affiche 100 avec une quantité vendable de 99.
1. Ouvrez la commande et accédez à **Facture** > **Submit Invoice**.
1. `invoice_created` enregistrement créé dans `inventory_reservation`. La quantité virtuelle du produit est maintenant de 99, et la quantité vendable aussi est de 99.
1. Créez une note de crédit sans sélectionner **Revenir à Stock**.

<u>Résultats attendus</u> :

Aucun nouvel enregistrement n’est créé dans `inventory_reservation` et la quantité en stock du produit virtuel reste inchangée.

<u>Résultats réels</u> :

Un enregistrement `creditmemo_created` est créé dans `inventory_reservation`, et la quantité de stock de produit virtuel est ajustée à 98 avec une quantité vendable à 99.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
