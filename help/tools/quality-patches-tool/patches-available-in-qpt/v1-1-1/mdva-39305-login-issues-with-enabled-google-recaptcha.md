---
title: 'MDVA-39305 : problème de connexion lié à l’activation de Google reCAPTCHA'
description: Appliquez le correctif MDVA-39305 pour résoudre le problème Adobe Commerce en raison duquel les clients enregistrés ne peuvent pas se connecter lorsque Google reCAPTCHA est activé.
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
source-git-commit: 007fcb1308ba2c5b42755ee4c4c2ca598eb0e62e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305 : problème de connexion lié à l’activation de Google reCAPTCHA

>[!NOTE]
>
>Ce correctif a été mis à jour et le dernier identifiant de correctif est MDVA-39305-V3. Le nouveau correctif est destiné aux versions 2.4.4, 2.4.5-p2 et 2.4.7 d’Adobe Commerce. Pour plus d’informations, reportez-vous à l’article du correctif [MDVA-39305-V3](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha).

Le correctif MDVA-39305 corrige le problème en raison duquel les clients enregistrés ne peuvent pas se connecter lorsque Google reCAPTCHA est activé. Ce correctif est disponible lorsque la version 1.1.1 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est MDVA-39305. Notez que le problème a été corrigé dans les versions 2.4.4 et 2.4.7 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur les infrastructures cloud 2.4.2-p1, 2.4.3-p3, 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1 - 2.4.3-p3, 2.4.4-p1 - 2.4.4-p5, 2.4.5 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients enregistrés ne peuvent pas se connecter à l’aide du reCAPTCHA Google activé.

<u>Procédure à suivre </u> :

1. Accédez à **Store** > **Configuration** > **Security** > **Storefront reCAPTCHA Google** et activez **reCAPTCHA Google**.
1. Accédez à **Frontend**.
1. Ouvrez la **Developer Tool Console** dans le navigateur.

<u>Résultats attendus</u> :

Aucun avertissement de CSP dans la console.

<u>Résultats réels</u> :

Avertissements de la CSP dans la console.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
