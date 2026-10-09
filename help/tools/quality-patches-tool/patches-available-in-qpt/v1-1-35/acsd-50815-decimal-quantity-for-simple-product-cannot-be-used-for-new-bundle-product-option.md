---
title: 'ACSD-50815 : la quantité décimale pour un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé'
description: Appliquez le correctif ACSD-50815 pour résoudre le problème d’Adobe Commerce où la quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.
feature: Products
role: Admin
exl-id: 5cd69abe-bd88-497d-9696-804c787b73ef
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%
---
# ACSD-50815 : la quantité décimale pour un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé

Le correctif ACSD-50815 corrige le problème en raison duquel la quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé. Ce correctif est disponible lorsque la version 1.1.35 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-50815. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La quantité décimale d’un produit simple ne peut pas être utilisée pour une nouvelle option de produit groupé.

<u>Procédure à suivre </u> :

1. Connectez-vous en tant qu’administrateur
1. Créez un produit simple.
   * Dans la fenêtre **[!UICONTROL Advanced Inventory]**, définissez [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Enregistrez le produit simple.
1. Créez un nouveau produit groupé.
1. Ajoutez n’importe quelle option.
1. Ajoutez le produit simple dans cette option.
1. Définissez une quantité décimale pour le produit simple dans l’option produit groupé . Par exemple, 1.5.

<u>Résultats attendus</u> :

Il est possible de définir une quantité décimale. Aucune erreur ne s’affiche.

<u>Résultats réels</u> :

L’erreur *Veuillez saisir un nombre valide dans ce champ* s’affiche.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
