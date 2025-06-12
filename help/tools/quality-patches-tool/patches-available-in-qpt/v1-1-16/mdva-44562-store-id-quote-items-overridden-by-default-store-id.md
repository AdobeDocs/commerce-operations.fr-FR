---
title: 'MDVA-44562 : ID de magasin pour les articles de devis remplacé par l’ID de magasin par défaut'
description: Le correctif MDVA-44562 corrige le problème en raison duquel l’ID de magasin par défaut remplace l’ID de magasin pour les éléments de devis pour les requêtes GraphQL. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID du correctif est MDVA-44562. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562 : ID de magasin pour les articles de devis remplacé par l’ID de magasin par défaut

Le correctif MDVA-44562 corrige le problème en raison duquel l’ID de magasin par défaut remplace l’ID de magasin pour les éléments de devis pour les requêtes GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID du correctif est MDVA-44562. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ID de magasin pour les articles de devis est remplacé par l’ID de magasin par défaut pour les requêtes GraphQL.

<u>Procédure à suivre </u> :

1. Créez une vue de magasin.
1. Créez un produit simple avec des noms différents par vue de magasin.
1. Créez un nouveau client.
1. Obtenez le jeton d’autorisation du client.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Créez un devis pour le client à l’aide du jeton d’autorisation.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Ajoutez un produit au panier.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Obtenez le contenu du panier pour l’affichage du magasin par défaut.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Obtenez le contenu du panier pour la nouvelle vue de magasin.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Résultats attendus</u> :

La réponse de la nouvelle vue de magasin affiche le nom du produit de la nouvelle vue de magasin.

<u>Résultats réels</u> :

La réponse de la nouvelle vue de magasin affiche la configuration du nom du produit sous la vue de magasin par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
