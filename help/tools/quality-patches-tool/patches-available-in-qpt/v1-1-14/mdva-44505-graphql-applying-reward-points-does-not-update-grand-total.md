---
title: 'MDVA-44505 : la requête GraphQL pour l’application de points de récompense au panier ne met pas à jour le total général'
description: Le correctif MDVA-44505 résout le problème où la requête GraphQL pour un panier appliquant des points de récompense ne prend pas en compte les points de récompense et renvoie un total général incorrect. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-44505. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505 : la requête GraphQL pour l’application de points de récompense au panier ne met pas à jour le total général

Le correctif MDVA-44505 résout le problème où la requête GraphQL pour un panier appliquant des points de récompense ne prend pas en compte les points de récompense et renvoie un total général incorrect. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-44505. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL d’un panier qui applique des points de récompense ne prend pas en compte les points de récompense et renvoie un total général incorrect.

<u>Procédure à suivre </u> :

1. Configurez les points de récompense.
1. Créez un panier et appliquez des points de récompense.
1. Appelez la requête `GetCart` à partir du point d’entrée `GraphQL` et récupérez votre panier :

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Vérifiez l&#39;entrée du total général.
1. Vérifiez maintenant le total du panier du client à l’aide de l’API REST (`/rest/V1/carts/mine/totals`).

<u>Résultats attendus</u> :

La requête GraphQL pour le panier renvoie le total général correct qui prend en compte les points de récompense.

<u>Résultats réels</u> :

La requête GraphQL ne prend pas en compte les points de récompense et renvoie un total général incorrect.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
