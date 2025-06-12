---
title: 'ACSD-50849 : l’ajout d’un nouveau produit après l’effacement du cache entraîne des incohérences'
description: Appliquez le correctif ACSD-50849 pour résoudre le problème d’Adobe Commerce où l’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraîne une incohérence des positions et des sélections des produits existants.
feature: Cache, Categories, Products
role: Admin
exl-id: e7fd0614-eaa3-48ad-95ff-87f7ad3d76c1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-50849 : l’ajout d’un nouveau produit après l’effacement du cache entraîne des incohérences

Le correctif ACSD-50849 corrige le problème en raison duquel l’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraîne une incohérence des positions et des sélections des produits existants. Ce correctif est disponible lorsque le [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) QPT 1.1.32 est installé. L’ID du correctif est ACSD-50849. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un nouveau produit à la catégorie après l’effacement du cache entraîne une incohérence des positions et des sélections des produits existants.

<u>Procédure à suivre </u> :

1. Créez deux produits.
1. Attribuez un produit à une catégorie.
1. Ouvrez la catégorie à partir de l’administrateur.
1. Nettoyez le cache `bin/magento cache:flush`.
1. Ajoutez le deuxième produit à la catégorie .

<u>Résultats attendus</u> :

Les produits existants affectés à la catégorie ne sont pas supprimés automatiquement.

<u>Résultats réels</u> :

Le premier produit (existant) est automatiquement supprimé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
