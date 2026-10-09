---
title: 'ACSD-63793 : les processus d’importation interfèrent entre eux dans différents onglets du navigateur'
description: Appliquez le correctif ACSD-63793 pour résoudre le problème d’Adobe Commerce où les processus d’importation interfèrent les uns avec les autres dans différents onglets du navigateur.
feature: Data Import/Export
role: Admin, Developer
exl-id: f6bed4c4-5ea2-47e7-97fa-d7717470297f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
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
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-63793 : les processus d’importation interfèrent entre eux dans différents onglets du navigateur

Le correctif ACSD-63793 corrige le problème d’interférence des processus d’importation dans les différents onglets du navigateur. Ce correctif est disponible lorsque la version 1.1.59 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63793. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’importation de données par le biais de l’interface utilisateur d’administration interfère avec une autre importation, ce qui entraîne le traitement des données d’une importation dans une autre.

<u>Procédure à suivre </u> :

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.
1. Définissez **[!UICONTROL Entity Type]** sur *[!UICONTROL Customers and Addresses] (fichier unique)*.
1. Définissez **[!UICONTROL Import Behavior]** sur *[!UICONTROL Add/Update]*.
1. Sélectionnez un fichier valide à importer.
1. Cliquez sur le bouton **[!UICONTROL Check Data]** .
1. Gardez cet onglet ouvert.
1. Ouvrez un nouvel onglet et répétez les étapes avec un fichier contenant des données non valides (par exemple, deux e-mails identiques pour des clients différents).
1. Revenez au premier onglet.
1. Cliquez sur le bouton **[!UICONTROL Import]** en bas de la page.

<u>Résultats attendus</u> :

Le processus d’importation ne doit pas interférer les uns avec les autres.

<u>Résultats réels</u> :

Le processus d’importation est terminé et le fichier de rapport peut être téléchargé. Elle indique une erreur dans la deuxième ligne et les données d’une autre importation sont traitées, même si la validation initiale a réussi sans erreur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
