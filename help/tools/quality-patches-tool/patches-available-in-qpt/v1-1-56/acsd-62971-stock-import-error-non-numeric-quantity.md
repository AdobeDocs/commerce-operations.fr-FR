---
title: 'ACSD-62971 : l''importation des sources de stock avec des valeurs de quantité non numériques entraîne la définition de la quantité sur 0'
description: Appliquez le correctif ACSD-62971 pour résoudre le problème d'Adobe Commerce où l'importation d'origines de stock avec des valeurs non numériques dans la colonne 'quantité' entraîne la définition de la quantité sur 0.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
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
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-62971 : l&#39;importation des sources de stock avec des valeurs de quantité non numériques entraîne la définition de la quantité sur 0

Le correctif ACSD-62971 corrige le problème où l&#39;importation de sources de stock avec des valeurs non numériques dans la colonne &#39;quantité&#39; entraîne la définition de la quantité sur 0. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62971. Notez que le problème devait être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction du problème en raison duquel l’importation d’origines de stock avec des valeurs non numériques dans la colonne **[!UICONTROL Quantity]** entraîne la définition de la quantité sur 0.

<u>Procédure à suivre </u> :

1. Créer un **[!UICONTROL Simple Product]** avec qty=100
1. Effectuez une importation **[!UICONTROL Stock Sources]** en utilisant le fichier dont la quantité est incorrecte (« abc »)

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Vérifier la quantité après l&#39;import.

<u>Résultats attendus</u> :
La validation des données d’importation doit échouer.

<u>Résultats réels</u> :
La quantité de produit simple est devenue 0 et le produit est mis à jour comme [!UICONTROL Out of Stock].

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
