---
title: "ACSD-60584 : le jeton d’accès créé pour un site web est autorisé à accéder aux informations d’autres sites web"
description: Appliquez le correctif ACSD-60584 pour résoudre le problème en raison duquel le jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web.
feature: Customers, GraphQL
role: Admin, Developer
source-git-commit: eba4a8fd7bbf52fbc4295feab0d5bb79e7383b66
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584 : le jeton d’accès créé pour un site web est autorisé à accéder aux informations d’autres sites web.

Le correctif ACSD-60584 corrige le problème en raison duquel le jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53 est installé. L’ID de correctif est ACSD-60584. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le jeton API créé pour l’utilisateur sur un site web vous permet d’accéder aux informations du client, de créer un panier et d’ajouter des produits au panier sur d’autres pages vues du site web.

<u>Étapes à reproduire</u> :

1. Assurez-vous que **[!DNL Share Customer Accounts configuration]** est défini sur **[!UICONTROL Per Website]**.
1. Créez des *sites web*, *magasin* et *storeview* supplémentaires.
1. Créez deux clients avec le même email sur le *site web* principal et le *site web* de l&#39;étape précédente.
1. Générez un jeton client via [!DNL GraphQL] sur le site web principal.
1. À l’aide du jeton généré, envoyez une requête **[!DNL GraphQL]** client avec le deuxième site web dans l’en-tête pour récupérer les informations client.
1. Observez le résultat renvoyé.

<u>Résultats attendus</u> :

Les informations client du *site web* principal sont renvoyées car le jeton du *site web* principal est utilisé dans la requête [!DNL GraphQL].

<u>Résultats réels</u> :

Les informations sur les clients du deuxième site web sont renvoyées.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].