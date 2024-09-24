---
title: 'MDVA-38393 : les règles du catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé'
description: Le correctif MDVA-38393 corrige le problème en raison duquel les règles du catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID de correctif est MDVA-38393. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393 : les règles du catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé

Le correctif MDVA-38393 corrige le problème en raison duquel les règles du catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID de correctif est MDVA-38393. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles du catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé.

<u>Étapes à reproduire</u> :

1. Créez un produit configurable avec un produit simple associé.
1. Créez une catégorie.
1. Attribuez uniquement le produit configurable à la nouvelle catégorie.
1. Créer de nouvelles règles de catalogue :
   * Condition = Catégorie contient \&lt;nouvel ID de catégorie>
   * Action = réduction de 50 %
   * Actif = Oui
1. Effectuez la réindexation.
1. Vérifiez le produit paramétrable sur le front-end (la réduction doit être appliquée).
1. Vérifiez la table `catalogrule_product` (le produit simple doit avoir une remise).
1. Accédez à l’administrateur et modifiez le nom du produit simple. Cela ajouterait un enregistrement à la table `catalogrule_product_cl`.
1. Exécutez la commande cron ou `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`.
1. Vérifiez la table `catalogrule_product`.

<u>Résultats attendus</u> :

Le produit configurable offre une remise.

<u>Résultats réels</u> :

* Les enregistrements de remise créés pour les produits simples sont manquants dans la table `catalogrule_product`.
* Le produit configurable sur l’interface a le prix d’origine complet.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
