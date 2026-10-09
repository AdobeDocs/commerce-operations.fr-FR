---
title: 'ACSD-66179 : L''annulation d''une facture avec le type de paiement [!UICONTROL Not Capture] génère une page d''erreur 404'
description: Appliquez le correctif ACSD-66179 pour résoudre le problème d'Adobe Commerce où l'annulation d'une facture avec le type de paiement [!UICONTROL Not Capture] a généré une page d'erreur 404.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
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
source-wordcount: '359'
ht-degree: 0%
---
# ACSD-66179 : L&#39;annulation d&#39;une facture avec le type de paiement [!UICONTROL Not Capture] génère une page d&#39;erreur 404

Le correctif ACSD-66179 corrige le problème en raison duquel l’annulation d’une facture créée avec le type de paiement *[!UICONTROL Not Capture]* entraînait une page d’erreur 404. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66179. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;annulation d&#39;une facture créée avec le type de paiement *[!UICONTROL Not Capture]* génère une page d&#39;erreur 404.

<u>Procédure à suivre </u> :

1. Créez une commande à l&#39;aide d&#39;un mode de paiement tel que PayPal Express Checkout.
1. Créez une facture. Définissez **[!UICONTROL Amount]** sur *[!UICONTROL Not Capture]* et soumettez la facture.
1. Ouvrez la facture créée et sélectionnez **[!UICONTROL Cancel]**.

<u>Résultats attendus</u> :

1. La facture a été annulée.
1. Un message de réussite s’affiche : *Vous avez annulé la facture.*

<u>Résultats réels</u> :

Une page d’erreur 404 s’affiche : *Page introuvable.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
