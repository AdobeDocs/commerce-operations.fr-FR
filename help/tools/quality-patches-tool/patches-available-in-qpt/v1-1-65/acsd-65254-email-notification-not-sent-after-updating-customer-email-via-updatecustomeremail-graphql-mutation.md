---
title: 'ACSD-65254 : notification par e-mail non envoyée après la mise à jour de l’e-mail du client via la mutation updateCustomerEmail [!DNL GraphQL]'
description: Appliquez le correctif ACSD-65254 pour résoudre le problème d’Adobe Commerce en raison duquel les notifications par e-mail n’étaient pas envoyées aux clients après la mise à jour réussie de leurs adresses e-mail sur leurs comptes à l’aide de la mutation updateCustomerEmail [!DNL GraphQL].
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%
---
# ACSD-65254 : notification par e-mail non envoyée après la mise à jour de l’e-mail du client via `updateCustomerEmail` mutation [!DNL GraphQL]

Le correctif ACSD-65254 corrige le problème en raison duquel les notifications par e-mail n’étaient pas envoyées aux clients après la mise à jour de leurs adresses e-mail sur leurs comptes à l’aide de la mutation [!DNL GraphQL] `updateCustomerEmail`. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65254. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les notifications par e-mail n’étaient pas envoyées aux clients après la mise à jour de leurs adresses e-mail à l’aide de la mutation `updateCustomerEmail` [!DNL GraphQL].

<u>Procédure à suivre </u> :

1. Créez un utilisateur à l’aide de la mutation suivante :

   ```graphql
   mutation {
       createCustomer(
           input: {
               firstname: "Test"
               lastname: "User"
               email: "test@test.com"
               password: "Admin@123"
               is_subscribed: true
           }
       ) {
           customer {
               created_at
           }
       }
   }
   ```

1. Générez un jeton pour l’utilisateur ou l’utilisatrice créé(e) précédemment et utilisez-le comme jeton porteur :

   ```graphql
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
       token
   }
   }
   ```

1. Essayez de mettre à jour l’e-mail de l’utilisateur créé précédemment à l’aide du dernier jeton du porteur créé :

   ```graphql
   mutation {
       updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
           customer {
               email
           }
       }
   }
   ```

<u>Résultats attendus</u> :

Les clients doivent recevoir des notifications par e-mail après la mise à jour des adresses e-mail sur leurs comptes.

<u>Résultats réels</u> :

Seul un e-mail d’abonnement est envoyé à la nouvelle adresse ; l’e-mail de confirmation de changement d’adresse e-mail n’est pas envoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
