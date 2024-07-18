---
title: Création de liens symboliques vers des fichiers LESS
description: Découvrez comment créer des liens symboliques vers des fichiers LESS.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
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
>Pendant le développement, cette commande crée des liens symboliques pour les fichiers LESS dans les dossiers `var/view_preprocessed` et `pub/static`. Ce processus ne compile pas les fichiers LESS dans les fichiers CSS.

Le tableau suivant explique les paramètres et les valeurs de cette commande.

| Paramètre | Valeur | Obligatoire ? |
| --------- | ----- | --------- |
| `--type` | Type de fichiers source : [less] (par défaut : &quot;less&quot;)<br>Actuellement, LESS est le seul type de fichier pris en charge. | Non |
| `--locale` | Code de paramètre régional.<br>Pour afficher la liste des codes de paramètres régionaux, saisissez `bin/magento info:language:list` | Non |
| `--area` | Zone (`adminhtml` pour la zone administrative, `frontend` pour le storefront). | Non |
| `--theme` | Nom du thème au format `<VendorName>/<theme-name>`. Par exemple, `Magento/blank` ou `Magento/backend`. | Non |
| `<file>` | Liste de fichiers CSS séparés par des espaces à convertir en LESS sans l’extension CSS. (La valeur par défaut est `css/styles-m css/styles-l`, pour le type adminhtml `css/styles css/styles-old`) | Non |

Par exemple, pour créer des fichiers LESS pour le thème front-end `VendorName/themeName` dans le paramètre régional `en_US` à l’aide d’un fichier CSS nommé `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, saisissez la commande suivante :

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Les messages suivants s’affichent pour confirmer la réussite :

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Pour créer des fichiers LESS pour l’administrateur html :

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
