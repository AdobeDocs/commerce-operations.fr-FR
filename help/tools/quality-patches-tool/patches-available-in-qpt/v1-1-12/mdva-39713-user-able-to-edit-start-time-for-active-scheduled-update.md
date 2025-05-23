---
title: 'MDVA-39713 : l’utilisateur peut modifier l’heure de début de la mise à jour planifiée active'
description: Le correctif MDVA-39713 corrige le problème lorsqu’un utilisateur est en mesure de modifier l’heure de début d’une mise à jour planifiée active. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-39713. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713 : l’utilisateur peut modifier l’heure de début de la mise à jour planifiée active

Le correctif MDVA-39713 corrige le problème lorsqu’un utilisateur est en mesure de modifier l’heure de début d’une mise à jour planifiée active. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID de correctif est MDVA-39713. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur peut modifier l’heure de début d’une mise à jour planifiée active.

<u>Étapes à reproduire</u> :

1. Créez de nouvelles pages CMS.
1. Sélectionnez **Planifier une nouvelle mise à jour** et définissez la **Date de début** sur la valeur actuelle de +1 minute.
1. Activez la Mise à jour planifiée en exécutant la commande `bin/magento cron:run --group=staging` dans un environnement local. Patientez quelques minutes et vérifiez si le planning est actif.
1. Une fois que la planification est active, actualisez la page.
1. Cliquez sur **Afficher/Modifier** dans la section Modifications planifiées .
1. Modifiez l’heure en ajoutant +2 minutes et enregistrez la modification.
1. Enregistrez la page CMS.
1. Exécutez à nouveau la commande suivante : `bin/magento cron:run --group=staging`.
1. Cliquez sur **Afficher/Modifier** de la mise à jour planifiée.

<u>Résultats attendus</u> :

L’utilisateur ne peut pas modifier l’heure de début d’une mise à jour planifiée active.

<u>Résultats réels</u> :

L&#39;utilisateur obtient une erreur du type *Item (Magento\Cms\Model\Page) avec le même ID &quot;11&quot; existe déjà.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
