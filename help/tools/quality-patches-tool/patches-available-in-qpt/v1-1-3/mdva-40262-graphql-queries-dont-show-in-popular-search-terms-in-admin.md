---
title: 'MDVA-40262 : les requêtes GraphQL ne s’affichent pas dans les termes de recherche populaires dans admin'
description: Le correctif de qualité Adobe Commerce MDVA-40262 corrige le problème où les requêtes de recherche GraphQL ne sont pas affichées dans les termes de recherche populaires dans l’administration. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-40262. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Admin Workspace, GraphQL, Search
role: Admin
exl-id: 9442ac86-e632-4ab3-8cb3-d29487a1ecbe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-40262 : les requêtes GraphQL ne s’affichent pas dans les termes de recherche populaires dans admin

Le correctif de qualité Adobe Commerce MDVA-40262 corrige le problème où les requêtes de recherche GraphQL ne sont pas affichées dans les termes de recherche populaires dans l’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 est installé. L’ID du correctif est MDVA-40262. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les requêtes GraphQL ne sont pas affichées dans les termes de recherche populaires dans l’administration.

<u>Conditions préalables</u> :

Les exemples de données doivent être installés.

<u>Procédure à suivre </u> :

1. Accédez à **Magasins** > **Configuration** > **Catalogue** > **SEO** > **Termes de recherche populaires** et définissez sur activer.
1. Exécutez la requête GraphQL suivante :

<pre>
<code class="language-graphql">
&lbrace;
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) &lbrace;
    total_count
    items &lbrace;
      name
      sku
    &rbrace;
    page_info &lbrace;
      page_size
      current_page
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Après avoir exécuté la requête GraphQL pour rechercher un produit, la requête doit être ajoutée aux termes de recherche populaires.

<u>Résultats réels</u> :

La requête de recherche n’est pas ajoutée aux termes de recherche populaires.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur les correctifs de qualité pour Adobe Commerce, consultez :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
