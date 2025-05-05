---
title: 'MDVA-44940 : erreur SQL lors de l''enregistrement de la catégorie depuis l''administrateur'
description: Le correctif MDVA-44940 corrige le problème d’erreur SQL lors de l’enregistrement d’une catégorie depuis l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID de correctif est MDVA-44940. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Admin Workspace, Categories, Sales Channels
role: Admin
exl-id: de4384f1-a75d-4726-810f-6560a7c57b82
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-44940 : erreur SQL lors de l&#39;enregistrement de la catégorie depuis l&#39;administrateur

Le correctif MDVA-44940 corrige le problème d’erreur SQL lors de l’enregistrement d’une catégorie depuis l’administrateur. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID de correctif est MDVA-44940. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur SQL se produit lors de l’enregistrement d’une catégorie à partir de l’administrateur.

<u>Étapes à reproduire</u> :

1. Installez des exemples de données.
1. Créez un deuxième site web avec un groupe de magasins affecté à la catégorie par défaut.

   * Créez une vue de magasin affectée au nouveau groupe de magasins.

1. Créez un stock et une source supplémentaire affectée à ce stock ainsi qu’un canal de vente affecté au second site web.
1. Créez un produit test affecté au deuxième site web.
1. Accédez à **Admin** > **Catalogue** > **Catégories**, sélectionnez **Portée** = **Second site Web** et accédez à **Produits de la catégorie** > **Tri automatique** > Déplacer les produits en rupture de stock vers le bas, puis cliquez sur **Enregistrer**&rbrace; .

<u>Résultats attendus</u> :

La catégorie est enregistrée.

<u>Résultats réels</u> :

L’erreur suivante se produit : *un problème s’est produit lors de l’enregistrement de la catégorie*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
