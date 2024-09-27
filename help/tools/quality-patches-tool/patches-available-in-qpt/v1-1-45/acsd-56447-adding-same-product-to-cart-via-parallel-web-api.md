---
title: "ACSD-56447 : l’ajout d’un même produit au panier via l’API REST web parallèle entraîne l’insertion de deux éléments distincts dans le panier"
description: Appliquez le correctif ACSD-56447 pour résoudre le problème Adobe Commerce en raison duquel l’ajout du même produit au panier via des demandes d’API REST web parallèles entraîne deux éléments distincts dans le panier.
feature: Shopping Cart, REST
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56447 : l’ajout d’un même produit au panier via l’API REST web parallèle entraîne l’apparition de deux éléments distincts dans le panier.

Le correctif ACSD-56447 corrige le problème en raison duquel l’ajout du même produit au panier via des demandes d’API REST web parallèles entraîne deux éléments distincts dans le panier. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 est installé. L’ID de correctif est ACSD-56447. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ajout d’un même produit au panier via des demandes d’API REST web parallèles entraîne l’insertion de deux éléments distincts dans le panier.

<u>Étapes à reproduire</u> :

1. Générez un jeton client pour effectuer la demande d’appels d’API REST à l’aide de [!DNL Postman].
1. Créez un panier pour le client.
1. Utilisez le jeton généré ci-dessus pour créer un panier vide pour le client.
1. Utilisez CURL pour effectuer deux requêtes `AddProductsToCart` exécutées en parallèle. Suivez les instructions du [tutoriel sur le traitement des commandes](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) de la documentation destinée aux développeurs.

<u>Résultats attendus</u> :

Les articles avec plusieurs quantités sont affichés sur une seule ligne.

<u>Résultats réels</u> :

Les mêmes SKU s’affichent sur plusieurs lignes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
