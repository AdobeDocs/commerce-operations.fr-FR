---
title: 'MDVA-40134 : GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé'
description: Le correctif MDVA-40134 corrige le problème en raison duquel GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-40134. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134 : GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé

Le correctif MDVA-40134 corrige le problème en raison duquel GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-40134. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL ne renvoie pas les produits associés lorsque le catalogue partagé est activé.

<u>Conditions préalables</u> :

Les modules B2B doivent être installés.
L’instance doit être propre avec uniquement les données d’exemple.

<u>Procédure à suivre </u> :

1. Accédez à **Magasins** > **Configuration** > **Général** > **Fonctionnalités B2B** et activez **Catalogue d’entreprise et partagé**.
1. Accédez à **Catalogue** > **Catalogue partagé** et ajoutez tous les produits au **Catalogue général**.
1. Utilisez les données d’exemple et modifiez le sac de voyage Joust (SKU 24-MB01).
1. Sous **Produits connexes**, ajouter les deux sacs Duffle (ID 7 et 13).
1. Envoyez une requête **Post** :

<pre>&lbrace;
  products(filter : {sku : {eq : « 24-MB01 »}}, sort : {name : ASC}) &lbrace;
    items &lbrace;
      related_products &lbrace;
        uid
        nom
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Résultats attendus</u> :

Les produits associés sont affichés dans la réponse de GraphQL.

<u>Résultats réels</u> :

L’erreur suivante s’affiche pour les utilisateurs :

<pre>La valeur renvoyée par Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() doit être du type int, la valeur renvoyée par null &lbrace;« exception »:« [object] (GraphQL\\Error\\Error(code : 0) : la valeur renvoyée par Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() doit être du type int, la valeur renvoyée par null </pre>

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
