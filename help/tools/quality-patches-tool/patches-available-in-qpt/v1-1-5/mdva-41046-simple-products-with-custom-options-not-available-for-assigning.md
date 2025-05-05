---
title: "MDVA-41046 : produits simples avec des options personnalisées non disponibles pour l’attribution"
description: Le correctif MDVA-41046 résout le problème en raison duquel des produits simples avec des options personnalisées ne sont pas disponibles pour l’attribution à un produit configurable/groupé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID de correctif est MDVA-41046. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Products
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046 : produits simples avec des options personnalisées non disponibles pour l’attribution

Le correctif MDVA-41046 résout le problème en raison duquel des produits simples avec des options personnalisées ne sont pas disponibles pour l’attribution à un produit configurable/groupé. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID de correctif est MDVA-41046. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits simples avec des options personnalisées ne sont pas disponibles pour l’affectation à un produit configurable/groupé.

<u>Étapes à reproduire</u> :

1. Créez un produit simple avec des options personnalisables et définissez une valeur pour l’attribut configurable.
   * Utilisez *Color* comme attribut configurable et sélectionnez *Yellow* comme valeur de couleur.
1. Enregistrez le produit simple.
1. Accédez maintenant à la page Créer un produit configurable .
1. Accédez à l’assistant &quot;Créer une configuration&quot; et veillez à sélectionner *Jaune* comme couleur d’attribut.
1. Sans enregistrer le produit configurable, sélectionnez l’option &quot;Choisir un autre produit&quot; dans la liste déroulante Sélectionner .
1. Cela ouvre une grille de produit filtrée en jaune par attribut de couleur. Sélectionnez maintenant le produit simple créé précédemment avec des options personnalisables.
1. Enregistrez le produit configurable.

<u>Résultats attendus</u> :

Le produit simple avec des options personnalisées est disponible pour l’attribution (visible dans la grille) à l’étape 6.

<u>Résultats réels</u> :

La section Configuration est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
