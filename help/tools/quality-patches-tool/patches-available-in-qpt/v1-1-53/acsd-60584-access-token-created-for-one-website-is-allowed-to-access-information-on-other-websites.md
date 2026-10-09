---
title: 'ACSD-60584 : le jeton d’accès créé pour un site web est autorisé à accéder aux informations d’autres sites web'
description: Appliquez le correctif ACSD-60584 pour résoudre le problème où le jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web.
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
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
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-60584 : le jeton d’accès créé pour un site web est autorisé à accéder aux informations d’autres sites web

Le correctif ACSD-60584 corrige le problème en raison duquel le jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) est installée. L’ID du correctif est ACSD-60584. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le jeton API créé pour l’utilisateur sur un site web vous permet d’accéder aux informations du client, de créer un panier et d’ajouter des produits au panier sur d’autres affichages de site web.

<u>Procédure à suivre </u> :

1. Assurez-vous que **[!DNL Share Customer Accounts configuration]** est défini sur **[!UICONTROL Per Website]**.
1. Créez des *site web*, *magasin* et *storeview* supplémentaires.
1. Créez deux clients avec le même e-mail sur le *site web* principal et le *site web* de l’étape précédente.
1. Générez un jeton client via [!DNL GraphQL] sur le site web principal.
1. À l’aide du jeton généré, envoyez une requête de **[!DNL GraphQL]** client avec le deuxième site web dans l’en-tête pour récupérer les informations du client.
1. Observez le résultat renvoyé.

<u>Résultats attendus</u> :

Les informations sur le client du *site web* principal sont renvoyées, car le jeton du *site web* principal est utilisé dans [!DNL GraphQL] requête.

<u>Résultats réels</u> :

Les informations client du deuxième site web sont renvoyées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
