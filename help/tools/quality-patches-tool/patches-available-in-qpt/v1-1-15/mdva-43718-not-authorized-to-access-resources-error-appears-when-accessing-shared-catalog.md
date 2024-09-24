---
title: '"MDVA-43718 : l''erreur "le consommateur n''est pas autorisé à accéder aux ressources" s''affiche lors de l''accès au catalogue partagé"'
description: Le correctif MDVA-43718 résout le problème où l’erreur *consumer n’est pas autorisé à accéder à %resources.* apparaît lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID de correctif est MDVA-43718. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-43718 : l&#39;erreur &quot;le consommateur n&#39;est pas autorisé à accéder aux ressources&quot; s&#39;affiche lors de l&#39;accès au catalogue partagé

Le correctif MDVA-43718 résout le problème où l’erreur *consumer n’est pas autorisée à accéder à %resources.* s’affiche lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID de correctif est MDVA-43718. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur suivante s’affiche lors de l’accès à un catalogue partagé à partir d’une intégration personnalisée : *Le consommateur n’est pas autorisé à accéder à %resources*.

<u>Étapes à reproduire</u> :

1. Créez une nouvelle intégration à partir de Admin > **Système** > **Intégration** > **Ajouter une intégration**.
1. Ajoutez l&#39;accès aux ressources suivantes et activez l&#39;intégration :

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::manage
   * Magento_Catalog::catalog

1. Utilisation de l’accès à l’intégration : `rest/default/V1/sharedCatalog/1`

<u>Résultats attendus</u> :

Les détails du catalogue partagé sont renvoyés.

<u>Résultats réels</u> :

L’erreur suivante est renvoyée :

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
