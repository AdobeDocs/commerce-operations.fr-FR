---
title: 'ACSD-59366 : suppression des équipes dont les utilisateurs sont désactivés et qui ne sont pas visibles dans la liste des équipes'
description: Appliquez le correctif ACSD-59366 pour résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit lorsque vous tentez de supprimer une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366 : suppression des équipes dont les utilisateurs sont désactivés et qui ne sont pas visibles dans la liste des équipes

Le correctif ACSD-59366 corrige le problème où une erreur se produit lorsque vous tentez de supprimer une équipe qui contient des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-59366. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lorsque vous supprimez une équipe qui contient des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes.

<u>Conditions préalables</u> :

Les modules B2B d’Adobe Commerce sont installés et les sociétés sont activées.

<u>Procédure à suivre </u> :

1. Créez et connectez-vous avec un utilisateur d’entreprise.
1. Dans la structure de l’entreprise, créez une nouvelle équipe.
1. Sous la nouvelle équipe, créez un nouvel utilisateur.
1. Modifiez le nouvel utilisateur et désactivez.
1. Sélectionnez l’équipe et supprimez-la.

<u>Résultats attendus</u> :

L&#39;équipe compte un ou plusieurs utilisateurs inactifs. La suppression de l&#39;équipe annulera l&#39;affectation de ces utilisateurs. Vous trouverez des utilisateurs inactifs dans la section [!UICONTROL Company Users] .

<u>Résultats réels</u> :

Une erreur se produit lorsque vous tentez de supprimer une équipe dont l&#39;utilisateur est désactivé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
