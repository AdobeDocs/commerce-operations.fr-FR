---
title: 'ACSD-62671: [!DNL GraphQL] ne renvoie pas l’adresse mise à jour à la première tentative'
description: Appliquez le correctif ACSD-62671 pour résoudre le problème d’Adobe Commerce où une  [!DNL GraphQL]  ne renvoie pas d’informations d’adresse à jour lors de la première tentative.
feature: GraphQL
role: Admin, Developer
source-git-commit: 697b0e3d7789b0324866d2192f56613f5526e4df
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671 : [!DNL GraphQL] ne renvoie pas l&#39;adresse mise à jour à la première tentative

Le correctif ACSD-62671 corrige le problème où une requête [!DNL GraphQL] ne renvoie pas d’informations d’adresse à jour lors de la première tentative. Ce correctif est disponible lorsque la version 1.1.57 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) est installée. L’ID du correctif est ACSD-62671. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’utilisation de l’[!DNL GraphQL Application Server] , la demande d’adresse du client ne renvoie pas les données les plus récentes.

<u>Procédure à suivre </u> :

1. Installez et démarrez [!DNL GraphQL Application Server].
1. Assurez-vous que `graphQL_query_resolver_result` type de cache est activé.
1. Utilisez [!DNL GraphQL] pour :

   * Créez un client.
   * Générez un jeton.
   * Utilisez le jeton pour créer plusieurs adresses pour le client ci-dessus.

1. Envoyez [!DNL GraphQL] demande pour obtenir les adresses du client.
1. Ajoutez une nouvelle adresse au client.
1. Répétez plusieurs fois la requête de l’étape #4 lors de la surveillance du nombre d’adresses renvoyées dans la réponse.

<u>Résultats attendus</u> :

[!DNL GraphQL] réponse contient le nombre correct d’adresses client.

<u>Résultats réels</u> :

Parfois, un nombre incorrect d’adresses est renvoyé dans la réponse [!DNL GraphQL].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
