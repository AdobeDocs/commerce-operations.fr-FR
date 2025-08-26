---
title: 'ACSD-66311 : la grille Entreprises se charge lentement pour les utilisateurs administrateurs restreints'
description: Appliquez le correctif ACSD-66311 pour résoudre le problème d’Adobe Commerce en raison duquel la grille des sociétés se charge lentement pour les utilisateurs administrateurs disposant d’un accès restreint aux sites web.
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311 : la grille Entreprises se charge lentement pour les utilisateurs administrateurs restreints

Le correctif ACSD-66311 corrige le problème en raison duquel la grille de sociétés se charge lentement pour les utilisateurs administrateurs disposant d’un accès restreint au site web. Ce correctif est disponible lorsque la version 1.1.69 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66311. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La grille des sociétés se charge lentement pour les utilisateurs administrateurs disposant d’un accès restreint au site web.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec **[!UICONTROL B2B features]**.
1. Créez 2 sites web supplémentaires (en plus du site web principal) avec des magasins/vues :
   * Site web principal (créé lors de l&#39;installation)
   * Site web 2 → Store 2 → StoreView 2
   * Site web 3 → Store 3 → StoreView 3
1. Créez le rôle d’utilisateur **[!UICONTROL Admins in Scope]** :
   * Portée : seulement deux magasins : *Site Web principal* + *Site Web 3/Magasin 3*.
   * Ressources : uniquement *Tableau de bord* + *Entreprises*.
1. Créez un utilisateur administrateur avec un **[!UICONTROL Admins in Scope]** de rôle, par exemple **adminscope**.
1. Générer des données clients et d’entreprise distribuées spécifiques :
   1. **Clients affectés à des sites web**

      | Identifiant du site web | Nombre de clients |
      |------------|---------------------|
      | 1 | 600 000 |
      | 2 | 1 500 |
      | 3 | 500 |


   1. Exécutez la requête suivante pour vérifier la distribution :

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Clients affectés à des sociétés**

      | Nombre de clients | Nombre d&#39;entreprises |
      |---------------------|---------------------|
      | 1 | 4 500 |
      | 2 | ~1 000 |
      | ~595 k | 1 |

   1. Exécutez la requête suivante pour vérifier la distribution :

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            SELECT company_id, COUNT(customer_id) AS customer_count
            FROM company_advanced_customer_entity
            GROUP BY company_id
) COMME sous-requête
GROUP BY customer_count
ORDER BY customer_count ;
«

1. Réindexez toutes les données pour générer des entrées dans le **customer_grid_flat**.
1. Connectez-vous en tant qu **adminscope**.
1. Accédez à **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.

<u>Résultats attendus</u> :

La page se charge en moins d’une seconde.

<u>Résultats réels</u> :

Le chargement de la page prend plus de 14 minutes.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
