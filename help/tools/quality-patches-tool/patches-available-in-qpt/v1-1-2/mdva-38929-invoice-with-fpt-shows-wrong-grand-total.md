---
title: 'MDVA-38929 : la facture avec FPT affiche un total incorrect'
description: Le correctif MDVA-38929 résout le problème en raison duquel la facture avec FPT affichait un total général incorrect lorsque la commande était payée avec le crédit de magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-38929. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Invoices, Orders
role: Admin
exl-id: fd0ca2f3-c6bf-4f09-a0fa-c931df94158b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-38929 : la facture avec FPT affiche un total incorrect

Le correctif MDVA-38929 résout le problème en raison duquel la facture avec FPT affichait un total général incorrect lorsque la commande était payée avec le crédit de magasin. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 est installé. L’ID de correctif est MDVA-38929. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La facture avec FPT affiche un total général incorrect lorsque la commande est payée avec le crédit de magasin.

<u>Étapes à reproduire</u> :

1. Créez un client et assurez-vous que le client dispose de suffisamment de crédit de magasin pour couvrir la commande.
1. Activez FPT et ajoutez FPT à un produit.
1. Depuis l’interface, connectez-vous en tant que client que vous venez de créer.
1. Ajoutez le produit avec FPT au panier.
1. Achat et paiement avec crédit de la boutique. Ça devrait être un ordre de paiement nul.
1. Accédez à Commandes et facturez manuellement la commande.
1. Vérifiez le total général de la facture.

<u>Résultats attendus</u> :

* Le total général de la facture est zéro.
* Le montant total payé de la commande est nul.

<u>Résultats réels</u> :

* Le total général de la facture indique toujours le montant du FPT.
* Le total payé affiche toujours le montant du FPT.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
