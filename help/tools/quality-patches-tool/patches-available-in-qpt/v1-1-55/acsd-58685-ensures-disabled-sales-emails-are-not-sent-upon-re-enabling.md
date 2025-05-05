---
title: 'ACSD-58685 : Les emails de vente désactivés sont envoyés lors de la réactivation.'
description: Appliquez le correctif ACSD-58685 pour résoudre le problème Adobe Commerce en raison duquel les courriers électroniques de vente démarrés alors que la communication par courrier électronique est désactivée sont envoyés une fois la communication par courrier électronique réactivée.
feature: Configuration
role: Admin, Developer
source-git-commit: db495f2dbf307f9da42b6dc4fc7bed1e6af1d307
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685 : Les emails de vente désactivés sont envoyés lors de la réactivation.

Le correctif ACSD-58685 corrige le problème en raison duquel les courriers électroniques de vente démarrés alors que la communication par courrier électronique est désactivée étaient envoyés une fois la communication par courrier électronique réactivée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-58685. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les courriers électroniques de vente démarrés lorsque la communication par courrier électronique est désactivée sont envoyés une fois que la communication par courrier électronique est réactivée.

<u>Étapes à reproduire</u> :

1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** et définissez **[!UICONTROL Disable Email Communications]** sur *[!UICONTROL No]*.
1. Accédez à **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** et définissez **[!UICONTROL Asynchronous Sending]** sur *[!UICONTROL Yes]*.
1. Effacez le cache de configuration.
1. passé une commande ;
1. Activez la communication par courrier électronique.
1. Faites une autre commande.
1. Lancez le cron.

<u>Résultats attendus</u> :

Seul le courrier électronique correspondant à la deuxième commande est envoyé.

<u>Résultats réels</u> :

Les emails pour la première et la deuxième commande sont envoyés.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
