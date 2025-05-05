---
title: 'ACSD-49970 : gestion incorrecte des erreurs GraphQL'
description: Appliquez le correctif ACSD-49970 pour résoudre le problème Adobe Commerce en raison duquel les erreurs GraphQL sont mal gérées lorsque [!UICONTROL New Relic Reporting] est activé.
feature: GraphQL, Observability
role: Admin
exl-id: f06f6cbf-ea85-406a-850d-f63e1001ff82
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-49970 : gestion incorrecte des erreurs GraphQL

Le correctif ACSD-49970 corrige le problème de gestion incorrecte des erreurs GraphQL lorsque *[!UICONTROL New Relic Reporting]* est activé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 est installé. L’ID de correctif est ACSD-49970. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La clé `GraphQLOperationNames` n’est pas correctement gérée si `logDataHelper` contient cette clé ou non.

<u>Étapes à reproduire</u> :

1. Exécutez `bin/magento deploy:mode:set developer`.
1. Connectez-vous à l’administrateur.
1. Activez **[!UICONTROL New Relic Integration]** depuis **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Remarque : même si une erreur s’affiche indiquant que l’extension [!DNL New Relic] n’est pas disponible, la configuration est enregistrée).
1. Exécutez cette mutation *GraphQL* vers `http://yourMagentoDomain/graphql` à partir du client *[!DNL Altair]* ou de tout autre client ou via cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Remarque : définissez **[!UICONTROL Header]** sur [!UICONTROL Content-Currency:CA] avant de l’exécuter).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Résultats attendus</u> :

Il n&#39;y a pas *500 exception* dans les journaux, la clé `GraphQLOperationNames` est correctement gérée.

<u>Résultats réels</u> :

Il existe une *500 exception* dans les journaux, la clé `GraphQLOperationNames` n’est pas traitée correctement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
