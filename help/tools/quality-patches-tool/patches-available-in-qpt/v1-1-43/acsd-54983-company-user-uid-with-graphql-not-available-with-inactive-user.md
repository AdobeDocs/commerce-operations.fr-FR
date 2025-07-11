---
title: 'ACSD-54983 : l’utilisateur d’entreprise UID avec GraphQL n’est pas disponible avec l’utilisateur inactif'
description: Appliquez le correctif ACSD-54983 pour résoudre le problème d’Adobe Commerce en raison duquel il n’est pas possible d’obtenir la demande de l’utilisateur de la société UID avec GraphQL lorsque le statut de l’utilisateur est défini sur inactif.
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983 : l’utilisateur d’entreprise UID avec GraphQL n’est pas disponible avec l’utilisateur inactif

Le correctif ACSD-54983 corrige le problème en raison duquel il n’est pas possible d’obtenir la demande de l’utilisateur de la société UID avec GraphQL lorsque le statut de l’utilisateur est défini sur inactif. Ce correctif est disponible lorsque la version 1.1.43 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-54983. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible d’obtenir l’utilisateur de l’entreprise UID avec la requête GraphQL lorsque le statut de l’utilisateur est défini sur inactif.

<u>Procédure à suivre </u> :

1. Créez une société avec un utilisateur administrateur. Par ex. company@test.com.
1. Créez un nouveau client.
1. Affectez le nouveau client à une entreprise.
1. Prends un **[!UICONTROL company admin token]**.
1. À l’aide de l’**[!UICONTROL company admin token]** , récupérez la structure de l’entreprise. Voir [Renvoyer la structure de l’entreprise](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) dans notre documentation destinée aux développeurs.
1. La réponse contient uniquement des clients *ACTIFS* avec leurs ID.
1. Mettez à jour l’utilisateur de la société sur *INACTIF*.
1. Récupérez à nouveau la structure de l’entreprise.

<u>Résultats attendus</u> :

Il est possible d’obtenir l’utilisateur de la société UID lorsque le statut est défini sur inactif.

<u>Résultats réels</u> :

Les clients inactifs ne figurent pas dans la liste. Impossible d&#39;obtenir l&#39;utilisateur de la société UID lorsque le statut est défini sur inactif.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
