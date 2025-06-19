---
title: 'ACSD-54026 : message d’erreur incorrect pour la requête GraphQL updateCompanyRole'
description: Appliquez le correctif ACSD-54026 pour résoudre le problème d’Adobe Commerce en présence d’un message d’erreur incorrect pour une requête de GraphQL updateCompanyRole destinée à un utilisateur non autorisé.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54026 : message d’erreur incorrect pour `updateCompanyRole` requête GraphQL

Le correctif ACSD-54026 corrige le problème en raison duquel un message d’erreur incorrect apparaît pour une requête `updateCompanyRole` GraphQL destinée à un utilisateur non autorisé. Ce correctif est disponible lorsque la version 1.1.39 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-54026. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Obtention d’un message d’erreur incorrect pour une requête `updateCompanyRole` GraphQL pour un utilisateur non autorisé.

<u>Procédure à suivre </u> :

1. Activez la société B2B dans la configuration.
1. Créez une entreprise.
1. Envoyez une requête `updateCompanyRole` GraphQL sans transmettre de jeton porteur ou avec un jeton porteur non valide.
1. Observez le message d’erreur dans la réponse de GraphQL.

<u>Résultats attendus</u> :

Le message d’erreur suivant s’affiche : *Le client actuel n’est pas autorisé.*

<u>Résultats réels</u> :

Le message d’erreur suivant s’affiche : *Le client n’est pas un utilisateur de la société.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
