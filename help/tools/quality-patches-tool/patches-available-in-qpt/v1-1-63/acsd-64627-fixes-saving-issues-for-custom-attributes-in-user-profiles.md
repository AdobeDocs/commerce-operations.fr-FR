---
title: 'ACSD-64627 : impossible d’enregistrer les attributs du client personnalisé dans [!UICONTROL Company Structure]'
description: Appliquez le correctif ACSD-64627 pour résoudre le problème d’Adobe Commerce en raison duquel les attributs personnalisés du client ne peuvent pas être enregistrés lors de l’ajout ou de la modification d’utilisateurs dans [!UICONTROL Company Structure].
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627 : impossible d’enregistrer les attributs du client personnalisé dans [!UICONTROL Company Structure]

Le correctif ACSD-64627 corrige le problème en raison duquel les attributs personnalisés du client ne peuvent pas être enregistrés lors de l’ajout ou de la modification d’utilisateurs dans la page **[!UICONTROL Company Structure]**. Ce correctif est disponible lorsque la version 1.1.63 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64627. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les attributs personnalisés du client ne sont pas enregistrés lors de l’ajout ou de la modification d’utilisateurs sur la page **[!UICONTROL Company Structure]**.

<u>Procédure à suivre </u> :

1. Installez une instance Adobe Commerce avec les fonctionnalités B2B activées.
1. Créez un attribut client nommé *custom_upload* avec le **[!UICONTROL Input Type]** défini sur *[!UICONTROL File (attachment)]*.
1. Créez un autre attribut client nommé *image_attachment* avec le **[!UICONTROL Input Type]** défini sur *[!UICONTROL Image File]*.
1. Définissez **[!UICONTROL Show on Storefront]** sur *Oui* pour que les deux attributs soient visibles sur le storefront. Sélectionner tous les formulaires :
   * Enregistrement des clients
   * Modification du compte client
   * Extraction admin
1. Créer et activer une nouvelle entreprise.
1. Connectez-vous au storefront en tant qu’administrateur de la société.
1. Accédez à **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** ou **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**.
1. Cliquez sur **[!UICONTROL Add New User]**.
1. Cliquez sur **[!UICONTROL Upload]** pour l’attribut *custom_upload*.
1. Cliquez sur **[!UICONTROL Select file]** pour l’attribut *image_attachment*.

<u>Résultats attendus</u> :

L’explorateur de fichiers s’ouvre pour les deux attributs. Lors de l’enregistrement, les valeurs sont stockées et les fichiers sont chargés correctement.

<u>Résultats réels</u> :

Les boutons ne répondent pas. Aucun explorateur de fichiers ne s’ouvre ou les données ne sont enregistrées.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
