---
title: Référence .gitignore
description: Découvrez comment ajouter des fichiers à la liste .gitignore pour les projets Adobe Commerce. Découvrez les bonnes pratiques en matière de gestion du contrôle de version et d’exclusion de fichiers.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# Référence .gitignore

Magento Open Source comprend un fichier `.gitignore` de base. Voir [le dernier fichier `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) de Commerce. Si vous devez ajouter un fichier qui se trouve dans la liste de `.gitignore`, vous pouvez utiliser l’option `-f` (forcer) lors de l’évaluation d’une validation :

```bash
git add <path/filename> -f
```
