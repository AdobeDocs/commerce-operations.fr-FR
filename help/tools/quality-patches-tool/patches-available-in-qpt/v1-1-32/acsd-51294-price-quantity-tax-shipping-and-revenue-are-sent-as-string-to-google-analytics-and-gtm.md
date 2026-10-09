---
title: 'ACSD-51294 : prix, quantité, taxe, expédition, chiffre d''affaires envoyé en tant que chaîne à [!DNL Google Analytics] et GTM'
description: Appliquez le correctif ACSD-51294 pour résoudre le problème d’Adobe Commerce où le prix, la quantité, les taxes, l’expédition et le chiffre d’affaires sont envoyés sous forme de chaîne à [!DNL Google Analytics] et GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 99d2a311-2543-4007-99fd-6c34a2950773
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%
---
# ACSD-51294 : prix, quantité, taxe, expédition, chiffre d&#39;affaires envoyé en tant que chaîne à [!DNL Google Analytics] et GTM

Le correctif ACSD-51294 corrige le problème en raison duquel le prix, la quantité, la taxe, l’expédition et le chiffre d’affaires sont envoyés sous forme de chaîne à [!DNL Google Analytics] et GTM. Ce correctif est disponible lorsque la version 1.1.32 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-51294. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le prix, la quantité, la taxe, l&#39;expédition et le chiffre d&#39;affaires sont envoyés sous forme de chaîne à [!DNL Google Analytics] et GTM.

<u>Procédure à suivre </u> :

1. Configurez [!DNL Google Tag Manager] en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Créez un produit simple.
3. Effectuez le passage en caisse avec ce produit.
4. Vérifiez la variable JavaScript `dataLayer` sur la page de succès du passage en caisse.

<u>Résultats attendus</u>

Les valeurs de prix et de quantité sont numériques.

<u>Résultats réels</u>

Les valeurs de prix et de quantité sont des chaînes.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
