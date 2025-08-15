---
title: 'ACSD-61134 : [!UICONTROL Braintree Vault] mode de paiement automatiquement désélectionné dans le workflow de passage en caisse'
description: Appliquez le correctif ACSD-61134 pour résoudre le problème d’Adobe Commerce où le mode de paiement *[!UICONTROL Braintree Vault]* est automatiquement désélectionné dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en décochant la case *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134 : *[!UICONTROL Braintree Vault]* mode de paiement automatiquement désélectionné dans le workflow de passage en caisse

Le correctif ACSD-61134 corrige le problème où le mode de paiement *[!UICONTROL Braintree Vault]* est automatiquement désélectionné dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en décochant la case *[!UICONTROL My billing and shipping address are the same]*. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-61134. Notez que ce problème doit être corrigé dans la version 2.4.7-bêta1 d’Adobe Commerce.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

*[!UICONTROL Braintree Vault]* mode de paiement est automatiquement désélectionné dans le workflow de passage en caisse.

<u>Procédure à suivre </u> :

1. Configurez le mode de paiement *[!DNL Braintree]* avec le *[!UICONTROL Vault]* activé.
1. Extrayez et enregistrez une carte dans le *[!UICONTROL Vault]*.
1. Extrayez un autre produit.
1. Sur la page *[!UICONTROL Shipping]*, ajoutez une nouvelle adresse de livraison afin d&#39;avoir deux adresses à sélectionner.
1. Sur la page *[!UICONTROL Payment]*, sélectionnez votre mode de paiement et cliquez sur **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Résultats attendus</u> :

Le mode de paiement sélectionné reste sélectionné.

<u>Résultats réels</u> :

Le mode de paiement sélectionné est désélectionné.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
