---
title: 'ACSD-58352 : les libellés d’attribut de retour du magasin par défaut sont renvoyés via [!DNL GraphQL] API'
description: Appliquez le correctif ACSD-58352 pour résoudre le problème d’Adobe Commerce où les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via [!DNL GraphQL]’API lorsqu’une vue de magasin autre que celle par défaut est spécifiée dans l’en-tête de la requête.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
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
source-wordcount: '417'
ht-degree: 0%
---
# ACSD-58352 : les libellés d’attribut de retour du magasin par défaut sont renvoyés via [!DNL GraphQL] API

Le correctif ACSD-58352 corrige le problème où les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via [!DNL GraphQL]’API lorsqu’une vue de magasin autre que celle par défaut est spécifiée dans l’en-tête de la requête. Ce correctif est disponible lorsque la version 1.1.50 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58352. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les libellés d’attribut de retour du magasin par défaut sont renvoyés via l’API [!DNL GraphQL].

<u>Procédure à suivre </u> :

1. Activez la **[!UICONTROL Return Merchandising Authorization]**.
1. Créez un *[!UICONTROL Additional Store]* et un *[!UICONTROL Store View]* sous le site web par défaut.
1. Modifiez l’attribut de retour **[!UICONTROL Reason for Return]** et ajoutez des libellés pour toutes les vues de magasin.
1. Créez un *[!UICONTROL Order]*.
1. Créez un *[!UICONTROL Return]* pour cette commande. Assurez-vous que le *[!UICONTROL Return]* a le statut *[!UICONTROL Pending]*.
1. Envoyez une requête de [!DNL GraphQL] client avec les [!UICONTROL Store View] non par défaut spécifiées dans l’en-tête :

   ```graphql
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observez la réponse.

<u>Résultats attendus</u>

Les étiquettes de retour dans la réponse [!DNL GraphQL] sont pour les [!UICONTROL Store View] définies dans l’en-tête de la requête.

<u>Résultats réels</u> :

Les étiquettes de retour dans [!DNL GraphQL] réponse correspondent à l’[!UICONTROL Store View] par défaut.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
