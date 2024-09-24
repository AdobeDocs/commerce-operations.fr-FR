---
title: "MDVA-39923 : la recherche par SKU dans la fonctionnalité d’ordre rapide B2B est sensible à la casse"
description: Le correctif MDVA-39923 corrige le problème en raison duquel les clients recevaient une erreur lorsqu’ils recherchaient la commande par SKU dans la fonctionnalité d’ordre rapide B2B avec une casse différente de celle avec laquelle le nom était enregistré. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-39923. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923 : la recherche par SKU dans la fonctionnalité d’ordre rapide B2B est sensible à la casse.

Le correctif MDVA-39923 corrige le problème en raison duquel les clients recevaient une erreur lorsqu’ils recherchaient la commande par SKU dans la fonctionnalité d’ordre rapide B2B avec une casse différente de celle avec laquelle le nom était enregistré. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-39923. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La recherche par SKU dans la fonctionnalité d’ordre rapide B2B est sensible à la casse et affiche une erreur lorsqu’un autre cas est utilisé que celui avec lequel le SKU est enregistré.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur et accédez à **Magasins** > **Configuration** > **B2B**.
1. Activez **Catalogue partagé** et **Ordre rapide**.
1. Créez un produit avec un SKU majuscule, par exemple, TEST20-1234.
1. Attribuez le produit créé au **catalogue partagé**.
1. Connectez-vous en tant que client et cliquez sur **Commande rapide**.
1. Saisissez le SKU en minuscules, par exemple, test20-1234.

<u>Résultats attendus</u> :

Le produit doit être trouvé, quel que soit le cas utilisé.

<u>Résultats réels</u> :

Le message d&#39;erreur suivant est reçu : *1 produit(s) nécessite(s) votre attention*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
