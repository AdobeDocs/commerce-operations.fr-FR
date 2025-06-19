---
title: 'ACSD-49179 : le rapport Commandes affiche des montants incorrects pour différents magasins.'
description: Appliquez le correctif ACSD-49179 pour résoudre le problème d'Adobe Commerce où le rapport des commandes affiche des montants incorrects en cas de devises différentes pour différents magasins.
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179 : le rapport Commandes affiche des montants incorrects pour différents magasins

Le correctif ACSD-49179 corrige le problème où le rapport des commandes affiche des montants incorrects en cas de différentes devises pour différents magasins. Ce correctif est disponible lorsque la version 1.1.28 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-49179. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;état des commandes affiche des montants incorrects en cas de devises différentes pour différents magasins.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** et définissez [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Créez un site web, un magasin et une vue de magasin supplémentaires.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** et définissez :
   * Configuration par défaut :
      * Devise de base : USD
      * Devise d’affichage par défaut : USD
      * Devises autorisées : EUR, USD et THB (Baht thaïlandais)
   * Site Internet Principal :
      * Devise de base : EUR
      * Devise d&#39;affichage par défaut : EUR
      * Devises autorisées : EUR
   * Nouveau site Web supplémentaire :
      * Devise de base : THB (Baht thaïlandais)
      * Devise d’affichage par défaut : THB (Baht thaïlandais)
      * Devises autorisées : THB (Baht thaïlandais)
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** et définissez les taux de conversion vides pour le THB (définissez les taux sur 1,0000).
1. Créez un produit, affectez-le aux deux sites Web et passez une commande avec ce produit sur le site Web supplémentaire précédemment créé.
1. Assurez-vous que la commande a le statut *En cours de traitement* (facturez-la).
1. Sur le serveur principal, accédez à **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Cliquez sur l’avertissement **[!UICONTROL Yellow]** pour actualiser les statistiques.
1. Définissez la portée du rapport sur le site web supplémentaire créé précédemment et définissez le filtre comme suit :
   * [!UICONTROL Date Used] : [!UICONTROL Created]
   * [!UICONTROL Period] : [!UICONTROL Day]
   * [!UICONTROL From and To] : le jour même où la commande de test a été passée
   * [!UICONTROL Order Status] : [!UICONTROL Any]
   * [!UICONTROL Empty rows] : [!UICONTROL No]
   * [!UICONTROL Show Actual Values] : [!UICONTROL No]

<u>Résultats attendus</u> :

Le total des ventes indique le montant correct converti dans la devise du site web.

<u>Résultats réels</u> :

Le total est zéro.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
