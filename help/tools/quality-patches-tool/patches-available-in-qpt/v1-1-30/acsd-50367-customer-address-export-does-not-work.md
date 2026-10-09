---
title: 'ACSD-50367 : l’exportation de l’adresse du client ne fonctionne pas avec l’attribut à sélection multiple'
description: Appliquez le correctif ACSD-50367 pour résoudre le problème d’Adobe Commerce en raison duquel l’exportation de l’adresse du client ne fonctionne pas lors de la création d’un attribut **`Adresse du client`** à sélection multiple sans valeurs.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%
---
# ACSD-50367 : l’exportation de l’adresse du client ne fonctionne pas

Le correctif ACSD-50367 corrige le problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lorsqu’un attribut **`Customer Address`** à sélection multiple sans valeurs est créé. Ce correctif est disponible lorsque la version 1.1.30 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-50367. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’exportation d’adresses client ne fonctionne pas lorsqu’un attribut **`Customer Address`** à sélection multiple sans valeurs est créé.

<u>Conditions préalables</u> :

Créez un client avec une adresse.

<u>Procédure à suivre </u> :

1. Créez un attribut de **`Customer Address`** à sélection multiple dans **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]**, puis sélectionnez **`Customer Address`** type d’entité.
1. Exportez les adresses du client. Vous verrez que rien n&#39;est exporté.
1. Supprimez l’attribut de **`Customer Address`** à sélection multiple et exportez à nouveau les adresses des clients. Cette fois, le fichier CSV des adresses est généré.

<u>Résultats attendus</u> :

Les adresses des clients peuvent être exportées sous la forme d’un fichier CSV lors de la création d’un attribut de **`Customer Address`** à sélection multiple.

<u>Résultats réels</u> :

Les adresses des clients ne peuvent pas être exportées sous la forme d’un fichier CSV lorsqu’un attribut de **`Customer Address`** à sélection multiple est créé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
