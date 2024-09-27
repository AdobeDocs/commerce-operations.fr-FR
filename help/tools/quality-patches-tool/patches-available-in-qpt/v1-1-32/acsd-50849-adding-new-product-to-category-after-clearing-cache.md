---
title: "ACSD-50849 : l’ajout d’un nouveau produit après l’effacement du cache entraîne une incohérence"
description: Appliquez le correctif ACSD-50849 pour résoudre le problème Adobe Commerce en raison duquel l’ajout d’un nouveau produit à la catégorie après avoir effacé le cache entraîne une incohérence des positions et des sélections des produits existants.
feature: Cache, Categories, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-50849 : l’ajout d’un nouveau produit après l’effacement du cache entraîne une incohérence.

Le correctif ACSD-50849 corrige le problème en raison duquel l’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraînait une incompatibilité des positions et des sélections des produits existants. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) QPT 1.1.32 est installé. L’ID de correctif est ACSD-50849. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraîne une incohérence des positions et des sélections des produits existants.

<u>Étapes à reproduire</u> :

1. Créez deux produits.
1. Attribuez un produit à une catégorie.
1. Ouvrez la catégorie depuis l’administrateur.
1. Nettoyez le cache `bin/magento cache:flush`.
1. Ajoutez le deuxième produit à la catégorie.

<u>Résultats attendus</u> :

Les produits existants affectés dans la catégorie ne sont pas supprimés automatiquement.

<u>Résultats réels</u> :

Le premier produit (existant) est automatiquement supprimé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
