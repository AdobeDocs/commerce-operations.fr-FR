---
title: Configuration du système de développement
description: Découvrez comment configurer un système de développement pour l’application Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Configuration du système de développement

Vous pouvez avoir un nombre illimité de systèmes de développement, à condition que ce qui suit s’applique à tous :

- Ils exécutent tous Commerce 2.2 ou une version ultérieure
- Tout le code Commerce est sous contrôle de code source dans le même référentiel que les systèmes de génération et de production
- Chaque système de développement doit utiliser [mode par défaut](../bootstrap/application-modes.md#default-mode) ou [mode développeur](../bootstrap/application-modes.md#developer-mode)
- La propriété et les autorisations du système de fichiers sont définies, comme indiqué dans la section [Prérequis pour les systèmes de développement, de version et de production](../deployment/technical-details.md).
- Assurez-vous que tous les éléments suivants sont _exclus_ du contrôle de code source :

   - Répertoire `vendor` (et sous-répertoires)
   - Répertoire `generated` (et sous-répertoires)
   - Répertoire `pub/static` (et sous-répertoires)
   - fichier `app/etc/env.php`

- Vérifiez que `app/etc/config.php` est _inclus_ dans le contrôle de code source

Si vous utilisez Git, le fichier `.gitignore` fournit la plupart des éléments précédents. Voir la référence [`.gitignore`](../reference/config-reference-gitignore.md).
