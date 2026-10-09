---
title: 'ACP2E-3918 : échec de passage en caisse pour les clients de l’entreprise qui utilisent le retrait en magasin'
description: Appliquez le correctif ACP2E-3918 pour résoudre le problème d’Adobe Commerce en raison duquel le passage en caisse échoue pour les clients de la société connectés qui utilisent le retrait en magasin sans adresse de facturation par défaut.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '384'
ht-degree: 0%
---
# ACP2E-3918 : échec de passage en caisse pour les clients de l’entreprise qui utilisent le retrait en magasin

Le correctif ACP2E-3918 corrige le problème en raison duquel le passage en caisse échouait pour les clients de l’entreprise connectés qui utilisaient le retrait en magasin sans adresse de facturation par défaut. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3918. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le passage en caisse échoue lorsqu’un client d’entreprise connecté sans adresse par défaut tente de passer une commande fournisseur à l’aide du retrait en magasin.

<u>Procédure à suivre </u> :

1. Activez **[!UICONTROL Purchase Orders]**.
1. Créez une **[!UICONTROL Company]** et activez-la **[!UICONTROL Purchase Orders]**.
1. Créez un **[!UICONTROL Company User]** sans les adresses enregistrées.
1. Activez le mode d’expédition **[!UICONTROL In-Store Delivery]**.
1. Ajoutez une source d’inventaire.
1. Ajoutez un stock d’inventaire.
1. Affectez un stock à un produit.
1. Sur le serveur frontal, connectez-vous en tant qu’utilisateur de l’entreprise.
1. Ajoutez des produits aux **[!UICONTROL Cart]**.
1. Passer en caisse.
1. Sélectionnez **[!UICONTROL In-Store Pick Up]** à l’étape d’expédition.
1. Procédez au paiement.

<u>Résultats attendus</u> :

L’étape de paiement doit se charger correctement lors du passage en caisse et aucune erreur ne doit apparaître dans la console du navigateur.

<u>Résultats réels</u> :

L’étape de paiement ne se charge pas et la console du navigateur affiche l’erreur JavaScript suivante :

```text
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
