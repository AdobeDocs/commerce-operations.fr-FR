---
title: "ACSD-51305 : produits enfants composites en rupture de stock indisponibles dans la réponse GraphQL"
description: Appliquez le correctif ACSD-51305 pour résoudre le problème Adobe Commerce en raison duquel les produits enfants composites en rupture de stock ne sont pas disponibles dans la réponse GraphQL.
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51305 : produits enfants composites en rupture de stock indisponibles dans la réponse GraphQL

Le correctif ACSD-51305 corrige le problème en raison duquel les produits enfants composites en rupture de stock ne sont pas disponibles dans la réponse GraphQL. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 est installé. L’ID de correctif est ACSD-51305. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits enfants composites en rupture de stock ne sont pas disponibles dans la réponse GraphQL.

<u>Étapes à reproduire</u> :

1. Connectez-vous au site Web d’administration.
1. Créez une catégorie (cat1, id=3).
1. Créez un produit *simple1* (en rupture de stock, non visible individuellement, affecté à *cat1*).
1. Créez un produit *simple2* (en stock, non visible individuellement, affecté à *cat1*).
1. Créez un produit *bundle1* avec les produits *simple1* et *simple2* enfants en tant que produits bouton radio *option1* et affectez-le à la catégorie *cat1*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Définissez **[!UICONTROL Display Out of Stock Products]** sur *Yes*.

1. Ouvrez le produit *bundle1* sur le storefront et assurez-vous que les produits enfants *simple1* et *simple2* y sont affichés.
1. Exécutez la requête GraphQL suivante :

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Résultats attendus</u> :

La section **[!UICONTROL Product]** du bloc **[!UICONTROL Options]** n&#39;est pas vide.

<u>Résultats réels</u> :

La section **[!UICONTROL Product]** du bloc **[!UICONTROL Options]** est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
