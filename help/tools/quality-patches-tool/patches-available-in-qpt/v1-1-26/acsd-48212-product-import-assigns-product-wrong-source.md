---
title: 'ACSD-48212 : l’importation de produit affecte un produit à une source incorrecte'
description: Appliquez le correctif ACSD-48212 pour résoudre le problème d’Adobe Commerce où l’importation du produit affecte le produit à la mauvaise source.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212 : l’importation de produit affecte un produit à une source incorrecte

Le correctif ACSD-48212 corrige le problème en raison duquel l’importation du produit affecte le produit à une source incorrecte. Ce correctif est disponible lorsque la version 1.1.26 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48212. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation de produits affecte le produit à une source incorrecte.

<u>Procédure à suivre </u> :

1. Créez une source d&#39;inventaire secondaire.
1. Créez un produit avec l&#39;origine d&#39;inventaire par défaut uniquement.
1. Exportez le produit.
1. Exécutez `bin/magento cron:run`.
1. Ouvrez **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Sélectionnez le produit dans la grille.
1. Annulez l&#39;affectation du stock à l&#39;aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Attribuez la source secondaire à l’aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Supprimez le produit à l’aide du menu *[!UICONTROL mass action]* .
1. Exécutez `bin/magento cron:run`.
1. Importez le produit à l’aide du fichier CSV précédemment exporté.
1. Vérifiez l’affectation de la source.

<u>Résultats attendus</u> :

Le produit est affecté à la source par défaut uniquement.

<u>Résultats réels</u> :

Le produit est affecté à la fois à la source par défaut et à la source secondaire.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
