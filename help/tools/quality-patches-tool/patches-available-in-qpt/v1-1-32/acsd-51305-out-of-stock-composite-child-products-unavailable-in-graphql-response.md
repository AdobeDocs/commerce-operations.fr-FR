---
title: 'ACSD-51305 : produits enfants composites en rupture de stock non disponibles dans la réponse GraphQL'
description: Appliquez le correctif ACSD-51305 pour résoudre le problème d’Adobe Commerce où les produits enfants composites en rupture de stock ne sont pas disponibles dans la réponse de GraphQL.
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51305 : produits enfants composites en rupture de stock non disponibles dans la réponse GraphQL

Le correctif ACSD-51305 corrige le problème en raison duquel les produits enfants composites en rupture de stock ne sont pas disponibles dans la réponse de GraphQL. Ce correctif est disponible lorsque la version 1.1.32 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51305. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits enfants composites en rupture de stock ne sont pas disponibles dans la réponse de GraphQL.

<u>Procédure à suivre </u> :

1. Connectez-vous au site Web de l’administrateur.
1. Créez une catégorie (cat1, id=3).
1. Créez un produit *simple1* (en rupture de stock, non visible individuellement, affecté à *cat1*).
1. Créez un produit *simple2* (en stock, non visible individuellement, affecté à *cat1*).
1. Créez un produit *bundle1* avec des produits enfants *simple1* et *simple2* en tant que produits à bouton radio *option1* et affectez-le à la catégorie *cat1*.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Définissez **[!UICONTROL Display Out of Stock Products]** sur *Oui*.

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

La section **[!UICONTROL Product]** à l’intérieur du bloc de **[!UICONTROL Options]** n’est pas vide.

<u>Résultats réels</u> :

La section **[!UICONTROL Product]** à l’intérieur du bloc de **[!UICONTROL Options]** est vide.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
