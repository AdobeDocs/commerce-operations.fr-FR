---
title: 'MDVA-44887 : erreur « Uncaught SyntaxError: Unexpected token const » dans le panneau d’administration'
description: 'Le correctif MDVA-44887 corrige le problème en raison duquel l’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unexpected token const* s’affiche dans le panneau d’administration. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID du correctif est MDVA-44887. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.'
feature: Admin Workspace, Orders
role: Admin
exl-id: d8cc03c3-35a0-4f00-8ec3-1ba3e100f7ca
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-44887 : erreur « Uncaught SyntaxError: Unexpected token const » dans le panneau d’administration

Le correctif MDVA-44887 corrige le problème en raison duquel l’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unexpected token const* s’affiche dans le panneau d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID du correctif est MDVA-44887. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unexpected token const* s’affiche dans le panneau d’administration.

<u>Procédure à suivre </u> :

1. Activez le regroupement JS.
1. Minimisez les fichiers JS.
1. Connectez-vous au panneau d’administration de Commerce.

<u>Résultats attendus</u> :

L’utilisateur administrateur ne peut cliquer sur aucune option de menu. Une erreur s’est produite dans la console du navigateur : *Syntaxe non interceptéeError : const de jeton inattendue*.

<u>Résultats réels</u> :

Le panneau d’administration est accessible aux utilisateurs administrateurs.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
