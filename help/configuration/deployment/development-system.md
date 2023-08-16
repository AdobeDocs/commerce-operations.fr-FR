---
title: Configuration du système de développement
description: Découvrez comment configurer un système de développement pour l’application Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Configuration du système de développement

Vous pouvez avoir un nombre illimité de systèmes de développement, à condition que ce qui suit soit vrai pour tous :

- Elles exécutent toutes Commerce 2.2 ou version ultérieure.
- L’ensemble du code Commerce est contrôlé par la source dans le même référentiel que les systèmes de création et de production.
- Chaque système de développement doit utiliser : [mode par défaut](../bootstrap/application-modes.md#default-mode) ou [mode développeur](../bootstrap/application-modes.md#developer-mode)
- Il dispose de la propriété du système de fichiers et d’autorisations définies comme décrit dans [Conditions préalables pour vos systèmes de développement, de génération et de production](../deployment/technical-details.md).
- Assurez-vous que tous les éléments suivants sont _excluded_ du contrôle source :

   - `vendor` répertoire (et sous-répertoires)
   - `generated` répertoire (et sous-répertoires)
   - `pub/static` répertoire (et sous-répertoires)
   - `app/etc/env.php` fichier

- Assurez-vous de `app/etc/config.php` is _included_ dans le contrôle source

Si vous utilisez Git, la variable `.gitignore` fournit la plupart des éléments précédents. Voir [`.gitignore` reference](../reference/config-reference-gitignore.md).
