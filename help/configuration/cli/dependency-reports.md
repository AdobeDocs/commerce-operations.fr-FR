---
title: Rapports de dépendance
description: Créez des rapports qui affichent les totaux pour les dépendances de module, circulaire et de structure.
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Rapports de dépendance

{{file-system-owner}}

Vous pouvez exécuter les types de rapports suivants :

- **Dépendances de module** : indique le nombre total de dépendances entre les modules et si les dépendances sont hard ou soft.
- **Dépendances circulaires** : affiche le nombre total de chaînes de dépendances ainsi que le nombre et la liste des dépendances circulaires pour chaque module.
- **Dépendances de structure** : affiche le nombre total de dépendances de la structure Commerce par module (y compris le nombre total d’entrées de structure pour chaque bibliothèque).

Une dépendance dans un commentaire est également une dépendance.

## Exécution des rapports de dépendance

Options de commande :

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

Le tableau suivant explique les options, paramètres et valeurs de cette commande.

| Paramètre | Valeur | Obligatoire ? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Rapport Dépendances des modules . | Oui |
| `show-modules-circular` | Rapport Dépendances circulaires . | Oui |
| `show-framework` | Rapport des dépendances de structure. | Oui |
| `-d --directory` | Chemin d’accès au répertoire de base pour commencer la recherche des données de rapport. | Non |
| `-o --output` | Indique le chemin d’accès au système de fichiers absolu et le nom de fichier du fichier de sortie csv (valeurs séparées par des virgules) pour le rapport. | Non |

Si aucun répertoire ou nom de fichier n’est transmis comme argument, la racine de l’application suivante est utilisée comme répertoire par défaut et les noms de fichier par défaut suivants sont utilisés :

| Commande | Nom du fichier |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Exemple de rapport de dépendances de module

Voici une partie de la sortie pour un exemple de rapport de dépendances de module :

```
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Exemple de rapport de dépendances circulaires

Voici une partie de la sortie pour un exemple de rapport de dépendances circulaires :

```
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Exemple de rapport de dépendances de framework

Voici une partie de la sortie pour un exemple de rapport de dépendances de structure :

```
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
