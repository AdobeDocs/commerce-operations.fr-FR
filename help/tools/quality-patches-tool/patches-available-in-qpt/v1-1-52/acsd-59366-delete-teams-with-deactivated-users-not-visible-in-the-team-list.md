---
title: "ACSD-59366 : Suppression des équipes dont les utilisateurs désactivés ne sont pas visibles dans la liste des équipes"
description: Appliquez le correctif ACSD-59366 pour corriger le problème Adobe Commerce qui se produit lorsqu’une erreur se produit lorsque vous tentez de supprimer une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste de l’équipe.
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366 : suppression des équipes dont les utilisateurs désactivés ne sont pas visibles dans la liste des équipes

Le correctif ACSD-59366 corrige le problème d’erreur qui se produit lorsque vous tentez de supprimer une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste de l’équipe. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 est installé. L’ID de correctif est ACSD-59366. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur se produit lorsque vous supprimez une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste des membres de l’équipe.

<u>Conditions préalables</u> :

Les modules Adobe Commerce B2B sont installés et les entreprises sont activées.

<u>Étapes à reproduire</u> :

1. Créez et connectez-vous avec un utilisateur de l’entreprise.
1. Sous la structure de l’entreprise, créez une équipe.
1. Sous la nouvelle équipe, créez un utilisateur.
1. Modifiez le nouvel utilisateur et désactivez-le.
1. Sélectionnez l’équipe et supprimez-la.

<u>Résultats attendus</u> :

L’équipe compte un ou plusieurs utilisateurs inactifs. La suppression de l’équipe annule l’affectation de ces utilisateurs. Vous pouvez trouver les utilisateurs inactifs dans la section [!UICONTROL Company Users] .

<u>Résultats réels</u> :

Une erreur se produit lorsque vous tentez de supprimer une équipe avec un utilisateur désactivé.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.


