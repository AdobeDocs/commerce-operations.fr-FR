---
title: 'ACSD-61785 : mise à jour de l’attribut récompense_warning_notification impossible par mutation GraphQL et appels API REST'
description: Appliquez le correctif ACSD-61785 pour résoudre le problème Adobe Commerce en raison duquel la mise à jour de l’attribut "récompense_warning_notification" n’est pas possible par le biais d’une mutation GraphQL et d’appels API REST.
feature: REST, GraphQL, Rewards
role: Admin, Developer
source-git-commit: 87ce6004a632f860447d55c13c08f78533ab093e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785 : mise à jour de l’attribut récompense_warning_notification impossible par mutation GraphQL et appels API REST

Le correctif ACSD-61785 corrige le problème en raison duquel la mise à jour de l’attribut `reward_warning_notification` n’est pas possible par le biais d’une mutation GraphQL et d’appels d’API REST. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-61785. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour de l’attribut `reward_warning_notification` n’est pas possible par mutation GraphQL et appels API REST.

<u>Étapes à reproduire</u> :

1. Consultez la documentation/le schéma GraphQL et l’API REST pour *s’abonner aux mises à jour de la balance* et *s’abonner aux notifications d’expiration des points*.

<u>Résultats attendus</u> :

Il est possible de s’abonner aux *Mises à jour de l’équilibre des récompenses* et aux *notifications d’expiration de points* via l’API GraphQL et REST.

<u>Résultats réels</u> :

Cette fonctionnalité n’est pas disponible pour GraphQL et l’API REST.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
