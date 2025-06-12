---
title: 'ACSD-53118 : les règles de panier avec coupon ne fonctionnent pas correctement'
description: Appliquez le correctif ACSD-53118 pour résoudre le problème d’Adobe Commerce en raison duquel la règle de prix du panier est appliquée à l’aide d’un code de coupon tandis que le produit du panier comporte un attribut de correspondance vide.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 8957790e-c22b-4a25-939b-94d7a9fb1cc7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53118 : les règles de panier avec coupon ne fonctionnent pas correctement

Le correctif ACSD-53118 corrige le problème en raison duquel la règle de prix du panier est appliquée à l’aide d’un code de coupon alors que le produit du panier comporte un attribut de correspondance vide. Ce correctif est disponible lorsque la version 1.1.41 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53118. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La règle de prix du panier est appliquée à l’aide d’un code de coupon tandis que le produit du panier possède un attribut correspondant vide.

<u>Procédure à suivre </u> :

1. Créez un attribut de prix et ajoutez-le au jeu d’attributs. Rendez l’attribut utilisable dans les conditions des règles de promotion.
1. Créez un produit et laissez le nouvel attribut vide.
1. Créez une règle de prix de panier avec un coupon spécifique et la condition suivante :

   * Si un article est TROUVÉ dans le panier avec TOUTES ces conditions vraies : Attribute1 est 0.

1. Ajoutez au panier le produit créé à l’étape 2.
1. Utilisez le code de coupon pour la règle de panier créée à l’étape 3.

<u>Résultats attendus</u> :

La remise n’est pas appliquée au panier.

<u>Résultats réels</u> :

La remise est appliquée au panier.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
