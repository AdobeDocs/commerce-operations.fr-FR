---
title: Créer des liens symboliques vers des fichiers LESS
description: Découvrez comment créer des liens symboliques vers des fichiers LESS pour le développement Adobe Commerce. Découvrez la liaison de feuilles de style et l’optimisation des workflows de développement.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
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
source-wordcount: '173'
ht-degree: 0%
---
# Créer des liens symboliques vers des fichiers LESS

{{file-system-owner}}

Pour créer des liens symboliques vers des fichiers LESS :

Options de commande :

```shell
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

```shell
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Les messages suivants s’affichent pour confirmer la réussite :

```text
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Pour créer des fichiers LESS pour le code HTML d’administration :

```shell
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
