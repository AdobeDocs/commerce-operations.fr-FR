---
title: "ACSD-61103 : le nombre d’échecs n’est pas réinitialisé à zéro après une connexion client réussie via l’API"
description: Appliquez le correctif ACSD-61103 pour résoudre le problème Adobe Commerce en raison duquel le nombre d’échecs dans la table &grave;customer_entity&grave; n’est pas réinitialisé à zéro une fois qu’un client s’est connecté via les points de terminaison de l’API.
feature: GraphQL, REST, Customers
role: Admin, Developer
source-git-commit: d53b747c3b2021e842647de5371a5f0f2a760f09
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-61103 : le nombre d’échecs n’est pas réinitialisé à zéro après une connexion client réussie via l’API

Le correctif ACSD-61103 résout le problème en raison duquel le nombre d’échecs dans la table `customer_entity` n’est pas réinitialisé à zéro une fois qu’un client s’est connecté via les points de terminaison de l’API. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-61103. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le nombre d’échecs dans la table `customer_entity` n’est pas réinitialisé à zéro même après qu’un client se soit connecté correctement via les points de terminaison de l’API.

<u>Étapes à reproduire</u> :

1. Créez un compte client.
1. Générez un jeton client via l’API, à l’aide de détails incorrects.
1. Vérifiez la colonne `failures_num` de la table `customer_entity` DB pour le client ci-dessus.
1. Générez un jeton client via l’API, à l’aide des détails corrects.
1. Vérifiez la colonne `failures_num` de la table `customer_entity` DB pour le client ci-dessus.

<u>Résultats attendus</u> :

La colonne `failures_num` doit être réinitialisée à 0 après avoir utilisé les informations d’identification correctes pour générer un jeton client via l’API.

<u>Résultats réels</u> :

La colonne `failures_num` n’est pas réinitialisée à 0 après avoir utilisé les informations d’identification correctes pour générer un jeton client via l’API.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.

