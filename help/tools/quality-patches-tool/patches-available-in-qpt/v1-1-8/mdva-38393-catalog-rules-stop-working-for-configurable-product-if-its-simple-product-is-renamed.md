---
title: 'MDVA-38393 : les règles de catalogue ne fonctionnent plus pour les produits configurables si leur produit simple est renommé'
description: Le correctif MDVA-38393 corrige le problème où les règles de catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 est installé. L’ID du correctif est MDVA-38393. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393 : les règles de catalogue ne fonctionnent plus pour les produits configurables si leur produit simple est renommé

Le correctif MDVA-38393 corrige le problème où les règles de catalogue cessent de fonctionner pour un produit configurable si son produit simple est renommé. Ce correctif est disponible lors de l’installation de l’outil [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) version 1.1.8. L’ID du correctif est MDVA-38393. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les règles de catalogue ne fonctionnent plus pour un produit configurable si son produit simple est renommé.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec un produit simple associé.
1. Créez une catégorie.
1. Affectez uniquement le produit configurable à la nouvelle catégorie.
1. Créez des règles de catalogue :
   * Condition = la catégorie contient \&lt;nouvel ID de catégorie>
   * Action = 50 % de remise
   * Actif = Oui
1. Effectuez la réindexation.
1. Vérifiez le produit configurable sur le serveur frontal (la remise doit être appliquée).
1. Vérifiez le tableau des `catalogrule_product` (le produit simple doit bénéficier d’une remise).
1. Accédez à Admin et modifiez le nom du produit simple. Cela ajouterait un enregistrement à la table `catalogrule_product_cl`.
1. Exécutez la commande cron ou `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`.
1. Vérifiez le tableau `catalogrule_product`.

<u>Résultats attendus</u> :

Le produit configurable bénéficie d’une remise.

<u>Résultats réels</u> :

* Les enregistrements de remise créés pour les produits simples sont manquants dans le tableau `catalogrule_product`.
* Le produit configurable sur le serveur frontal a le prix d’origine complet.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
