---
title: 'ACSD-60811 : corrige la limitation dans la mise à jour du statut de commande vers des valeurs personnalisées'
description: Appliquez le correctif ACSD-60811 pour résoudre le problème d’Adobe Commerce où la mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est « traitement » ou « fraude ».
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811 : corrige la limitation dans la mise à jour du statut de commande vers des valeurs personnalisées

Le correctif ACSD-60811 corrige le problème en raison duquel la mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est « [!UICONTROL Processing] » ou « [!UICONTROL Suspected Fraud] ». Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-60811. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La mise à jour du statut de la commande avec une valeur ou un commentaire personnalisé n’est possible que si le statut actuel est *traitement* ou *fraude*. Le statut de la commande reste inchangé lorsqu’un nouveau statut est sélectionné et envoyé.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Order Status]** pour créer un statut de commande personnalisé dans le panneau d’administration.
1. Cliquez sur **[!UICONTROL Assign Status to State]** pour attribuer le statut personnalisé à l’état de commande.
1. Modifiez le statut de la commande à partir de la page vue de commande du panneau d’administration.

<u>Résultats attendus</u> :

L’utilisateur administrateur doit pouvoir modifier le statut de la commande en statut de commande personnalisé dans le panneau d’administration.

<u>Résultats réels</u> :

Le statut de la commande reste le même lorsqu’un nouveau statut de commande est sélectionné et envoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
