---
title: 'ACSD-51358 : les mises à jour du planning sont manquantes'
description: Appliquez le correctif ACSD-51358 pour résoudre le problème d’Adobe Commerce où les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%
---
# ACSD-51358 : les mises à jour du planning sont manquantes

Le correctif ACSD-51358 corrige le problème où les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité. Ce correctif est disponible lorsque la version 1.1.35 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-51358. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les modifications apportées à la mise à jour planifiée sans date de fin entraînent la suppression d’autres mises à jour planifiées sur la même entité.

<u>Procédure à suivre </u> :

1. Créez un **[!UICONTROL scheduled update]** sans la date de fin (*mise à jour 1*).
1. Créez une nouvelle **[!UICONTROL scheduled update]** avec la même date de début que la première mise à jour, mais ajoutez le jour suivant et la date de fin (*mise à jour 2*).
1. Modifiez les **[!UICONTROL scheduled update]** créées à l’étape 1 (*mise à jour 1*) et enregistrez les modifications.

<u>Résultats attendus</u>

Le (*mise à jour 2*) doit rester dans la liste **[!UICONTROL schedule update]** lorsque (*mise à jour 1*) est modifié.

<u>Résultats réels</u>

(*mise à jour 2*) a été supprimé de la liste **[!UICONTROL schedule update]** lors de la modification de (*mise à jour 1*).

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
