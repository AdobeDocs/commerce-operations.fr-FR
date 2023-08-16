---
title: Référence .gitignore
description: Découvrez comment ajouter un fichier inclus dans la liste d’exclusion.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# Référence .gitignore

Magento Open Source comprend une base `.gitignore` fichier . Voir [le dernier Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) fichier . Si vous devez ajouter un fichier qui se trouve dans la variable `.gitignore` , vous pouvez utiliser la variable `-f` (force) lors de l’évaluation d’une validation :

```bash
git add <path/filename> -f
```
