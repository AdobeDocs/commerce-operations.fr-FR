---
title: Créer des liens symboliques vers des fichiers LESS
description: Découvrez comment créer des liens symboliques vers des fichiers LESS pour le développement Adobe Commerce. Découvrez la liaison de feuilles de style et l’optimisation des workflows de développement.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Créer des liens symboliques vers des fichiers LESS

{{file-system-owner}}

Pour créer des liens symboliques vers des fichiers LESS :

Options de commande :

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Pendant le développement, cette commande crée des liens symboliques pour les fichiers LESS dans les dossiers `var/view_preprocessed` et `pub/static`. Ce processus ne compile pas les fichiers LESS dans des fichiers CSS.

Le tableau suivant explique les paramètres et valeurs de cette commande.

| Paramètre | Valeur | Obligatoire ? |
| --------- | ----- | --------- |
| `--type` | Type des fichiers sources : [less] (par défaut : « less »)<br>Actuellement, LESS est le seul type de fichier pris en charge. | Non |
| `--locale` | Code du paramètre régional.<br>Pour afficher la liste des codes de paramètres régionaux, saisissez `bin/magento info:language:list` | Non |
| `--area` | Zone (`adminhtml` pour la zone administrative, `frontend` pour la vitrine). | Non |
| `--theme` | Nom du thème au format `<VendorName>/<theme-name>`. Par exemple, `Magento/blank` ou `Magento/backend`. | Non |
| `<file>` | Liste séparée par des espaces de fichiers CSS à convertir en LESS sans extension CSS. (La valeur par défaut est `css/styles-m css/styles-l`, pour le type adminhtml `css/styles css/styles-old`) | Non |

Par exemple, pour créer des fichiers LESS pour le thème front-end nommé `VendorName/themeName` dans le paramètre régional `en_US` à l’aide d’un fichier CSS nommé `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, saisissez la commande suivante :

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Les messages suivants s’affichent pour confirmer la réussite :

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Pour créer des fichiers LESS pour le code HTML d’administration :

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
