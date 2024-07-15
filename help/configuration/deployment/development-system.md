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

Vous pouvez avoir un nombre illimité de systèmes de développement, à condition que ce qui suit soit vrai pour tous :

- Ils exécutent tous Commerce 2.2 ou version ultérieure.
- Tout le code Commerce est contrôlé par la source dans le même référentiel que les systèmes de création et de production.
- Chaque système de développement doit utiliser le [mode par défaut](../bootstrap/application-modes.md#default-mode) ou le [mode développeur](../bootstrap/application-modes.md#developer-mode).
- Il dispose de droits de propriété et d’autorisations du système de fichiers, comme décrit dans la section [Condition préalable requise pour votre développement, création et production ](../deployment/technical-details.md).
- Assurez-vous que tous les éléments suivants sont _excluded_ du contrôle source :

   - Répertoire `vendor` (et sous-répertoires)
   - Répertoire `generated` (et sous-répertoires)
   - Répertoire `pub/static` (et sous-répertoires)
   - `app/etc/env.php` fichier

- Assurez-vous que `app/etc/config.php` est _inclus_ dans le contrôle de code source

Si vous utilisez Git, le fichier `.gitignore` fournit la plupart des éléments précédents. Voir la référence [`.gitignore`](../reference/config-reference-gitignore.md).
