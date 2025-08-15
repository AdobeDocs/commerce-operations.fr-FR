---
title: 'MDVA-39229 : erreur après la mise à jour de la règle de catalogue - Heure de début de la mise à jour intermédiaire'
description: Le correctif MDVA-39229 corrige le problème où les utilisateurs et utilisatrices obtiennent une erreur après la mise à jour de l’heure de début de la mise à jour de l’évaluation des règles de catalogue. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-39229. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229 : erreur après la mise à jour de la règle de catalogue - Heure de début de la mise à jour intermédiaire

Le correctif MDVA-39229 corrige le problème où les utilisateurs et utilisatrices obtiennent une erreur après la mise à jour de l’heure de début de la mise à jour de l’évaluation des règles de catalogue. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 est installé. L’ID du correctif est MDVA-39229. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs reçoivent une erreur après la mise à jour de l’heure de début de la mise à jour de l’évaluation des règles de catalogue.

<u>Procédure à suivre </u> :

1. Créez une règle de prix de catalogue.
1. Créez et exécutez toute mise à jour d’évaluation.
1. Exécutez la requête et vérifiez que l’indicateur Évaluation a été créé.


   `select * from flag;`


1. Créez une mise à jour d’évaluation pour démarrer au bout de cinq minutes.
1. Ouvrez **Contenu** > **Évaluation** > **Tableau de bord** > **Nouvelle mise à jour** et retardez l’heure de début d’une minute.
1. Attends six minutes.
1. Exécutez cron.

<u>Résultats attendus</u> :

L’heure de début de la mise à jour est modifiée et la mise à jour est appliquée. L’ancienne mise à jour est supprimée de la table des `staging_update`.

<u>Résultats réels</u> :

L’erreur suivante s’affiche pour les utilisateurs :

*report.ERROR: Une erreur s’est produite lors de la tâche cron staging_synchronize_entities_period : la mise à jour active ne peut pas être supprimée.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr).
