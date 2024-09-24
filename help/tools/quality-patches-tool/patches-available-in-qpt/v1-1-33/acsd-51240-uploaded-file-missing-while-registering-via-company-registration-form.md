---
title: 'ACSD-51240 : fichier téléchargé manquant lors de l’enregistrement via le formulaire d’enregistrement de la société'
description: Appliquez le correctif ACSD-51240 pour résoudre le problème Adobe Commerce en raison duquel le fichier téléchargé est manquant lors de l’enregistrement via le formulaire d’enregistrement de l’entreprise.
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240 : fichier téléchargé manquant lors de l’enregistrement via le formulaire d’enregistrement de la société

>[!NOTE]
>
>Ce correctif est remplacé par [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

Le correctif ACSD-51240 corrige le problème d’absence du fichier téléchargé lors de l’enregistrement via le formulaire d’enregistrement de la société. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 est installé. L’ID de correctif est ACSD-51240. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Problème

Le fichier téléchargé est manquant lors de l’enregistrement via le formulaire d’enregistrement de la société.

<u>Étapes à reproduire</u> :

1. Définissez **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Oui*.
1. Créez un nouvel attribut du client de type **[!UICONTROL File]**, définissez **[!UICONTROL Show in StoreFront]** = *Oui* et sélectionnez **[!UICONTROL all forms]**.
1. Créez une nouvelle société sur Storefront et chargez une image pour le nouvel attribut.
Ouvrez l’entreprise et l’utilisateur administrateur sur le storefront.

<u>Résultats attendus</u> :

Le fichier téléchargé s’affiche.

<u>Résultats réels</u> :

Le fichier chargé n’est pas affiché sur la page de la société ni sur la page du client administrateur dans [!UICONTROL Commerce Admin].

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
