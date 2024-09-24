---
title: "ACSD-45849 : les métadonnées vidéo sont perdues après la mise à jour de l’évaluation"
description: Le correctif ACSD-45849 corrige le problème de perte des métadonnées vidéo après l’application d’une mise à jour intermédiaire. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 est installé. L’ID de correctif est ACSD-45849. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.4.
feature: Staging, Page Content
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-45849 : Les métadonnées vidéo sont perdues après la mise à jour de l’évaluation

Le correctif ACSD-45849 corrige le problème de perte des métadonnées vidéo après l’application d’une mise à jour intermédiaire. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.18 est installé. L’ID de correctif est ACSD-45849. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les métadonnées vidéo sont perdues après l’application d’une mise à jour intermédiaire.

<u>Étapes à reproduire</u> :

1. Configurez la clé API YouTube dans **Admin** > **Magasins** > **Configuration** > **Catalogue** > **Vidéo produit**.
1. Créez un produit avec une vidéo YouTube. Notez que l’URL, le titre et la description sont remplis.
1. Créez une mise à jour planifiée du produit avec les paramètres sans modifier la section *Images et vidéo*.
1. Cliquez sur **Afficher/Modifier** dans Modifications planifiées.
1. Accédez à **Images et vidéos** et cliquez sur la vidéo.

<u>Résultats attendus</u> :

L’URL, le titre et la description contiennent les données appropriées.

<u>Résultats réels</u> :

Les champs URL, titre et description sont vides.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
