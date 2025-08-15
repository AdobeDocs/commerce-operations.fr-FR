---
title: 'ACSD-61785 : la mise à jour de l’attribut reward_warning_notification n’est pas possible via la mutation GraphQL et les appels API REST'
description: Appliquez le correctif ACSD-61785 pour résoudre le problème d’Adobe Commerce en raison duquel la mise à jour de l’attribut « reward_warning_notification » n’est pas possible via la mutation de GraphQL et les appels API REST.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785 : la mise à jour de l’attribut reward_warning_notification n’est pas possible via la mutation GraphQL et les appels API REST

Le correctif ACSD-61785 corrige le problème en raison duquel la mise à jour de l’attribut `reward_warning_notification` n’est pas possible via la mutation GraphQL et les appels de l’API REST. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61785. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour de l’attribut `reward_warning_notification` n’est pas possible via la mutation GraphQL et les appels API REST.

<u>Procédure à suivre </u> :

1. Vérifiez la documentation/le schéma de l’API GraphQL et REST pour *S’abonner aux mises à jour de solde* et *s’abonner aux notifications d’expiration de points*.

<u>Résultats attendus</u> :

Il est possible de s’abonner aux *Mises à jour du solde de récompenses* et aux *Notifications d’expiration de points* via GraphQL et l’API REST.

<u>Résultats réels</u> :

GraphQL et l’API REST ne disposent pas de cette fonctionnalité.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
