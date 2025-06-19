---
title: 'ACSD-51294 : prix, quantité, taxe, expédition, chiffre d’affaires envoyé en tant que chaîne à et  [!DNL Google Analytics] '
description: Appliquez le correctif ACSD-51294 pour résoudre le problème d’Adobe Commerce où le prix, la quantité, les taxes, l’expédition et le chiffre d’affaires sont envoyés sous forme de chaîne à et  [!DNL Google Analytics]  GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 99d2a311-2543-4007-99fd-6c34a2950773
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
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
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

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
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le guide de [!DNL Quality Patches Tool].
