---
title: 'MDVA-44562 : identifiant de magasin pour les éléments de devis remplacés par identifiant de magasin par défaut.'
description: Le correctif MDVA-44562 corrige le problème en raison duquel l’ID de magasin par défaut remplace l’ID de magasin pour les éléments de guillemet pour les requêtes GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID de correctif est MDVA-44562. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562 : identifiant de magasin pour les éléments de devis remplacés par identifiant de magasin par défaut.

Le correctif MDVA-44562 corrige le problème en raison duquel l’ID de magasin par défaut remplace l’ID de magasin pour les éléments de guillemet pour les requêtes GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 est installé. L’ID de correctif est MDVA-44562. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ID de magasin pour les éléments de guillemet est remplacé par l’ID de magasin par défaut pour les requêtes GraphQL.

<u>Étapes à reproduire</u> :

1. Créez une vue de magasin.
1. Créez un produit simple avec des noms différents par vue de magasin.
1. Créez un client.
1. Obtenez le jeton d’autorisation du client.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Créez un nouveau devis pour le client à l’aide du jeton d’autorisation.

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

1. Obtenez le contenu du panier pour la vue de magasin par défaut.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Obtenez le contenu du panier pour la nouvelle vue de magasin.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Résultats attendus</u> :

La réponse de la nouvelle vue de magasin affiche le nom du produit à partir de la nouvelle vue de magasin.

<u>Résultats réels</u> :

La réponse de la nouvelle vue de magasin affiche la configuration du nom du produit sous la vue de magasin par défaut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
