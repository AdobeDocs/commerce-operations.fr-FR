---
title: 'ACSD-60344 : duplication des e-mails de confirmation de commande lors de l’utilisation de [!UICONTROL Purchase Order] avec approbation automatique'
description: Appliquez le correctif ACSD-60344 pour résoudre le problème d’Adobe Commerce où des doublons d’e-mails de confirmation de commande sont envoyés lors de l’utilisation d’un [!UICONTROL Purchase Order] avec approbation automatique.
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344 : duplication des e-mails de confirmation de commande lors de l’utilisation de *[!UICONTROL Purchase Order]* avec approbation automatique

Le correctif ACSD-60344 corrige le problème d’envoi d’e-mails de confirmation de commande en double lors de l’utilisation d’un *[!UICONTROL Purchase Order]* avec approbation automatique. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-60344. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des e-mails de confirmation de commande en double sont envoyés lors de l’utilisation d’un *[!UICONTROL Purchase Order]* avec validation automatique.

<u>Conditions préalables</u>

Activez les modules et les *[!UICONTROL Purchase Order]* B2B.

<u>Procédure à suivre </u> :

1. Créez un compte d’entreprise et activez-en un *[!UICONTROL Purchase Order]*.
1. Créez un compte utilisateur standard et ajoutez-le au compte d’entreprise en tant qu’utilisateur d’entreprise.
1. Passer une commande à l’aide de ce compte.
1. Exécutez cron et vérifiez les e-mails.

<u>Résultats attendus</u> :

Un seul e-mail de confirmation de commande est reçu par commande.

<u>Résultats réels</u> :

Deux e-mails de confirmation de commande sont reçus.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
