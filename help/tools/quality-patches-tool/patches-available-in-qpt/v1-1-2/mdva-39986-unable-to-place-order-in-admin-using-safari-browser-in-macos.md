---
title: 'MDVA-39986 : impossible de passer des commandes dans l’administration dans le navigateur Safari sur macOS'
description: Le correctif MDVA-39986 corrige le problème en raison duquel les utilisateurs ne peuvent pas passer de commandes dans l’administration à l’aide du navigateur Safari sur macOS. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-39986. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.
feature: Admin Workspace, Orders
role: Admin
exl-id: bd4e72fe-278d-40ae-98d3-1eeca0a0e70c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# MDVA-39986 : impossible de passer des commandes dans l’administration dans le navigateur Safari sur macOS

Le correctif MDVA-39986 corrige le problème en raison duquel les utilisateurs ne peuvent pas passer de commandes dans l’administration à l’aide du navigateur Safari sur macOS. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-39986. Notez que le problème a été résolu dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs ne peuvent pas passer de commande dans l’administration à l’aide du navigateur Safari sur macOS.

<u>Procédure à suivre </u> :

1. Passer une commande.
1. Accédez à l’administration à l’aide du navigateur Safari sur macOS et ouvrez la commande que vous avez créée précédemment.
1. Cliquez sur **Réorganiser**.
1. Essayez de mettre à jour **quantité de produit**.

<u>Résultats attendus</u> :

Les utilisateurs doivent pouvoir effectuer une nouvelle commande à l’aide du navigateur Safari sur macOS.

<u>Résultats réels</u> :

Les utilisateurs obtiennent une erreur JS où le rouet tourne sans fin.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
