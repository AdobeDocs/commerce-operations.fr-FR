---
title: 'ACSD-66041 : code postal de l''Irlande (IE) impossible à rechercher pour les lieux de retrait en raison de l''absence de CountryID'
description: Appliquez le correctif ACSD-66041 pour résoudre le problème Adobe Commerce en raison duquel les codes postaux Irlande (IE) ne pouvaient pas être recherchés dans les lieux de retrait en raison d’un ID de pays manquant.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 4c33da14-38b2-4a3c-a680-849b62dfb896
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-66041 : code postal de l&#39;Irlande (IE) impossible à rechercher pour les emplacements de retrait en raison de `CountryID` manquants

Le correctif ACSD-66041 corrige le problème en raison duquel les codes postaux Irlande (IE) ne peuvent pas être recherchés pour les emplacements de retrait en raison d’un `CountryID` manquant. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66041. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les codes postaux Irlande (IE) ne peuvent pas être recherchés dans les lieux de retrait en raison d&#39;un `CountryID` manquant.

<u>Procédure à suivre </u> :

1. Exécutez la requête GraphQL suivante :

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. Utilisez les variables suivantes :

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>Résultats attendus</u> :

Les codes postaux de l&#39;Irlande sont disponibles pour rechercher les lieux de retrait.

<u>Résultats réels</u> :

* Une *erreur de serveur interne* est renvoyée.
* `var/log/exception.log` contient l&#39;erreur suivante :

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
