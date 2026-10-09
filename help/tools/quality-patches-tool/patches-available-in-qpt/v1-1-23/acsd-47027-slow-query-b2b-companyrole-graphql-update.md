---
title: 'ACSD-47027 : mise à jour de [!DNL GraphQL] B2B à requête lente [!UICONTROL CompanyRole]'
description: Appliquez le correctif ACSD-47027 pour résoudre le problème d’Adobe Commerce lié à une mise à jour de [!DNL GraphQL] de [!UICONTROL CompanyRole] B2B de requête lente.
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
exl-id: 91eb0297-1ba8-47b7-9581-29bee835843c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%
---
# ACSD-47027 : mise à jour de [!DNL GraphQL] B2B à requête lente [!UICONTROL CompanyRole]

Le correctif ACSD-47027 résout le problème en raison duquel la mise à jour [!DNL GraphQL] de la [!UICONTROL CompanyRole] B2B de requête lente ne fonctionne pas comme prévu. Ce correctif est disponible lorsque la version 1.1.23 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-47027. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour du [!DNL GraphQL] de [!UICONTROL CompanyRole] B2B de requête lente ne fonctionne pas comme prévu.

<u>Conditions préalables</u> :

Installez le module B2B .

<u>Procédure à suivre </u> :

1. Dans Adobe Commerce Admin, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** et définissez **[!UICONTROL Enable Company]** sur _Oui_.
1. Accédez au serveur frontal et créez une entreprise.
1. Après vous être connecté en tant qu’utilisateur d’entreprise, accédez à **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** et ajoutez un nouveau rôle.
1. Activez [!UICONTROL dev] journal des requêtes à l’aide de `bin/magento dev:que:enab`.
1. Envoyez maintenant la requête de [!DNL GraphQL] ci-dessous (l’identifiant est l’identifiant de rôle codé en [!UICONTROL base64]) :

   ```graphql
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id
   
         name
   
         permissions {
         id
   
         text
   
         children {
            id
   
            text
   
            children {
               id
   
               text
             }
           }
         }
       }
     }
   }
   ```

1. Vérifiez le journal des requêtes.
1. Vous pouvez constater que la requête ci-dessus est exécutée. Cette requête est exécutée en `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>Résultats attendus</u> :

Le `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` doit être optimisé pour éviter de charger toutes les données disponibles dans la table de base de données **[!UICONTROL company_permissions]**.

<u>Résultats réels</u> :

Adobe Commerce exécute une requête sans aucun filtre. Lorsqu’il y a un grand nombre d’enregistrements, la préparation de la collecte de données par Adobe Commerce prend beaucoup de temps.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud . 

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
