---
title: 'ACSD-61103 : nombre d’échecs non réinitialisé après une connexion réussie du client via l’API'
description: Appliquez le correctif ACSD-61103 pour résoudre le problème d’Adobe Commerce où le nombre d’échecs dans la table « customer_entity » n’est pas réinitialisé à zéro après qu’un client s’est connecté avec succès via les points d’entrée de l’API.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103 : nombre d’échecs non réinitialisé après une connexion réussie du client via l’API

Le correctif ACSD-61103 résout le problème où le nombre d’échecs dans la table `customer_entity` n’est pas réinitialisé à zéro après qu’un client s’est connecté avec succès via les points d’entrée de l’API. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61103. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le nombre d’échecs dans le tableau `customer_entity` n’est pas réinitialisé, même après qu’un client s’est connecté avec succès via les points d’entrée de l’API.

<u>Procédure à suivre </u> :

1. Créez un compte client.
1. Générer un jeton client via l’API, en utilisant des détails incorrects.
1. Vérifiez la colonne `failures_num` du tableau de base de données `customer_entity` pour le client ci-dessus.
1. Générez un jeton client via l’API, en utilisant les détails appropriés.
1. Vérifiez la colonne `failures_num` du tableau de base de données `customer_entity` pour le client ci-dessus.

<u>Résultats attendus</u> :

La colonne `failures_num` doit être réinitialisée à 0 après l’utilisation des informations d’identification correctes pour générer un jeton client via l’API.

<u>Résultats réels</u> :

La colonne `failures_num` n’est pas réinitialisée à 0 après l’utilisation des informations d’identification correctes pour générer un jeton client via l’API.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
