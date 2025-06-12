---
title: 'ACSD-51739 : erreur lors de la demande de « structure_id » dans la requête GraphQL « CompanyTeam »'
description: Appliquez le correctif ACSD-51739 pour résoudre le problème d’Adobe Commerce où une erreur est renvoyée lorsque « structure_id » est demandé dans une requête GraphQL « CompanyTeam ».
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739 : erreur lors de la demande de `structure_id` dans `CompanyTeam` demande GraphQL

Le correctif ACSD-51739 corrige le problème où une erreur est renvoyée lorsque le `structure_id` est demandé dans une requête GraphQL `CompanyTeam`. Ce correctif est disponible lorsque la version 1.1.34 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51739. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur est renvoyée lorsque l’`structure_id` est demandée dans une requête GraphQL `CompanyTeam`.

<u>Procédure à suivre</u>

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**, puis définissez *[!UICONTROL Enable Company]* sur *Oui*.
1. Créez une société avec un utilisateur administrateur de société.
1. Créez un nouveau client (*customer1*) et affectez la société (créée ci-dessus) à ce client.
1. Sur le front-end, connectez-vous en tant qu’utilisateur administrateur de la société.
1. Créez une équipe d’entreprise et affectez *client1* à l’équipe par glisser-déposer.
1. Exécutez la requête GraphQl d’entreprise suivante, qui inclut les `CompanyTeam` avec `structure_id` :

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Vérifiez la réponse de GraphQL.

<u>Résultats attendus</u> :

Aucune erreur n’est renvoyée et toutes les données demandées sont présentes dans la réponse de GraphQL.

<u>Résultats réels</u> :

* La réponse contient une *erreur de serveur interne*.
* `var/log/exception.log` contient :

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
