---
title: 'ACSD-46519 : [!UICONTROL product_count] dans [!UICONTROL categoryList] [!DNL GraphQL] la requête renvoie 0 pour les catégories d’ancrage'
description: Appliquez le correctif ACSD-46519 pour résoudre le problème d’Adobe Commerce où, lorsque vous utilisez la méthode [!UICONTROL categoryList] [!DNL GraphQL]  pour obtenir des catégories enfants, la [!UICONTROL product_count] est 0 pour les catégories parents.
feature: Categories, GraphQL, Products
role: Admin
exl-id: 7becaa4e-421a-4983-ac73-f5b58fc45d8f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46519 : [!UICONTROL product_count] dans [!UICONTROL categoryList] requête [!DNL GraphQL] renvoie 0 pour les catégories d’ancrage

Le correctif ACSD-46519 résout le problème où la [!UICONTROL product_count] dans [!UICONTROL categoryList] requête [!DNL GraphQL] renvoie 0 pour les catégories d’ancrage. Ce correctif est disponible lorsque la version 1.1.23 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-46519. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque la méthode [!UICONTROL categoryList] [!DNL GraphQL] est utilisée pour obtenir des catégories enfants, elle affiche la [!UICONTROL product_count] 0 pour les catégories parents.

<u>Procédure à suivre </u> :

1. Utilisez la requête [!DNL GraphQL] suivante pour obtenir la hiérarchie de catégories avec [!UICONTROL product_count] :

<pre><code>
&lbrace;
  categoryList(filters: { ids: { eq: "2" } }) &lbrace;
    id
    name
    product_count
    level
    children &lbrace;
      name
      product_count
      level
      children &lbrace;
        name
        product_count
        level
        children &lbrace;
          name
          product_count
          level
          children &lbrace;
            name
            product_count
            level
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code></pre>

<u>Résultats attendus</u> :

Si la catégorie parent est une catégorie ancrée, la [!UICONTROL product_count] doit afficher la somme des nombres de produits de la catégorie enfant à chaque niveau.

<u>Résultats réels</u> :

Si la catégorie parent est une catégorie ancrée, les produits s’affichent avec la valeur 0 pour le niveau de catégorie 2 et les niveaux inférieurs.

<pre><code>
&lbrace;
    "data": &lbrace;
        "categoryList": &lbrack;
            &lbrace;
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": &lbrack;
                    &lbrace;
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    &rbrace;,
                    &lbrace;
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": &lbrack;
                            &lbrace;
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;,
                            &lbrace;
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;
                        &rbrack;
                    &rbrace;,
                    ...
                &rbrack;
            &rbrace;
        &rbrack;
    &rbrace;
&rbrace;
</code></pre>

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
