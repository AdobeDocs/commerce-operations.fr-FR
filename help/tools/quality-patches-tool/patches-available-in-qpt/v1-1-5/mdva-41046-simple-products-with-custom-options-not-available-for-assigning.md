---
title: 'MDVA-41046 : produits simples avec options personnalisées non disponibles pour l’affectation'
description: Le correctif MDVA-41046 résout le problème où des produits simples avec des options personnalisées ne sont pas disponibles pour l’affectation à des produits configurables/regroupés. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41046. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046 : produits simples avec options personnalisées non disponibles pour l’affectation

Le correctif MDVA-41046 résout le problème où des produits simples avec des options personnalisées ne sont pas disponibles pour l’affectation à des produits configurables/regroupés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-41046. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits simples avec des options personnalisées ne sont pas disponibles pour l’affectation à des produits configurables/groupés.

<u>Procédure à suivre </u> :

1. Créez un produit simple avec des options personnalisables et définissez une valeur pour l’attribut configurable.
   * Utilisez *Couleur* comme attribut configurable, puis sélectionnez *Jaune* comme valeur de couleur.
1. Enregistrez le produit simple.
1. Accédez maintenant à la page Créer un produit configurable .
1. Parcourez l’assistant « Créer une configuration » et veillez à sélectionner *Jaune* comme couleur d’attribut.
1. Sans enregistrer le produit configurable, sélectionnez l’option « Choisir un autre produit » dans la liste déroulante Sélectionner .
1. Cela ouvre une grille de produits filtrée par l’attribut de couleur jaune. Sélectionnez maintenant le produit simple qui a été créé précédemment avec des options personnalisables.
1. Enregistrer le produit configurable.

<u>Résultats attendus</u> :

Le produit simple avec des options personnalisées est disponible pour l’affectation (visible dans la grille) à l’étape 6.

<u>Résultats réels</u> :

La section Configuration est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
