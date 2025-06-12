---
title: 'MDVA-40830 : crédit de magasin appliqué plusieurs fois pendant la commande'
description: Le correctif MDVA-40830 corrige le problème en raison duquel le crédit de magasin est appliqué plusieurs fois lors du placement de la commande. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-40830. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Orders, Returns
role: Admin
exl-id: 4ee952c8-2736-47b2-84f6-a7a0556608dd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-40830 : crédit de magasin appliqué plusieurs fois pendant la commande

Le correctif MDVA-40830 corrige le problème en raison duquel le crédit de magasin est appliqué plusieurs fois lors du placement de la commande. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 est installé. L’ID du correctif est MDVA-40830. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le crédit de magasin est appliqué plusieurs fois lors du placement de la commande.

<u>Procédure à suivre </u> :

1. Créez un client et ajoutez un crédit de magasin au compte client.
1. Ajoutez un produit simple au panier.
1. Définissez l’adresse de livraison et l’adresse de facturation pour le panier.
1. Vérifiez le grand_total du panier.
1. Appliquez le crédit de magasin au panier à l’aide de la requête GraphQL suivante :

<pre>
<code class="language-graphql">
mutation {
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) {
    cart {
      prices {
        grand_total {
          currency
          value
        }
      }
      applied_store_credit {
        applied_balance {
          currency
          value
        }
        current_balance {
          currency
          value
        }
      }
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u> :

La valeur de applied_store_credit est appliquée avec précision et les totaux du panier sont correctement reflétés dans la réponse de l’API.

<u>Résultats réels</u> :

La valeur de applied_store_credit est appliquée deux fois, affectant à la fois le panier et le total général.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
