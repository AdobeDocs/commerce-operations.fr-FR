---
title: 'ACSD-57315 : une nouvelle transaction est créée  [!DNL PayPal Payflow Pro]  chaque fois que l’utilisateur clique sur le bouton de récupération'
description: Appliquez le correctif ACSD-57315 pour résoudre le problème d’Adobe Commerce où une nouvelle transaction est créée  [!DNL PayPal Payflow Pro]  chaque fois que l’utilisateur clique sur le bouton de récupération sur l’écran d’affichage des transactions du [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315 : une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération

Le correctif ACSD-57315 corrige le problème où une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération sur l’écran d’affichage des transactions du [!UICONTROL Admin]. Ce correctif est disponible lorsque la version 1.1.48 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-57315. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération sur l’écran d’affichage de la transaction dans le [!UICONTROL Admin].

<u>Procédure à suivre </u> :

1. Configurez [!DNL PayPal Payflow Pro].
1. Définissez la méthode de transaction sur *[!UICONTROL Sale]*.
1. Passez une commande avec *Carte de crédit*.
1. Ouvrez la transaction depuis [!UICONTROL Admin].
1. Cliquez sur le bouton **[!UICONTROL Fetch]**.
1. Vérifiez [!DNL PayPal] compte pour les transactions liées à la commande passée.

<u>Résultats attendus</u> :

Aucune nouvelle transaction de paiement n&#39;est créée.

<u>Résultats réels</u> :

Une nouvelle transaction de paiement est créée pour une commande qui a déjà été payée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
