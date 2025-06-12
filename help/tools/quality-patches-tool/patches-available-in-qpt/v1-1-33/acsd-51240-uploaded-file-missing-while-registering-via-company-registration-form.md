---
title: 'ACSD-51240 : fichier chargé manquant lors de l''enregistrement via le formulaire d''enregistrement de l''entreprise'
description: Appliquez le correctif ACSD-51240 pour résoudre le problème d'Adobe Commerce où le fichier chargé manquait lors de l'enregistrement via le formulaire d'enregistrement de la société.
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240 : fichier chargé manquant lors de l&#39;enregistrement via le formulaire d&#39;enregistrement de l&#39;entreprise

>[!NOTE]
>
>Ce correctif est remplacé par [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

Le correctif ACSD-51240 corrige le problème en raison duquel le fichier chargé est manquant lors de l’enregistrement via le formulaire d’enregistrement de l’entreprise. Ce correctif est disponible lorsque la version 1.1.33 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-51240. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Problème

Le fichier chargé est manquant lors de l&#39;enregistrement via le formulaire d&#39;enregistrement de la société.

<u>Procédure à suivre </u> :

1. Définissez **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Oui*.
1. Créez un nouvel attribut client de type **[!UICONTROL File]**, définissez **[!UICONTROL Show in StoreFront]** = *Oui*, puis sélectionnez **[!UICONTROL all forms]**.
1. Créez une nouvelle entreprise sur le Storefront et chargez une image pour le nouvel attribut.
Ouvrez l’entreprise et l’utilisateur administrateur sur le Storefront.

<u>Résultats attendus</u> :

Le fichier chargé s’affiche.

<u>Résultats réels</u> :

Le fichier chargé ne s’affiche pas sur la page d’entreprise ni sur la page cliente de l’administrateur dans la [!UICONTROL Commerce Admin].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
