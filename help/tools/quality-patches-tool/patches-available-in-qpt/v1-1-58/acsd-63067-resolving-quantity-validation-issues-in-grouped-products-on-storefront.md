---
title: 'ACSD-63067 : résolution des problèmes de validation de quantité dans les produits groupés sur storefront'
description: Appliquez le correctif ACSD-63067 pour résoudre le problème d’Adobe Commerce en raison duquel toutes les quantités de produits regroupés sont incorrectement mises en évidence comme non valides lorsqu’un seul produit a une quantité incorrecte.
feature: Storefront
role: Admin, Developer
source-git-commit: 7446f4d83932eedc6fa711ad09c6ee559d357f70
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067 : résolution des problèmes de validation de quantité dans les produits groupés sur storefront

Le correctif ACSD-63067 corrige le problème en raison duquel toutes les quantités de produits dans les produits regroupés sont incorrectement mises en évidence comme non valides lorsqu’un seul produit a une quantité incorrecte. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63067. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Dans les produits regroupés, une quantité non valide dans l’un des sous-produits entraîne la mise en surbrillance incorrecte de toutes les quantités comme non valides. De plus, un message de validation s’affiche pour tous les produits au lieu de uniquement pour celui dont la quantité n’est pas valide.

<u>Procédure à suivre </u> :

1. Créez un produit groupé avec au moins deux produits simples comme options.
1. Ouvrez le produit sur le storefront.
1. Entrez une quantité non valide (par exemple : -1) pour l&#39;une des options et une quantité valide (par exemple : 1) pour les autres options.
1. Cliquez sur **[!UICONTROL Add to Cart]**.

<u>Résultats attendus</u> :

Seul le produit avec la quantité non valide est mis en surbrillance comme non valide.

<u>Résultats réels</u> :

Toutes les quantités de produit sont surlignées comme non valides, et le message *Veuillez spécifier la quantité de produit(s). s’affiche pour tous les produits*.


## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
