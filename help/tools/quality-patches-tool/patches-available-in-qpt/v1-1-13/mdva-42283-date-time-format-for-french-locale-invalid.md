---
title: 'MDVA-42283 : le format de date et d’heure des paramètres régionaux français n’est pas valide'
description: Le correctif MDVA-42283 corrige le problème en raison duquel le format de date et d’heure dans la grille de commande d’administration pour les paramètres régionaux français n’est pas valide. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-42283. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: ed99519d-03e2-444b-9cd1-e5c6e6d2ac2d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42283 : le format de date et d’heure des paramètres régionaux français n’est pas valide

Le correctif MDVA-42283 corrige le problème en raison duquel le format de date et d’heure dans la grille de commande d’administration pour les paramètres régionaux français n’est pas valide. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-42283. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le format de date et d’heure dans la grille de commande d’administration pour les paramètres régionaux français n’est pas valide.

<u>Procédure à suivre </u> :

1. Créez une commande, un client, une page CMS ou un bloc CMS.
1. Accédez à **Admin** > **Paramètres du compte** et définissez les paramètres régionaux de l’interface pour admin sur **Français (Canada)**/**français (Canada)(fr_CA)** ou **Portugais brésilien (pt_BR)**.
1. Observez la valeur dans la colonne de date pour toute commande, expédition, avoir, client, page CMS ou grille de bloc CMS.

<u>Résultats attendus</u> :

La date est au format qui apparaît sur la page de modification réelle de l’entité.

<u>Résultats réels</u> :

La valeur date-heure est incorrecte.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
