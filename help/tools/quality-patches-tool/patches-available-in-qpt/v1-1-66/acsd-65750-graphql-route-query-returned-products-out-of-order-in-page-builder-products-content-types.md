---
title: 'La requête ACSD-65750: [!DNL GraphQL] « route » renvoie des produits dans le désordre dans le type  [!DNL Page Builder]  contenu Products'
description: Appliquez le correctif ACSD-65750 pour résoudre le problème d’Adobe Commerce où la requête « itinéraire » de GraphQL renvoie des produits dans le désordre du type  [!DNL Page Builder]  contenu Products.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2555327c02985a51e7f34a36dd256227b12b5924
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-65750 : [!DNL GraphQL] requête « itinéraire » renvoie des produits dans le désordre dans [!DNL Page Builder] type de contenu Produits

Le correctif ACSD-65750 corrige le problème où la requête « route » [!DNL GraphQL] renvoie des produits dans le désordre dans [!DNL Page Builder] type de contenu Produits . Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65750. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête « route » [!DNL GraphQL] ne renvoie pas les produits dans l’ordre de tri correct lors de l’utilisation du type de contenu Produits [!DNL Page Builder] .

<u>Procédure à suivre </u> :

1. Créez une nouvelle catégorie et certains produits dans le catalogue, puis liez les produits à cette catégorie.
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**, modifiez la catégorie créée, puis ouvrez l’onglet **[!UICONTROL Products in Category]** .
1. Définissez des **[!UICONTROL Position]** personnalisées pour chaque produit de cette catégorie.
1. Enregistrez la catégorie et exécutez la réindexation.
1. Accédez à **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** et cliquez sur **[!UICONTROL Add New Page]**.
1. Développez l&#39;onglet **[!UICONTROL Content]** , puis cliquez sur **[!UICONTROL Edit with Page Builder]**.
1. Faites glisser un élément **[!UICONTROL Row]** dans la zone de contenu, puis faites glisser un élément **[!UICONTROL Products]** à l’intérieur de la ligne.
1. Configurez l&#39;élément Products comme suit :
   * **[!UICONTROL Select Products By]** : *Catégorie*
   * **[!UICONTROL Category]** : *sélectionnez la catégorie nouvellement créée*
   * **[!UICONTROL Sort By]** : *Position*
1. Passez à l’onglet **[!UICONTROL Search Engine Optimization]** et définissez la **[!UICONTROL URL Key]** sur *test-widget*.
1. Enregistrez la page.
1. Effectuez la requête [!DNL GraphQL] suivante :

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>Résultats attendus</u> :

Le système renvoie les produits dans l’ordre défini par leur position dans la catégorie.

<u>Résultats réels</u> :

Le système renvoie des produits dans un ordre qui ne correspond pas à leur position de catégorie dans la réponse GraphQL.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
