---
title: 'MDVA-40311 : erreur « Clé de formulaire ou sécurité non valide » après la connexion à Admin si le chemin d’accès d’administration personnalisé est configuré'
description: 'Le correctif MDVA-40311 corrige le problème en raison duquel l’utilisateur administrateur reçoit un message d’erreur : *Clé de formulaire ou de sécurité non valide. Actualisez la page*, après vous être connecté à Admin si le chemin d’accès d’administration personnalisé est configuré et que la clé secrète est activée. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 est installé. L’ID du correctif est MDVA-40311. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.'
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-40311 : erreur « Clé de formulaire ou sécurité non valide » après la connexion à Admin si le chemin d’accès d’administration personnalisé est configuré

Le correctif MDVA-40311 corrige le problème en raison duquel l’utilisateur administrateur reçoit un message d’erreur : *Sécurité non valide ou clé de formulaire. Actualisez la page* après vous être connecté à Admin si le chemin d’accès administrateur personnalisé est configuré et la clé secrète activée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 est installé. L’ID du correctif est MDVA-40311. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur reçoit un message d’erreur : *Sécurité non valide ou clé de formulaire. Actualisez la page* après vous être connecté à Admin si le chemin d’accès administrateur personnalisé est configuré et la clé secrète activée.

<u>Procédure à suivre </u> :

* Connectez-vous en tant qu’administrateur en utilisant un nom d’utilisateur et un mot de passe valides.

<u>Résultats attendus</u> :

L’utilisateur peut se connecter sans message d’erreur.

<u>Résultats réels</u> :

*Clé de formulaire ou de sécurité non valide. Actualisez la page* un message d’erreur s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
