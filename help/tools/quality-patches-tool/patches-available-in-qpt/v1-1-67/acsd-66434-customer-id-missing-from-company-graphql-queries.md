---
title: 'ACSD-66434 : [!UICONTROL Customer ID] manquant dans les requêtes  [!DNL GraphQL]  société'
description: Appliquez le correctif ACSD-66434 pour résoudre le problème d’Adobe Commerce où [!UICONTROL Customer ID] est absent des requêtes  [!DNL GraphQL]  la société.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 422e5a9eb9948032cccaac98415cf4b92895d5a9
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# ACSD-66434 : [!UICONTROL Customer ID] manquant dans les requêtes de [!DNL GraphQL] d&#39;entreprise

Le correctif ACSD-66434 corrige le problème où **[!UICONTROL Customer ID]** est absent des requêtes de [!DNL GraphQL] d’entreprise. Ce correctif est disponible lorsque la version 1.1.67 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66434. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête de société [!DNL GraphQL] renvoie des `null` pour le **[!UICONTROL Customer ID]** dans la structure de la société.

<u>Procédure à suivre </u> :

1. Installez Adobe Commerce 2.4-develop avec les modules B2B et Inventory.
1. Dans l’administration Commerce, activez les fonctionnalités B2B et créez une société de test.
1. Générez un jeton porteur pour l’administrateur de la société à l’aide de la mutation [!DNL GraphQL] suivante :

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Utilisez le jeton généré pour récupérer la structure d’entreprise du client avec la requête [!DNL GraphQL] suivante :

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u>Résultats attendus</u> :

**[!UICONTROL Customer ID]** doit être renvoyé dans la requête de [!DNL GraphQL] d’entreprise.

<u>Résultats réels</u> :

**[!UICONTROL Customer ID]** renvoie comme `null` dans la requête de [!DNL GraphQL] d’entreprise.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
