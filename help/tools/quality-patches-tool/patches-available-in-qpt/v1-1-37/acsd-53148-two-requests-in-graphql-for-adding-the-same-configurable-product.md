---
title: 'ACSD-53148 : deux demandes parallèles dans GraphQL pour l’ajout du même produit configurable'
description: Appliquez le correctif ACSD-53148 pour résoudre le problème d’Adobe Commerce où deux demandes parallèles dans GraphQL pour l’ajout d’un même produit configurable au panier entraînaient deux éléments distincts du panier avec le même SKU de produit.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: e5e22bed-69de-4872-9aa8-ab228f640b30
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53148 : deux demandes parallèles dans GraphQL pour l’ajout du même produit configurable

Le correctif ACSD-53148 corrige le problème en raison duquel deux demandes parallèles dans GraphQL pour l’ajout d’un même produit configurable au panier entraînaient deux articles distincts dans le panier avec le même SKU de produit. Ce correctif est disponible lorsque la version 1.1.37 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-53148. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Deux requêtes parallèles dans GraphQL pour ajouter le même produit configurable au panier entraînaient deux articles distincts dans le panier avec le même SKU de produit.

<u>Procédure à suivre </u> :

1. Créez un produit configurable avec le SKU *Test* et un produit simple avec le SKU *Test-A*.
1. Création d’un panier vide via GraphQL (modifiez l’emplacement avec votre propre [!DNL URL]) :

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"mutation{\n createEmptyCart\n}","variables"{}}'
   ```

1. Exécutez deux requêtes simultanées pour ajouter le même produit au panier (modifiez l’*cartID* et l’emplacement des deux requêtes) :

   ```GraphQL
       curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}' & curl --location 'http://mag.local/graphql' --header 'Store: default' --header 'Content-Type: application/json' --data '{"query":"mutation($cartId: String!, $preSku: String!, $preParentSku: String!) {\r\n addConfigurableProductsToCart(\r\n input: {\r\n cart_id: $cartId\r\n cart_items: [\r\n {\r\n parent_sku: $preParentSku\r\n data: {\r\n quantity: 1\r\n sku: $preSku\r\n }\r\n }\r\n ]\r\n }\r\n ) {\r\n cart {\r\n items {\r\n id\r\n product {\r\n name\r\n sku\r\n }\r\n quantity\r\n \r\n prices {\r\n price {\r\n value\r\n currency\r\n }\r\n }\r\n ... on ConfigurableCartItem {\r\n configurable_options {\r\n option_label\r\n value_label\r\n }\r\n }\r\n }\r\n total_quantity\r\n prices {\r\n grand_total {\r\n value\r\n currency\r\n }\r\n discounts {\r\n amount {\r\n value\r\n currency\r\n }\r\n label\r\n }\r\n subtotal_excluding_tax {\r\n value\r\n currency\r\n }\r\n } \r\n }\r\n }\r\n}","variables":{"cartId":"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf","preParentSku":"Test","preSku":"Test-A"}}'
   ```

1. Accédez au panier pour afficher les articles (modifiez l’*cartId* et l’emplacement) :

   ```GraphQL
   curl --location 'http://mag.local/graphql' \
   --header 'Store: default' \
   --header 'Content-Type: application/json' \
   --data '{"query":"{\n cart(cart_id: \"VV85vRfmCrRm0aKLKkNDrXH2S5y7sSpf\") {\n items {\n id\n product {\n name\n sku\n }\n quantity\n }\n\n }\n}\n","variables":{}}'
   ```

<u>Résultats attendus</u> :

Objet mis en vente une seule fois avec [!UICONTROL qty] = 2.

```GraphQL
    {"data":{"cart":{"items":[{"id":"5","product":{"name":"config1","sku":"config1"},"quantity":2}]}}}%
```

<u>Résultats réels</u> :

Objet mis en vente deux fois avec [!UICONTROL qty] = 1.

```GraphQL
    {"data":{"cart":{"items":[{"id":"1","product":
    {"name":"config1","sku":"config1"},"quantity":1},
    {"id":"3","product":{"name":"config1","sku":"config1"},"quantity":1}]}}}%
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
