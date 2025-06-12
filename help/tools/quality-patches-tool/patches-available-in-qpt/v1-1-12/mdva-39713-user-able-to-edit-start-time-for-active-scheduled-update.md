---
title: 'MDVA-39713 : l’utilisateur peut modifier l’heure de début de la mise à jour planifiée active.'
description: Le correctif MDVA-39713 corrige le problème en raison duquel un utilisateur peut modifier l’heure de début d’une mise à jour planifiée active. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-39713. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713 : l’utilisateur peut modifier l’heure de début de la mise à jour planifiée active.

Le correctif MDVA-39713 corrige le problème en raison duquel un utilisateur peut modifier l’heure de début d’une mise à jour planifiée active. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-39713. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur peut modifier l’heure de début d’une mise à jour planifiée active.

<u>Procédure à suivre </u> :

1. Création de pages CMS.
1. Sélectionnez **Planifier une nouvelle mise à jour** et définissez la **Date de début** sur +1 minute.
1. Activez la mise à jour planifiée en exécutant la commande `bin/magento cron:run --group=staging` dans l’environnement local. Patientez quelques minutes et vérifiez si le planning est actif.
1. Une fois le planning actif, actualisez la page.
1. Cliquez sur **Afficher/Modifier** dans la section Modifications planifiées.
1. Modifiez l’heure en ajoutant +2 minutes et enregistrez la modification.
1. Enregistrez la page CMS.
1. Exécutez à nouveau la commande suivante : `bin/magento cron:run --group=staging`.
1. Cliquez sur **Afficher/Modifier** de la mise à jour planifiée.

<u>Résultats attendus</u> :

L’utilisateur ne peut pas modifier l’heure de début d’une mise à jour planifiée active.

<u>Résultats réels</u> :

L’utilisateur ou l’utilisatrice reçoit une erreur telle que *Item (Magento\Cms\Model\Page) avec le même ID « 11 » existe déjà.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
