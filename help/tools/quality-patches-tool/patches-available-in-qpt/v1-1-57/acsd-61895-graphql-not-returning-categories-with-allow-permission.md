---
title: 'La requête ACSD-61895: [!DNL GraphQL] categories échoue pour le catalogue partagé privé avec une vue restreinte'
description: Appliquez le correctif ACSD-61895 pour résoudre le problème d’Adobe Commerce où les réponses  [!DNL GraphQL]  clients invités (utilisant un catalogue public partagé avec toutes les catégories autorisées) ne renvoyaient aucune catégorie lorsqu’un catalogue privé partagé avec des restrictions était créé pour les mêmes catégories.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
exl-id: ef986fa6-e8bc-4322-80f2-fa0c5d5e8d40
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# ACSD-61895 : [!DNL GraphQL] requête `categories` échoue pour le catalogue partagé privé avec une vue restreinte

Le correctif ACSD-61895 corrige le problème où les réponses [!DNL GraphQL] pour les clients invités (utilisant un catalogue public partagé avec toutes les catégories autorisées) ne renvoyaient aucune catégorie lorsqu’un catalogue privé partagé avec des restrictions était créé pour les mêmes catégories.

Après le correctif, il renvoie toutes les catégories disposant d’autorisations autorisées (catalogue public partagé) pour les utilisateurs invités, même si la catégorie racine ne dispose pas d’autorisations autorisées dans la portée d’un catalogue privé partagé.

Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61895. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les réponses [!DNL GraphQL] pour les clients invités (utilisant un catalogue public partagé avec toutes les catégories autorisées) ne renvoient aucune catégorie lorsqu’un catalogue privé partagé avec des restrictions est créé pour les mêmes catégories.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce avec le B2B et des exemples de données.
1. Assurez-vous que les fonctionnalités B2B sont activées.
1. Créez deux catalogues partagés : un public et un privé.

   * Catalogue Public Partagé :

      * Affectez toutes les catégories au catalogue public.

   * Catalogue partagé privé :

      * Attribuez uniquement la catégorie `Gear` et ses catégories enfants au catalogue privé.
      * Affectez le catalogue privé à une société de test.

1. Créez un utilisateur d’entreprise :

   * Créez un utilisateur associé à la société de test liée au catalogue partagé privé.
   * Assurez-vous que l’utilisateur ou l’utilisatrice ne peut accéder qu’à la catégorie `Gear` et à ses catégories enfants sur le front-end lors de la connexion.

1. Catégories de requête via l’API :

   * Utilisez le client API pour exécuter la requête [!DNL GraphQL] suivante sans jeton client :

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Observez la réponse et vérifiez si la catégorie `Gear` et les autres catégories sont renvoyées.
1. Interrogez désormais les catégories avec un jeton client :

   * Connectez-vous en tant qu’utilisateur de la société de test.
   * Exécutez la même requête de catégorie de [!DNL GraphQL], mais incluez le jeton client pour l’utilisateur connecté.
   * Observez la réponse et vérifiez si seule la catégorie `Gear` et ses catégories enfants sont renvoyées.


<u>Résultats attendus</u> :

Lors de l’interrogation en tant qu’utilisateur d’entreprise invité, toutes les catégories doivent être renvoyées (comme prévu).

<u>Résultats réels</u> :

La réponse de la requête `categories` n’affiche aucune catégorie.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
