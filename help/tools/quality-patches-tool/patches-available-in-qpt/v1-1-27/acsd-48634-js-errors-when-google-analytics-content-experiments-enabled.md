---
title: 'ACSD-48634: [!DNL JS] errors when [!DNL Google Analytics Content Experiments] enabled'
description: Appliquez le correctif ACSD-48634 pour corriger  [!DNL JS]  erreurs sur une page  [!DNL staging]  mise à jour lorsque  [!DNL Google Analytics Content Experiments]  est activé.
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634 : [!DNL JS] des erreurs lorsqu’[!DNL Google Analytics Content Experiments] est activé

Le correctif ACSD-48634 corrige [!DNL JS] erreurs sur une page de mise à jour [!DNL staging] lorsque [!DNL Google Analytics Content Experiments] est activé. Ce correctif est disponible lorsque la version 1.1.27 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-48634. Notez que le problème a été résolu dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL JS] erreurs se produisent sur une page de mise à jour de [!DNL staging] lorsque [!DNL Google Analytics Content Experiments] est activé.

<u>Procédure à suivre </u> :

1. Dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, créez un site web, un magasin et un **[!UICONTROL Store View]** supplémentaires. Assurez-vous que le **[!UICONTROL Store View]** est *[!UICONTROL Enabled]*.
1. Configurez **[!DNL Configure Google Analytics]** en accédant à **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** :
   * Pour les sites web **[!DNL Main]** et supplémentaires [!DNL scope] :
      * **[!UICONTROL Enabled]** : *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]** : *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]** : *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]** : *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]** : *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** les *[!UICONTROL Use Default]* pour les autres champs, mais ne les modifiez pas.
   * Pour **[!DNL Default Config]** [!DNL scope] :
      * **[!UICONTROL Enabled]** : *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]** : *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]** : *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]** : *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]** : *[!UICONTROL Yes]*
1. Désactivez **[!DNL Configure Google Analytics]** sur **[!DNL Default Config]** [!DNL scope] en modifiant **[!UICONTROL Enable]** de *[!UICONTROL Yes]* à *[!UICONTROL No]*. Veillez à ne rien changer d’autre !
1. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Créez et modifiez n’importe quel **[!UICONTROL category]** et ajoutez-y une mise à jour planifiée :
   * Tout nom, date de début dans le futur, date de fin dans le futur et toute modification dans les **[!UICONTROL category]** ([!UICONTROL For Example] : *[!UICONTROL disable category]*).
1. Enregistrez la mise à jour et recherchez les erreurs dans le [!DNL browser developer console].

<u>Résultats attendus</u> :

Aucune erreur de [!DNL JS] et les modifications apportées à la mise à jour [!DNL staging] sont enregistrées avec succès.

<u>Résultats réels</u> :

[!DNL JS] erreurs sont visibles dans la console, le formulaire est mal formé et le [!DNL spinner] n’est jamais désactivé après l’enregistrement.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
