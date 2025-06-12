---
title: 'MDVA-41628 : les utilisateurs administrateurs restreints ont accès à de nouvelles ressources'
description: Le correctif MDVA-41628 corrige le problème en raison duquel les utilisateurs administrateurs restreints peuvent accéder aux nouvelles ressources lorsque de nouveaux modules sont ajoutés. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-41628. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Admin Workspace
role: Admin
exl-id: 774a4329-fa1f-4cca-aa97-1b8ef03c11d1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-41628 : les utilisateurs administrateurs restreints ont accès à de nouvelles ressources

Le correctif MDVA-41628 corrige le problème en raison duquel les utilisateurs administrateurs restreints peuvent accéder aux nouvelles ressources lorsque de nouveaux modules sont ajoutés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 est installé. L’ID du correctif est MDVA-41628. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs avec accès limité peuvent accéder aux nouvelles ressources lorsque de nouveaux modules sont ajoutés.

<u>Procédure à suivre </u> :

1. Créez un rôle d’utilisateur administrateur avec des ressources limitées.
1. Créez un utilisateur administrateur sous le rôle créé à l’étape 1.
1. Installez et activez le module personnalisé qui crée un nouvel ensemble d’éléments de menu avec des ressources ACL.
1. Connectez-vous à l’aide de l’utilisateur administrateur nouvellement créé.

<u>Résultats attendus</u> :

L’utilisateur administrateur disposant d’un accès restreint ne peut pas accéder aux éléments de menu nouvellement créés.

<u>Résultats réels</u> :

L’utilisateur administrateur restreint peut accéder aux nouveaux éléments de menu, même si les nouvelles ressources ne sont pas affectées au rôle utilisateur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
