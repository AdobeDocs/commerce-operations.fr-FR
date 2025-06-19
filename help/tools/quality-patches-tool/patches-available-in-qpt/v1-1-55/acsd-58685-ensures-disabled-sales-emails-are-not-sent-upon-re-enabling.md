---
title: 'ACSD-58685 : les e-mails de vente désactivés sont envoyés lors de la réactivation'
description: Appliquez le correctif ACSD-58685 pour résoudre le problème d’Adobe Commerce où les e-mails de vente déclenchés alors que la communication par e-mail est désactivée sont envoyés une fois que la communication par e-mail est réactivée.
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685 : les e-mails de vente désactivés sont envoyés lors de la réactivation

Le correctif ACSD-58685 corrige le problème où les e-mails de vente déclenchés alors que la communication par e-mail est désactivée sont envoyés une fois que la communication par e-mail est réactivée. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-58685. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les e-mails de vente initiés alors que la communication par e-mail est désactivée sont envoyés une fois que la communication par e-mail est réactivée.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** et définissez **[!UICONTROL Disable Email Communications]** sur *[!UICONTROL No]*.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** et définissez **[!UICONTROL Asynchronous Sending]** sur *[!UICONTROL Yes]*.
1. Effacez le cache de configuration.
1. Passer une commande.
1. Activez la communication par e-mail.
1. Passer une autre commande.
1. Exécutez le cron.

<u>Résultats attendus</u> :

Seul l’e-mail de la deuxième commande est envoyé.

<u>Résultats réels</u> :

Des e-mails sont envoyés pour la première et la deuxième commande.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

[[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
