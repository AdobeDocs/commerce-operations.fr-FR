---
title: 'BB2B-2598 : ajoute une fonctionnalité de mise en cache aux requêtes GraphQl storeConfig, currency, country, COUNTRIES, availableStores'
description: Appliquez le correctif BB2B-2598 pour ajouter une fonctionnalité de mise en cache aux requêtes GraphQl storeConfig, currency, country, country, country et availableStores .
feature: B2B, GraphQL, Cache
role: Admin
exl-id: b842fab4-d2c0-4ef1-be13-182f09015cd7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# BB2B-2598 : ajoute une fonctionnalité de mise en cache aux requêtes GraphQl `storeConfig`, `currency`, `country`, `countries` et `availableStores`

Le correctif BB2B-2598 ajoute une fonctionnalité de mise en cache aux requêtes GraphQl `storeConfig`, `currency`, `country`, `countries` et `availableStores`. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est BB2B-2598. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7-beta1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les requêtes `availableStores`, `countries`, `country`, `currency`, `storeConfig` et `customAttributeMetadata` GraphQL ne peuvent pas être mises en cache.

<u>Conditions préalables</u> :

* Le serveur pointe vers [!DNL Varnish] proxy vers le serveur principal d’Adobe Commerce.
* La `system/full_page_cache/caching_application` du paramètre de configuration est définie sur *2* ([!DNL Varnish]) ou accédez à Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > et définissez-la sur [!DNL Varnish].

Une fois le correctif appliqué, exécutez les étapes suivantes pour vous assurer que la fonctionnalité de mise en cache est désormais disponible :

1. Envoyez `GET` requête à l’une des requêtes GraphQL répertoriées ci-dessus, à l’aide de champs arbitraires.
1. Renvoyez la demande sans modification ; vous remarquerez qu’elle est beaucoup plus rapide. Notez que la requête n’est pas envoyée au serveur principal, mais elle est entièrement gérée par [!DNL Varnish] comme un accès au cache.
1. Si une épreuve supplémentaire est requise, commentez le désensemble de `X-Magento-Debug`’en-tête présent dans notre [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), puis redémarrez [!DNL Varnish] et exécutez à nouveau les étapes ci-dessus.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
