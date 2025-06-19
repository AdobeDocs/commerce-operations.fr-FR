---
title: 'ACSD-51683 : impossible d’ajouter l’option personnalisable au panier à l’aide de GraphQL'
description: Appliquez le correctif ACSD-51683 pour résoudre le problème d’Adobe Commerce en raison duquel l’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL.
feature: GraphQL
role: Admin
exl-id: 9cdf71aa-3dea-4f8c-b4d6-d6f192a9710d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51683 : impossible d’ajouter l’option personnalisable au panier à l’aide de GraphQL

Le correctif ACSD-51683 corrige le problème en raison duquel l’option personnalisable ne peut pas être ajoutée au panier à l’aide de GraphQL. Ce correctif est disponible lorsque la version 1.1.35 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51683. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible d’ajouter l’option personnalisable au panier à l’aide de GraphQL.

<u>Procédure à suivre </u> :

1. Créez un produit simple avec une option **champ de texte** personnalisable.
1. [Ajouter au panier](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/) le produit créé avec l’option personnalisable requise via GraphQL.
1. Envoyez la requête [panier](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/queries/cart/) GraphQL pour vérifier le produit et ses détails dans le panier.

<u>Résultats attendus</u>

La section `Customizable_options` de la réponse de GraphQL contient les données fournies lors de l’ajout du produit au panier.

<u>Résultats réels</u>

La section `Customizable_options` de la réponse GraphQL est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
