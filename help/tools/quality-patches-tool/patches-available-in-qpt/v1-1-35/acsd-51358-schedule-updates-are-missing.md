---
title: 'ACSD-51358 : les mises à jour de planification sont manquantes'
description: Appliquez le correctif ACSD-51358 pour résoudre le problème Adobe Commerce en raison duquel les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.
feature: Staging
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51358 : les mises à jour de planification sont manquantes

Le correctif ACSD-51358 corrige le problème en raison duquel les modifications apportées à la mise à jour planifiée sans date de fin entraînaient la suppression d’autres mises à jour planifiées sur la même entité. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 est installé. L’ID de correctif est ACSD-51358. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.

<u>Étapes à reproduire</u> :

1. Créez un **[!UICONTROL scheduled update]** sans date de fin (*mettre à jour 1*).
1. Créez **[!UICONTROL scheduled update]** avec la même date de début que la première mise à jour, mais ajoutez le jour suivant et la date de fin (*mise à jour 2*).
1. Modifiez **[!UICONTROL scheduled update]** créé à l&#39;étape 1 (*mettre à jour 1*) et enregistrez les modifications.

<u>Résultats attendus</u>

La (*mise à jour 2*) doit rester dans la liste **[!UICONTROL schedule update]** lorsque (*mise à jour 1*) est modifiée.

<u>Résultats réels</u>

La (*mise à jour 2*) a été supprimée de la liste **[!UICONTROL schedule update]** lorsque (*mise à jour 1*) est modifiée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide [!DNL Quality Patches Tool].
