---
title: Référence .gitignore
description: Découvrez comment ajouter un fichier inclus dans la liste d’exclusion.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# Référence .gitignore

Magento Open Source comprend un fichier `.gitignore` de base. Voir [le dernier fichier `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) de Commerce. Si vous devez ajouter un fichier qui se trouve dans la liste de `.gitignore`, vous pouvez utiliser l’option `-f` (forcer) lors de l’évaluation d’une validation :

```bash
git add <path/filename> -f
```
