---
title: "MDVA-44887: 'Uncaught SyntaxError: Uncaught token const (erreur de syntaxe non interceptée : const de jetons inattendus) dans le panneau d’administration"
description: "Le correctif MDVA-44887 corrige le problème où l’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unpending token const* s’affiche dans le panneau d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID de correctif est MDVA-44887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5."
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-44887 : Erreur de syntaxe non interceptée : erreur &quot;Conteneur de jetons inattendu&quot; dans le panneau d’administration

Le correctif MDVA-44887 corrige le problème en raison duquel l’utilisateur administrateur ne pouvait cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unpending token const* s’affiche dans le panneau d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 est installé. L’ID de correctif est MDVA-44887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unpending token const* s’affiche dans le panneau d’administration.

<u>Étapes à reproduire</u> :

1. Activez le regroupement JS.
1. Minifiez les fichiers JS.
1. Connectez-vous au panneau d’administration de Commerce.

<u>Résultats attendus</u> :

L’utilisateur administrateur ne peut cliquer sur aucune option de menu. Une erreur s’est produite dans la console du navigateur : *Uncaught SyntaxError: Unpending token const*.

<u>Résultats réels</u> :

Un utilisateur administrateur peut accéder au panneau d’administration.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
