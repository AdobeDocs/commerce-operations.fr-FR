---
title: 'ACSD-66082 : impossible de mettre à jour l’image d’échantillon d’un produit via l’importation du produit'
description: Appliquez le correctif ACSD-66082 pour résoudre le problème d’Adobe Commerce en raison duquel le chargement d’un fichier CSV avec le champ swatch_image défini sur EMPTY_VALUE pour annuler la définition des images d’échantillon entraîne l’échec du processus d’importation avec une erreur.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
source-git-commit: e0d2e42b070591f3fefc0e9adb1bf5c1ba580fd9
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-66082 : impossible de mettre à jour l’image d’échantillon d’un produit via l’importation du produit

Le correctif ACSD-66082 corrige le problème en raison duquel il n’était pas possible de mettre à jour l’image d’échantillon d’un produit lors de l’importation du produit. Ce correctif est disponible lorsque la version 1.1.68 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-66082. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le téléchargement d’un fichier CSV avec le champ `swatch_image` défini sur `EMPTY_VALUE` pour annuler la définition des images d’échantillon entraîne l’échec du processus d’importation avec une erreur.

<u>Procédure à suivre </u> :

1. Créez un produit simple. Accédez à **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Cliquez sur la flèche vers le bas à côté du bouton **[!UICONTROL Add Product]** et choisissez **[!UICONTROL Simple Product]**. Définissez son **[!UICONTROL SKU]** sur *ABC*.
1. Chargez une image PNG nommée *testing.png* dans `var/import/images/`.
1. Créez un fichier CSV avec le contenu suivant :

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Import]** pour importer le fichier en ajustant les paramètres suivants :
   * **[!UICONTROL Entity type]** : *Products*
   * **[!UICONTROL Import Behavior]** : *Ajouter/Mettre à jour*
   * Cliquez sur **[!UICONTROL Choose File]** pour sélectionner le fichier CSV créé à l’étape précédente à importer. L’importation a réussi et l’échantillon est ajouté.
1. Mettez à jour le fichier CSV avec le contenu suivant :

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Répétez le processus d’importation.

<u>Résultats attendus</u> :

L’image d’échantillon n’est pas définie.

<u>Résultats réels</u> :

Le processus d’importation renvoie une erreur.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
