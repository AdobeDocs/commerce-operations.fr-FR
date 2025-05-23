---
title: 'ACSD-48212 : l’importation de produit affecte le produit à une source incorrecte'
description: Appliquez le correctif ACSD-48212 pour résoudre le problème Adobe Commerce en raison duquel l’importation de produit affecte le produit à la mauvaise source.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212 : l’importation de produit affecte le produit à une source incorrecte

Le correctif ACSD-48212 corrige le problème en raison duquel l’importation de produit attribue le produit à la mauvaise source. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 est installé. L’ID de correctif est ACSD-48212. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation de produit affecte le produit à la mauvaise source.

<u>Étapes à reproduire</u> :

1. Créez une source de stock secondaire.
1. Créez un produit avec la source de stock par défaut uniquement.
1. Exportez le produit.
1. Exécutez `bin/magento cron:run`.
1. Ouvrez **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Sélectionnez le produit dans la grille.
1. Annulez l&#39;affectation du stock à l&#39;aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Affectez la source secondaire à l’aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Supprimez le produit à l’aide du menu *[!UICONTROL mass action]*.
1. Exécutez `bin/magento cron:run`.
1. Importez le produit à l’aide du fichier CSV précédemment exporté.
1. Vérifiez l’affectation de la source.

<u>Résultats attendus</u> :

Le produit est affecté à la source par défaut uniquement.

<u>Résultats réels</u> :

Le produit est affecté à la fois à la source par défaut et à la source secondaire.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
