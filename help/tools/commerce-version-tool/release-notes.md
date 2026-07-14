---
title: Notes de mise à jour de [!DNL Commerce Version Tool]
description: Découvrez les versions  [!DNL Commerce Version Tool] , notamment les nouveaux rapports sur l’état des correctifs, l’état de la protection CVE, la sortie CSV et le comportement du cache.
feature: Release Notes
TQID: 'https://experienceleague.adobe.com/38I3U5y9rmurP5gVhalfUq7DlcUb-JpF5eUam1nwEyk'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 180
ht-degree: 2%

---

# Notes de mise à jour de [!DNL Commerce Version Tool]

Ces notes de mise à jour décrivent les mises à jour d’[!DNL Commerce Version Tool] ([!DNL CVT]).

## Version 1.0.0 — Juin 2026 {#version-1-0-0}

### Nouvelles fonctionnalités

- **Rapports de statut des correctifs** - Indique quels correctifs de sécurité Adobe Commerce mensuels sont appliqués, manquants ou ne peuvent pas être classés pour une installation Adobe Commerce.
- **Statut de protection CVE** - Mappe les résultats du correctif aux valeurs de statut de protection par CVE : `PROTECTED`, `VULNERABLE`, `UNKNOWN` et `NOT_APPLICABLE`.
- **Prise en charge de plusieurs composants** - Détecte les composants Adobe Commerce installés à partir d’`composer.lock`, y compris Adobe Commerce business-to-business (B2B), Adobe Commerce Page Builder, Adobe Commerce Inventory et d’autres composants représentés dans le fichier de registre des correctifs.
- **Sortie JSON et CSV** - Fournit une sortie JSON par défaut pour la consommation programmatique et une sortie CSV pour les feuilles de calcul, les scanners, les tableaux de bord et les outils de conformité.
- **Comportement de mise en cache convivial hors ligne** - Met en cache le fichier de registre des correctifs localement après chaque récupération réussie. Si le registre distant n’est pas disponible, l’outil [!DNL CVT] peut utiliser le registre mis en cache avec un avertissement.
- **Diffusion groupée** - Expédiée dans des fichiers de correctifs de sécurité Adobe Commerce mensuels. L’application du correctif installe [!DNL CVT] à `vendor/bin/patch-status` sans étape d’installation distincte.

## Rubriques connexes

- [Introduction](intro.md)
- [Génération d’un rapport d’état des correctifs](generate-report.md)
- [Dépannage](troubleshooting.md)
