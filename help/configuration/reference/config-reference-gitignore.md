---
title: Référence .gitignore
description: Découvrez comment ajouter un fichier inclus dans la liste d’exclusion.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---


# Référence .gitignore

Magento Open Source comprend une base `.gitignore` fichier . Voir [le dernier Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) fichier . Si vous devez ajouter un fichier qui se trouve dans la variable `.gitignore` , vous pouvez utiliser la variable `-f` (force) lors de l’évaluation d’une validation :

```bash
git add <path/filename> -f
```
