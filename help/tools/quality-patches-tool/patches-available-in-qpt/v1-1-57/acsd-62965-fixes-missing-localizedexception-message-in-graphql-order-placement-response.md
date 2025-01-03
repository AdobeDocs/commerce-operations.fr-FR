---
title: 'ACSD-62965 : corrige le message LocalizedException manquant dans la réponse d’emplacement de commande GraphQL'
description: Appliquez le correctif ACSD-62965 pour résoudre les problèmes d’Adobe Commerce où le message « LocalizedException » n’était pas inclus dans la réponse de GraphQL lors du placement de la commande.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965 : corrige le message `LocalizedException` manquant dans la réponse d’emplacement de commande GraphQL

Le correctif ACSD-62965 corrige le problème où le message `LocalizedException` n’était pas inclus dans la réponse GraphQL lors du placement de la commande. Ce correctif est disponible avec la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). L’ID du correctif est ACSD-62965. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La réponse GraphQL pour l’emplacement de commande n’inclut pas de message `LocalizedException`, ce qui entraîne l’insuffisance des détails d’erreur pour le débogage.

<u>Procédure à suivre </u> :

1. Installez une instance de **[!DNL Adobe Commerce]** propre.
1. Ajoutez un produit au panier et passez à l’étape de placement de la commande.
1. Ajoutez un `LocalizedException` à `Magento\Framework\Exception\LocalizedException` dans `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`.
1. Insérez l&#39;exception après la ligne suivante :

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Ajoutez l’exception :

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Exécutez la requête GraphQL de commande de placement :

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Observez la réponse :
   1. La réponse n’inclut pas le message `LocalizedException`.
   1. Exemple de réponse incorrecte :

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>Résultats attendus</u> :

Si une `LocalizedException` se produit, le message d’exception doit être inclus dans la réponse GraphQL d’emplacement de commande pour une meilleure gestion des erreurs.

<u>Résultats réels</u> :

Si une `LocalizedException` se produit, le message d&#39;exception n&#39;est pas inclus dans la réponse GraphQL de placement de commande.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
