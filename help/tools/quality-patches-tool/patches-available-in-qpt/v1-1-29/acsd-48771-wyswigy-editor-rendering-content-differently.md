---
title: 'ACSD-48771 : l’éditeur WYSIWYG effectue un rendu du contenu différent'
description: Appliquez le correctif ACSD-48771 pour résoudre le problème d’Adobe Commerce en raison duquel l’éditeur de WYSIWYG effectue un rendu différent du contenu.
feature: Cache, Page Content
role: Admin
exl-id: 9480af54-800b-4802-b1a3-65d1a6e169ec
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%
---
# ACSD-48771 : l’éditeur WYSIWYG effectue un rendu du contenu différent

Le correctif ACSD-48771 corrige le problème en raison duquel l’éditeur WYSIWYG effectue un rendu du contenu différent. Ce correctif est disponible lorsque la version 1.1.29 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-48771. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’éditeur WYSIWYG effectue un rendu du contenu différent.

<u>Procédure à suivre </u> :

1. Accédez à l’Administration Adobe Commerce, créez une page avec une ligne à trois colonnes et enregistrez la page.
1. Mettez à jour Adobe Commerce vers l’une des dernières versions.
1. Définissez [!DNL Chrome] navigateur pour désactiver le cache et la vitesse sur *3G rapide*.
1. Accédez à nouveau à la page d’édition et actualisez-la jusqu’à ce que les colonnes deviennent des lignes.
1. Enregistrez la page lorsque les colonnes se trouvent dans les lignes.

<u>Résultats attendus</u> :

Le générateur de pages d’administration ne doit pas afficher les colonnes dans les lignes.

<u>Résultats réels</u> :

Les colonnes apparaissent dans différentes lignes.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
