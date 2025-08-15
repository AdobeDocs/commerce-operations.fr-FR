---
title: 'ACSD-61133 : le cron « sales_clean_quotes » supprime les devis des commandes fournisseur non approuvées'
description: Appliquez le correctif ACSD-61133 pour résoudre le problème d’Adobe Commerce où « sales_clean_quotes » cron supprime les devis des commandes fournisseur non approuvées.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133 : `sales_clean_quotes` cron supprime les devis des commandes fournisseur non approuvées

Le correctif ACSD-61133 corrige le problème où le cron `sales_clean_quotes` supprime les devis des commandes fournisseur non approuvées. Ce correctif est disponible lorsque la version 1.1.53 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-61133. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 et 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`sales_clean_quotes` cron supprime les devis des commandes fournisseur non approuvées. Le bon de commande *[B2B]* ne peut pas être converti en commande du devis associé au bon de commande car le cron le supprime.

<u>Conditions préalables</u> :

Les modules Adobe Commerce [!UICONTROL B2B] sont installés et activés.

<u>Procédure à suivre </u> :

1. Activez la fonctionnalité *[!UICONTROL B2B Purchase Order]*.
1. Créez une entreprise.
1. Créez un *[!UICONTROL Purchase Order]*.
1. Patientez jusqu’à l’expiration du devis et sa suppression par le cron. La période d’expiration du devis peut être définie avec **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**.
1. Convertissez les *[!UICONTROL Purchase Order]* en ordre via *[!UICONTROL My Purchase Order in Customer Dashboard]* ou avec [!DNL GraphQL] mutation `placeOrderForPurchaseOrder`.

<u>Résultats attendus</u> :

Le devis associé au *[!UICONTROL Purchase Order]* actif n&#39;est pas supprimé comme expiré par le cron. La commande est placée avec succès sur le storefront ou via [!DNL GraphQL].

<u>Résultats réels</u> :

La commande n’est pas passée et une erreur s’affiche sur le storefront ou est renvoyée dans la réponse [!DNL GraphQL].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
