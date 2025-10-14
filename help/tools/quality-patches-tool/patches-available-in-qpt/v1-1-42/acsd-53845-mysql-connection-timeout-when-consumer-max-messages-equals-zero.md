---
title: 'ACSD-53845 : problème de délai d’expiration de connexion MySQL lorsque max_messages du client = 0'
description: Appliquez le correctif ACSD-53845 pour résoudre le problème d’Adobe Commerce où la connexion MySQL expire lorsque le client « max_messages = 0 ».
feature: REST, Configuration
role: Admin, Developer
exl-id: 437e29f4-b11a-466c-9928-3867821d2b8d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-53845 : problème de délai d’expiration de connexion MySQL lors de la `max_messages = 0` du client

Le correctif ACSD-53845 corrige le problème en raison duquel la connexion MySQL expire lors de l’`max_messages = 0` du client. Ce correctif est disponible lorsque la version 1.1.42 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-53845. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La connexion MySQL expire lorsque le client `max_messages = 0`.

Cependant, la connexion à la base de données sera restaurée lors du démarrage d&#39;une transaction.

<u>Procédure à suivre </u> :

1. Envoyez une requête pour mettre à jour les produits en bloc à l’aide du point d’entrée de l’API REST `async/bulk/V1/products`.
1. Vérifiez le statut dans la table des `magento_operation`.

<u>Résultats attendus</u> :

Les produits sont mis à jour.

<u>Résultats réels</u> :

1. Une erreur est consignée :

   ```
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* pour cette opération reste *4* dans le tableau `magento_operation`.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool]
* Adobe Commerce sur les infrastructures cloud : [&#x200B; Mises à niveau et correctifs > Appliquer des correctifs &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool]
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
