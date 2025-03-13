---
title: 'ACSD-63323 : résout [!UICONTROL Select All] fonctionnalité et améliore la pagination et le nombre d’enregistrements dans la fenêtre contextuelle de la catégorie de produits.'
description: Appliquez le correctif ACSD-63323 pour résoudre le problème d’Adobe Commerce en raison duquel l’option [!UICONTROL Select All] ne fonctionne pas lors de l’ajout de produits à une catégorie. En outre, cela garantit que la pagination et le libellé du nombre d’enregistrements fonctionnent correctement lors de l’ajout de produits à une catégorie via la grille contextuelle.
feature: Products
role: Admin, Developer
source-git-commit: f3f0cc93adf83b485ca50811adcc561638e3c5c2
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-63323 : résout [!UICONTROL Select All] fonctionnalité et améliore la pagination et le nombre d’enregistrements dans la fenêtre contextuelle de la catégorie de produits.

Le correctif ACSD-63323 corrige le problème en raison duquel l’option **[!UICONTROL Select All]** ne fonctionne pas lors de l’ajout de produits à une catégorie. En outre, cela garantit que la pagination et le libellé du nombre d’enregistrements fonctionnent correctement lors de l’ajout de produits à une catégorie via la grille contextuelle. Ce correctif est disponible lorsque le [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installé. L’ID du correctif est ACSD-63323. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Correction du problème en raison duquel l’option **[!UICONTROL Select All]** ne fonctionne pas dans Admin > **[!UICONTROL Categories]** > choisir une catégorie > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**. Elle permet également à la pagination et au libellé du nombre d’enregistrements de fonctionner correctement lors de l’ajout de produits à une catégorie via la grille contextuelle.


<u>Procédure à suivre </u> :

1. Générez les produits *1200* à l’aide de la commande :

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Ouvrez **[!UICONTROL Catalog]** > **[!UICONTROL Products]** et affichez le nombre de produits : *1200* enregistrements trouvés.
1. Ouvrez une Catégorie par défaut > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**.
1. Cliquez sur **[!UICONTROL Assign]** > **[!UICONTROL Select All]**.
1. Remplacez le nombre de produits sur la page par la valeur = *5*.


**Résultats attendus** :

*Le message doit être le suivant : 1 200 enregistrements trouvés (1 200 sélectionnés)*

**Résultats réels** :

* La pagination ne fonctionne pas.
* Un message incorrect s’affiche : *5* enregistrements trouvés (*20* sélectionnés)

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .


