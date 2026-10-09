---
title: 'MDVA-38929 : le total de la facture avec FPT est incorrect'
description: Le correctif MDVA-38929 résout le problème où la facture avec FPT affiche un total général incorrect lorsque la commande est payée avec un crédit de magasin. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID du correctif est MDVA-38929. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Invoices, Orders
role: Admin
exl-id: fd0ca2f3-c6bf-4f09-a0fa-c931df94158b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%
---
# MDVA-38929 : le total de la facture avec FPT est incorrect

Le correctif MDVA-38929 résout le problème où la facture avec FPT affiche un total général incorrect lorsque la commande est payée avec un crédit de magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID du correctif est MDVA-38929. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La facture avec FPT affiche un total général incorrect lorsque la commande est payée avec un crédit de magasin.

<u>Procédure à suivre </u> :

1. Créez un client et assurez-vous qu&#39;il dispose d&#39;un crédit de magasin suffisant pour couvrir la commande.
1. Activer FPT et ajouter FPT à un produit.
1. À partir du front-end, connectez-vous en tant que client(e) récemment créé(e).
1. Ajoutez le produit avec FPT au panier.
1. Effectuez la commande et payez avec le crédit de la boutique. Il devrait s&#39;agir d&#39;un ordre de paiement nul.
1. Accédez à Commandes et facturez manuellement la commande.
1. Vérifiez le total général de la facture.

<u>Résultats attendus</u> :

* Le total général de la facture est égal à zéro.
* Le montant total payé de la commande est égal à zéro.

<u>Résultats réels</u> :

* Le total général de la facture affiche toujours le montant FPT.
* Le total payé affiche toujours le montant FPT.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
