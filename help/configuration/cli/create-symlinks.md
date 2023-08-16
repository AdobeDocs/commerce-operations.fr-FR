---
title: Création de liens symboliques vers des fichiers LESS
description: Découvrez comment créer des liens symboliques vers des fichiers LESS.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Création de liens symboliques vers des fichiers LESS

{{file-system-owner}}

Pour créer des liens symboliques vers des fichiers LESS :

Options de commande :

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Au cours du développement, cette commande crée des liens symboliques pour les fichiers LESS dans `var/view_preprocessed` et `pub/static` dossiers. Ce processus ne compile pas les fichiers LESS dans les fichiers CSS.

Le tableau suivant explique les paramètres et les valeurs de cette commande.

| Paramètre | Valeur | Obligatoire ? |
| --------- | ----- | --------- |
| `--type` | Type de fichier source : [less] (par défaut : &quot;less&quot;)<br>Actuellement, LESS est le seul type de fichier pris en charge. | Non |
| `--locale` | Code de paramètre régional.<br>Pour afficher la liste des codes de paramètres régionaux, saisissez `bin/magento info:language:list` | Non |
| `--area` | Zone (`adminhtml` pour la zone administrative, `frontend` pour le storefront). | Non |
| `--theme` | Nom du thème dans `<VendorName>/<theme-name>` format. Par exemple : `Magento/blank` ou `Magento/backend`. | Non |
| `<file>` | Liste de fichiers CSS séparés par des espaces à convertir en LESS sans l’extension CSS. (Par défaut : `css/styles-m css/styles-l`, pour le type adminhtml `css/styles css/styles-old`) | Non |

Par exemple, pour créer des fichiers LESS pour le thème front-end nommé `VendorName/themeName` dans le `en_US` locale à l’aide d’un fichier CSS nommé `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, saisissez la commande suivante :

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Les messages suivants s’affichent pour confirmer la réussite :

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Pour créer des fichiers LESS pour l’administrateur html :

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
