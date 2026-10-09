---
title: 'ACSD-62355 : améliore les performances d’édition de produit configurables dans Adobe Commerce'
description: Appliquez le correctif ACSD-62355 pour résoudre le problème d’Adobe Commerce en raison duquel la page d’édition de produit configurable subit un chargement lent lorsque le produit est basé sur de nombreux attributs avec de nombreuses valeurs.
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '562'
ht-degree: 0%
---
# ACSD-62355 : améliore les performances d’édition de produit configurables dans Adobe Commerce

Le correctif ACSD-62355 corrige le problème des temps de chargement lents et de la consommation élevée de mémoire sur la page de modification du produit configurable lorsque le produit a de nombreux attributs avec de nombreuses valeurs. Ce correctif est disponible lorsque la version 1.1.56 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62355. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le chargement de la page de modification de produit configurable prend beaucoup de temps lorsque le produit configurable est basé sur plusieurs attributs avec de nombreuses valeurs, ce qui entraîne des retards et des problèmes potentiels de délai d’expiration ou de limite de mémoire.

<u>Procédure à suivre </u> :

1. Créez 9 nouveaux attributs dans le jeu d’attributs par défaut, chacun étant [!UICONTROL Filterable] et comportant [!UICONTROL Scope] : [!UICONTROL Global].
   * Attribut 1 : 50 options
   * Attribut 2 : 20 options
   * Attribut 3 : 10 options
   * Attribut 4 : 5 options
   * Attribut 5 : 5 options
   * Attribut 6 : 5 options
   * Attribut 7 : 5 options
   * Attribut 8 : 3 options
   * Attribut 9 : 2 options

1. Créez 9 produits simples avec des combinaisons d’options à partir des attributs nouvellement créés.
   * Produit 1 : première option de chaque attribut
   * Produit 2 : deuxième option de chaque attribut
   * Produit 3 : troisième option de chaque attribut
   * Produit 4 : Quatrième option de chaque attribut
   * Si un attribut comporte moins d’options que le nombre de produits, affectez les produits restants à des options aléatoires dans cet attribut.

1. Créez un produit configurable qui utilise les attributs nouvellement créés :
   * Ajoutez un produit enfant avec la configuration suivante :
     * Utilisez la dernière option de l’attribut 1 et la première option des attributs 2 à 9.
     * Vous obtenez 1 produit configurable et 1 produit enfant.
1. Accédez à l’onglet **[!UICONTROL Configurations]** du produit configurable.
1. Cliquez sur **[!UICONTROL Add Products]** manuellement et commencez à ajouter un par un les produits simples créés précédemment.
1. Enregistrez les modifications après chaque ajout.
1. Lorsque vous ajoutez des produits, observez le temps de chargement de la page Modifier le produit configurable .
1. Après avoir ajouté 7 produits, vous remarquerez une augmentation significative de la consommation de RAM et du temps de chargement des pages

<u>Résultats attendus</u> :

Le formulaire de modification du produit doit se charger rapidement et efficacement sans consommation excessive de mémoire.

<u>Résultats réels</u> :

La modification du produit configurable prend beaucoup de temps à charger et peut atteindre des limites de mémoire ou des erreurs de délai d’expiration.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
