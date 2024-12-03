---
title: 'ACSD-61134 : [!UICONTROL Braintree Vault] méthode de paiement automatiquement désélectionnée dans le workflow de passage en caisse'
description: Appliquez le correctif ACSD-61134 pour résoudre le problème Adobe Commerce en raison duquel le mode de paiement *[!UICONTROL Braintree Vault]* est automatiquement désélectionné dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en désélectionnant la case à cocher *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
source-git-commit: 459f1e70464e4df04dc306ee403730798f0f9b9e
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134 : *[!UICONTROL Braintree Vault]* méthode de paiement automatiquement désélectionnée dans le workflow de passage en caisse

Le correctif ACSD-61134 corrige le problème en raison duquel le mode de paiement *[!UICONTROL Braintree Vault]* est automatiquement désélectionné dans le workflow de passage en caisse lorsqu’un acheteur met à jour son adresse de facturation en désélectionnant la case à cocher *[!UICONTROL My billing and shipping address are the same]* . Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.54 est installé. L’ID de correctif est ACSD-61134. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.7-beta1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p7

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le mode de paiement *[!UICONTROL Braintree Vault]* est automatiquement désélectionné dans le workflow de passage en caisse.

<u>Étapes à reproduire</u> :

1. Configurez le mode de paiement *[!DNL Braintree]* avec *[!UICONTROL Vault]* activé.
1. Extrayez et enregistrez une carte dans le *[!UICONTROL Vault]*.
1. Extraire un autre produit.
1. Sur la page *[!UICONTROL Shipping]*, ajoutez une nouvelle adresse de livraison afin de pouvoir sélectionner deux adresses.
1. Sur la page *[!UICONTROL Payment]*, sélectionnez votre mode de paiement et cliquez sur **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Résultats attendus</u> :

Le mode de paiement sélectionné reste sélectionné.

<u>Résultats réels</u> :

Le mode de paiement sélectionné est décoché.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.

