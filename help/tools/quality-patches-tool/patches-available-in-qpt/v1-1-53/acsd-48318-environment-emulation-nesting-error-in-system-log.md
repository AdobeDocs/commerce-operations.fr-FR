---
title: 'ACSD-48318 : erreur d’imbrication de l’émulation d’environnement dans « system.log »'
description: Appliquez le correctif ACSD-48318 pour résoudre le problème d’Adobe Commerce où un message d’erreur *main.ERROR:Environment emulation nested is not allowed* apparaît dans « system.log » chaque fois qu’un e-mail de facture est envoyé.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# ACSD-48318 : erreur d’imbrication de l’émulation d’environnement dans `system.log`

Le correctif ACSD-48318 corrige le problème où un message d’erreur *l’imbrication d’émulation main.ERROR:Environment n’est pas autorisée* s’affiche dans `system.log` chaque fois qu’un e-mail de facture est envoyé. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48318. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le message d’erreur *L’imbrication de l’émulation de l’environnement n’est pas autorisée* s’affiche dans `system.log` chaque fois qu’un e-mail de facture est envoyé.

<u>Procédure à suivre </u> :

1. Passer une commande et générer une facture.
1. Ouvrez la facture depuis Admin et cliquez sur **[!UICONTROL Send Email]**.
1. Suivez la même étape pour *avoir* et *expédition* en cliquant sur **[!UICONTROL Send Email]**.

<u>Résultats attendus</u> :

Aucune erreur dans les `system.log`.

<u>Résultats réels</u> :

`system.log` est inondé avec *main.ERROR: l’imbrication de l’émulation d’environnement n’est pas autorisée* erreur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

[[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
