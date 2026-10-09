---
title: Référence .gitignore
description: Découvrez comment ajouter des fichiers à la liste .gitignore pour les projets Adobe Commerce. Découvrez les bonnes pratiques en matière de gestion du contrôle de version et d’exclusion de fichiers.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '65'
ht-degree: 0%
---
# Référence .gitignore

Magento Open Source comprend un fichier `.gitignore` de base. Voir [le dernier fichier `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) de Commerce. Si vous devez ajouter un fichier qui se trouve dans la liste de `.gitignore`, vous pouvez utiliser l’option `-f` (forcer) lors de l’évaluation d’une validation :

```shell
git add <path/filename> -f
```
