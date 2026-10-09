---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
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
source-wordcount: '185'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.71

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.71.

QPT v1.1.71 comprend les correctifs suivants :


* **ACSD-60624** : le chargement de l’image échoue pour le contenu vide dans les sections Image, Bannière et Curseur de [!DNL Page Builder]
* **ACSD-67089** : problème de pagination dans l’API `inventory/export-stock-salable-qty`, qui limite incorrectement la `total_count` à la taille de la page.
* **ACSD-67093** : la récupération des commandes via [!DNL GraphQL] à l’aide du filtre de période renvoie des résultats incorrects.
* **ACSD-67459** : impossible d&#39;importer les produits dont la description dépasse 65 536 caractères.
* **ACSD-67603** : temps de traitement long de la génération du plan de site pour les produits avec l’inclusion d’images activée
* **ACSD-67643** : des entrées en double sont créées lors des mises à jour planifiées dans les environnements comportant un grand nombre de catégories imbriquées.
* **ACSD-67652** : le statut du bundle du produit est renvoyé comme étant en rupture de stock dans les appels de [!DNL GraphQL], même avec des produits enfants et parents en stock.
* **ACSD-67904** : impossible de passer des commandes si le nom de la ville contient des chiffres (0-9), une esperluette (&amp;), un point (.) ou des parenthèses ().

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
