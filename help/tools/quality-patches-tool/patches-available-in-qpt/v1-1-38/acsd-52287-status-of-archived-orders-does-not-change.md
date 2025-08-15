---
title: 'ACSD-52287 : le statut des commandes archivées ne change pas'
description: Appliquez le correctif ACSD-52287 pour résoudre le problème Adobe Commerce où le statut des commandes archivées ne change pas de *terminé* à *fermé* sur la grille après la soumission de l'avoir.
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287 : le statut des commandes archivées ne change pas

Le correctif ACSD-52287 corrige le problème où le statut des commandes archivées ne change pas de *terminées* à *clôturées* sur la grille après la soumission de l&#39;avoir. Ce correctif est disponible lorsque la version 1.1.38 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-52287. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le statut des commandes archivées ne passe pas de *terminées* à *clôturées* sur la grille après la soumission de l&#39;avoir.

<u>Procédure à suivre </u> :

1. Configurez *[!UICONTROL Asynchronous Indexing]*.
   * Dans la barre latérale d’administration, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Dans le panneau de gauche, développez la section **[!UICONTROL Advanced]** et choisissez **[!UICONTROL Developer]** en dessous.
   * Développez la section **[!UICONTROL Grid Settings]** .
   * Définissez *[!UICONTROL Asynchronous indexing]* sur *Oui*.
   * Cliquez sur **[!UICONTROL Save Config]**.
1. Configurez le *[!UICONTROL Order Archive]* .
   * Dans la barre latérale d’administration, accédez à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Dans le panneau de gauche, développez la section **[!UICONTROL Sales]** et choisissez **[!UICONTROL Sales]** en dessous.
   * Développez la section **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** .
   * Définissez *[!UICONTROL Enable Archiving]* sur *Oui* (laissez le reste des configurations par défaut).
   * Cliquez sur **[!UICONTROL Save Config]**.
1. Passer une commande sur le serveur frontal.
1. Exécutez le [!DNL cron] pour que l’ordre apparaisse dans le *[!UICONTROL Admin Order Grid]*.
1. Facturer et expédier la commande pour modifier le statut de la commande en *Terminé*.
1. Exécutez le [!DNL cron] pour mettre à jour le *[!UICONTROL Sales Order Grid]* avec le dernier statut de commande.
1. Archivez la commande.
1. Allez à la *[!UICONTROL Archived order grid]*.
1. Ouvrez la commande archivée et remboursez la commande hors ligne en créant un [!UICONTROL Credit Memo] pour effectuer le [!UICONTROL Order status] : *Fermé*.
1. Exécutez le [!DNL cron] plusieurs fois.
1. Vérifiez le *[!UICONTROL Archived order grid]* pour connaître le nouveau statut de la commande.

<u>Résultats attendus</u> :

La commande affiche la mention *Fermé*.

<u>Résultats réels</u> :

La commande affiche le statut *Terminé*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
