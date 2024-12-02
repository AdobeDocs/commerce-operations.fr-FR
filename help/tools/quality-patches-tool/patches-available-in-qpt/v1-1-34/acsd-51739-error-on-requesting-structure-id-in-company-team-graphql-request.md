---
title: 'ACSD-51739 : Erreur lors de la demande `structure_id` dans la demande GraphQL `CompanyTeam`'
description: Appliquez le correctif ACSD-51739 pour résoudre le problème Adobe Commerce en raison duquel une erreur est renvoyée lorsque le `structure_id` est demandé dans une requête GraphQL "CompanyTeam`.
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51739 : Erreur lors de la demande `structure_id` dans la demande `CompanyTeam` GraphQL

Le correctif ACSD-51739 corrige le problème qui entraînait le renvoi d’une erreur lorsqu’une requête `structure_id` était demandée dans une requête GraphQL `CompanyTeam`. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 est installé. L’ID de correctif est ACSD-51739. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur est renvoyée lorsque le `structure_id` est demandé dans une requête GraphQL `CompanyTeam`.

<u>Étapes à reproduire</u>

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** et définissez *[!UICONTROL Enable Company]* sur *Oui*.
1. Créez une société avec un utilisateur administrateur de société.
1. Créez un client (*customer1*) et affectez la société (créée ci-dessus) à ce client.
1. Sur le front-end, connectez-vous en tant qu’utilisateur administrateur de l’entreprise.
1. Créez une équipe d’entreprise et affectez *customer1* à l’équipe par glisser-déposer.
1. Exécutez la requête GraphQl de la société suivante, qui inclut `CompanyTeam` avec `structure_id` :

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

1. Vérifiez la réponse GraphQL.

<u>Résultats attendus</u> :

Aucune erreur n’est renvoyée et toutes les données demandées sont présentes dans la réponse GraphQL.

<u>Résultats réels</u> :

* La réponse contient une *erreur de serveur interne*.
* `var/log/exception.log` contient :

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
