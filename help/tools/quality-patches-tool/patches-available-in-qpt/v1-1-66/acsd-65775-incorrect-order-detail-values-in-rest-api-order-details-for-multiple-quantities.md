---
title: 'ACSD-65775 : valeurs « base_row_total » et « row_total » incorrectes dans les détails de commande de l’API REST pour plusieurs quantités'
description: Appliquez le correctif ACSD-65775 pour résoudre le problème d’Adobe Commerce où les détails de commande de l’API REST renvoient des valeurs « base_row_total » et « row_total » incorrectes lorsque plusieurs quantités du même article sont commandées.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 23c78abaf28f64baf0e91bcaf89bd0e34b5bf78a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-65775 : valeurs `base_row_total` et `row_total` incorrectes dans les détails de commande de l’API REST pour plusieurs quantités

Le correctif ACSD-65775 corrige le problème où les détails de commande de l’API REST renvoient des valeurs de `base_row_total` et de `row_total` incorrectes lorsque plusieurs quantités du même élément sont commandées. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65775. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les `base_row_total` et `row_total` de la réponse de l’API REST des détails de la commande affichent le prix unitaire au lieu du prix total lorsque plusieurs quantités du même article sont commandées.

<u>Procédure à suivre </u> :

1. Créez deux produits simples : simple1 à 10 $ et simple2 à 15 $.
1. Créez un compte client.
1. Ajoutez simple1 au panier avec la quantité 2 et simple2 avec la quantité 3.
1. Passez la commande à l’aide du compte client.
1. Obtenez un jeton d’administration en envoyant une requête POST à `/rest/V1/integration/admin/token` avec la payload suivante :

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Récupérez les détails de la commande à l’aide d’une requête GET à `/rest/default/V1/orders/1`.

<u>Résultats attendus</u> :

`base_row_total` et `row_total` doivent refléter le prix total calculé en multipliant la quantité par le prix de l&#39;article (par exemple, 2 × 10 EUR = 20 EUR pour simple1).

<u>Résultats réels</u> :

`base_row_total` et `row_total` renvoient uniquement le prix unitaire (par exemple, 10 $ pour simple1 au lieu de 20 $).

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
