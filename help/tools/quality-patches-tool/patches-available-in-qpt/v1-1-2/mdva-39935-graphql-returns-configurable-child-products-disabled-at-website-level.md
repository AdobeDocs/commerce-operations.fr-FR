---
title: "MDVA-39935 : GraphQL renvoie les produits enfants configurables désactivés au niveau du site web"
description: Le correctif Adobe Commerce MDVA-39935 corrige le problème en raison duquel GraphQL renvoie des produits enfants configurables désactivés au niveau du site web. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-39935. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: c1055ed10813aa6e585f93ec3091d216af06affd
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-39935 : GraphQL renvoie les produits enfants configurables désactivés au niveau du site web.

Le correctif Adobe Commerce MDVA-39935 corrige le problème en raison duquel GraphQL renvoie des produits enfants configurables désactivés au niveau du site web. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-39935. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

GraphQL renvoie les produits enfants configurables même après leur désactivation au niveau du site web.

<u>Étapes à reproduire</u> :

1. Activez l’option d’affichage des produits en rupture de stock sous **Magasin** > **Configuration** > **Catalogue** > **Inventaire** > **Options Stock** > **Produits d’affichage en rupture de stock** > **Oui**.
1. Sélectionnez un **produit configurable** qui comporte plus de deux **produits simples**.
1. Désactivez **Produit simple** et enregistrez le **Produit configurable**.
1. Récupérez les données **Configurable Product** à l’aide de GraphQL.

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u> :

Les produits désactivés ne s’affichent PAS dans les résultats des variantes.

<u>Résultats réels</u> :

Les données des produits désactivés sont récupérées dans les résultats des variantes.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) .
