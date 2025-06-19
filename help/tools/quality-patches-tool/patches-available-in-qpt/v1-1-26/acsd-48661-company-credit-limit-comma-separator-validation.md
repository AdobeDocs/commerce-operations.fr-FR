---
title: 'ACSD-48661 : problème de validation du séparateur de virgule de limite de crédit de l’entreprise'
description: Appliquez le correctif ACSD-48661 pour résoudre le problème d’Adobe Commerce où, lorsque la limite de crédit de la société est supérieure à 999, le séparateur par virgules empêche l’enregistrement de la société en raison d’une erreur de validation.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
exl-id: 7115226e-5942-4a8f-9dec-b1b6f665eef8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48661 : problème de validation du séparateur de virgule de limite de crédit de l’entreprise

Le correctif ACSD-48661 corrige le problème en raison duquel, lorsque la limite de crédit de l’entreprise est supérieure à 999, le séparateur par virgules empêche l’enregistrement de l’entreprise en raison d’une erreur de validation. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48661. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque la limite de crédit de l’entreprise est supérieure à 999, le séparateur à virgules empêche l’entreprise d’enregistrer en raison d’une erreur de validation.

<u>Procédure à suivre </u> :

1. Activez la fonction d’entreprise dans **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Créez une entreprise et ajoutez une limite de crédit supérieure à 999 sous l’onglet **[!UICONTROL Company Credit]** .
1. Sauve la société.
1. Modifiez la société et essayez de l’enregistrer à nouveau.

<u>Résultats attendus</u> :

Vous pouvez sauver la société sans fixer la limite de crédit. La virgule n’est pas prise en charge pour les champs de saisie des montants et des prix.

<u>Résultats réels</u> :

Vous ne pouvez pas enregistrer la société en raison d’une erreur de validation dans le champ *[!UICONTROL Credit Limit]*. Adobe Commerce ajoute automatiquement des séparateurs par virgules pour les limites de crédit, même si le champ [!UICONTROL Credit Limit] n’accepte pas les virgules.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
