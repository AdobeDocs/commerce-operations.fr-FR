---
title: 'ACSD-63578 : cliquer sur l’icône [!UICONTROL Delete] dans [!UICONTROL Add to Order by SKU] ne supprime pas le SKU'
description: Appliquez le correctif ACSD-63578 pour résoudre le problème d’Adobe Commerce en raison duquel le fait de cliquer sur l’icône [!UICONTROL Delete] dans [!UICONTROL Add to Order by SKU] dans l’interface d’administration ne supprime pas le SKU.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578 : cliquer sur l’icône **[!UICONTROL Delete]** dans *[!UICONTROL Add to Order by SKU]* ne supprime pas le SKU

Le correctif ACSD-63578 corrige le problème en raison duquel le fait de cliquer sur l’icône **[!UICONTROL Delete]** dans *[!UICONTROL Add to Order by SKU]* dans l’Administration ne supprime pas le SKU. Ce correctif est disponible lorsque la version 1.1.58 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63578. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Cliquer sur l’icône **[!UICONTROL Delete]** dans *[!UICONTROL Add to Order by SKU]* dans l’Administration ne supprime pas le SKU de la commande.

<u>Procédure à suivre </u> :

1. Accédez à Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**, puis cliquez sur **[!UICONTROL Create New Order]**.
1. Choisissez un client.
1. Cliquez sur **[!UICONTROL Add to Order by SKU]**.
   * Saisissez un SKU.
   * Cliquez sur le bouton **[!UICONTROL Add another]** .
1. Cliquez sur l’icône **[!UICONTROL Delete]** .

<u>Résultats attendus</u> :

* Les produits sont ajoutés et supprimés d’une commande dans l’Admin.

<u>Résultats réels</u> :

* L’icône **[!UICONTROL Delete]** ne fonctionne pas.
* Une erreur s’est produite dans la console :

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
