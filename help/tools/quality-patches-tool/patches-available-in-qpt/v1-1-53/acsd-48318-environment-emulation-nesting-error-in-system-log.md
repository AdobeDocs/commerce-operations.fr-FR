---
title: 'ACSD-48318 : Erreur d’imbrication de l’émulation de l’environnement dans &grave;system.log&grave;'
description: Appliquez le correctif ACSD-48318 pour résoudre le problème Adobe Commerce en raison duquel un message d’erreur *main.ERROR:Environment emulation nested n’est pas autorisé* apparaît dans &grave;system.log&grave; chaque fois qu’un email de facture est envoyé.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318 : Erreur d’imbrication de l’émulation de l’environnement dans `system.log`

Le correctif ACSD-48318 corrige le problème en raison duquel un message d’erreur *main.ERROR:Environment emulation nested n’est pas autorisé* apparaît dans `system.log` chaque fois qu’un courrier électronique de facture est envoyé. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 est installé. L’ID de correctif est ACSD-48318. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le message d&#39;erreur *L&#39;imbrication de l&#39;émulation de l&#39;environnement n&#39;est pas autorisée* apparaît dans `system.log` chaque fois qu&#39;un email de facture est envoyé.

<u>Étapes à reproduire</u> :

1. passé une commande et générer une facture ;
1. Ouvrez la facture à partir d&#39;Admin et cliquez sur **[!UICONTROL Send Email]**.
1. Suivez la même étape pour *note de crédit* et *envoi* en cliquant sur **[!UICONTROL Send Email]**.

<u>Résultats attendus</u> :

Aucune erreur dans `system.log`.

<u>Résultats réels</u> :

`system.log` est inondé avec *main.ERROR : L’imbrication de l’émulation de l’environnement n’est pas autorisée* erreur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
