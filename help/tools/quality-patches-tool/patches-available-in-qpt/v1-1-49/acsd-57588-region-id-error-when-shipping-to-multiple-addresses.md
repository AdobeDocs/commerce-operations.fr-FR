---
title: 'ACSD-57588 : erreur lors du traitement de l’ID de région lors de l’expédition vers plusieurs adresses'
description: Appliquez le correctif ACSD-57588 pour résoudre le problème d’Adobe Commerce en raison duquel l’envoi d’une commande à plusieurs adresses déclenche une erreur lors du traitement de l’ID de région.
feature: Orders, Shipping/Delivery
role: Admin, Developer
exl-id: 9a455d32-47d3-4d29-b12e-068bbee98f89
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%
---
# ACSD-57588 : erreur lors du traitement de l’ID de région lors de l’expédition vers plusieurs adresses

Le correctif ACSD-57588 corrige le problème en raison duquel l’envoi d’une commande à plusieurs adresses déclenche une erreur lors du traitement de l’ID de région. Ce correctif est disponible lorsque la version 1.1.49 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-57588. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Erreur déclenchée lors du traitement de l’identifiant de région lors de l’expédition vers plusieurs adresses.

<u>Procédure à suivre </u> :

1. Configurez le mode de paiement [!DNL Braintree].
1. Connectez-vous en tant que client sur le storefront.
1. Ajoutez un produit au panier et passez à l’affichage et à la modification du panier.
1. Ajoutez plusieurs adresses *(par exemple, Royaume-Uni, États-Unis, Californie)* pendant le processus de passage en caisse et vérifiez la commande.
1. Sur la page de passage en caisse, sélectionnez l’option de paiement par carte de crédit, saisissez les informations d’identification nécessaires et passez la commande.

<u>Résultats attendus</u> :

La commande peut être passée.

<u>Résultats réels</u> :

La commande n’est pas passée.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
