---
title: 'ACSD-65913: [!DNL OpenSearch] lance une exception legal_argument_exception pour les catégories dont les produits ont le même prix'
description: Appliquez le correctif ACSD-65913 pour résoudre le problème d [!DNL Opensearch] Adobe Commerce où renvoie une exception legal_argument_exception (« Le paramètre [from] ne peut pas être négatif ») sur les catégories contenant tous les produits au même prix.
feature: Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: fa4c50fdf6b51c981e49369dc9f70600f46b5689
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-65913 : [!DNL OpenSearch] lance une `illegal_argument_exception` pour les catégories dont les produits ont le même prix

Le correctif ACSD-65913 corrige le problème où [!DNL OpenSearch] lançait un `illegal_argument_exception` pour les catégories dont les produits avaient le même prix. Ce correctif est disponible lorsque la version 1.1.66 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65913. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.8

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

[!DNL OpenSearch] renvoie une `illegal_argument_exception` (*[le paramètre de ] ne peut pas être négatif*) lors du chargement de catégories dans lesquelles tous les produits partagent le même prix.

<u>Procédure à suivre </u> :

1. Installez [!DNL OpenSearch] version 2.19.1 et définissez-la comme moteur de recherche par défaut.
1. Configurez l’attribut de produit **[!UICONTROL Price]** pour qu’il soit visible dans la navigation superposée :
   1. **[!UICONTROL Visible in Advanced Search]** : *Oui*
   1. **[!UICONTROL Comparable on Storefront]** : *Oui*
   1. **[!UICONTROL Use in Layered Navigation]** : *filtrable (avec résultats)*
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**. Définissez **[!UICONTROL Price Navigation Step Calculation]** sur *Automatique (égalisation du nombre de produits)*.
1. Créez une catégorie avec six produits ayant tous le même prix :
   1. SKU : product_super_0-1-1-1, Prix : 150 $
   1. SKU : product_super_0-1-1, Prix : 48 $
   1. SKU : product_super_0-1, Prix : 48 $
   1. SKU : product_super_0, Prix : 48 $
   1. SKU : product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1, Prix : 48 $
   1. SKU : product_super_0-1-1-1-1-1-1-1-1-1-1-1, Prix : 48 $
1. Exécutez la commande suivante :
   `bin/magento indexer:reindex`
1. Ouvrez la page de catégorie. Une erreur s’affiche :
   Le paramètre *[from] ne peut pas être négatif, [-1 trouvé]*

<u>Résultats attendus</u> :

[!DNL OpenSearch] ne devez pas lancer de `illegal_argument_exception` lorsque tous les produits d’une catégorie ont le même prix.

<u>Résultats réels</u> :

* [!DNL OpenSearch] renvoie une `illegal_argument_exception` avec le message :
  Le paramètre *[from] ne peut pas être négatif, [-1 trouvé]*

* Le fichier `var/log/exception.log` contient :

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
