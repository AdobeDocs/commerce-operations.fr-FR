---
title: 'ACSD-64732 : les contrôleurs tiers ne sont pas correctement mis en cache avec les segments clients'
description: Appliquez le correctif ACSD-64732 pour résoudre le problème d’Adobe Commerce en raison duquel les contrôleurs tiers ne sont pas correctement mis en cache avec les segments clients.
feature: Cache
role: Admin, Developer
exl-id: 378e5a96-06dd-4796-9e45-a67cf539fcce
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '315'
ht-degree: 0%
---
# ACSD-64732 : les contrôleurs tiers ne sont pas correctement mis en cache avec les segments clients

Le correctif ACSD-64732 corrige le problème en raison duquel les contrôleurs tiers ne sont pas correctement mis en cache avec les segments clients. Ce correctif est disponible lorsque la version 1.1.62 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-64732. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les contrôleurs tiers ne sont pas correctement mis en cache avec les segments clients.

<u>Procédure à suivre </u> :

1. Accédez au contrôleur personnalisé (/catalog/category/vary).
1. Accédez à l’onglet **[!UICONTROL Network]** et vérifiez la valeur de **[!DNL X-Magento-Vary]**.

<u>Résultats attendus</u> :

La valeur **[!UICONTROL X-Magento-Vary]** doit être la même sur le contrôleur personnalisé.

<u>Résultats réels</u> :

La valeur de **[!UICONTROL X-Magento-Vary]** est différente, ce qui entraîne des pertes dans le cache. Cela signifie que le cache généré précédemment ne peut pas être utilisé lors de la visite du contrôleur personnalisé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : mises à niveau et correctifs > Appliquer des correctifs dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
