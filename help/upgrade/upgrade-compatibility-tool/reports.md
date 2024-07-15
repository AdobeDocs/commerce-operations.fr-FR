---
title: Rapports '[!DNL Upgrade Compatibility Tool]'
description: Suivez ces étapes pour exécuter  [!DNL Upgrade Compatibility Tool]  sur votre projet Adobe Commerce.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Rapports

{{commerce-only}}

Suite à l&#39;analyse, le [!DNL Upgrade Compatibility Tool] peut exporter un rapport contenant une liste de problèmes pour chaque fichier spécifiant sa gravité, son code d&#39;erreur et sa description de l&#39;erreur. Le [!DNL Upgrade Compatibility Tool] exporte le rapport dans deux formats différents :

- Un [fichier JSON](reports.md#json-file).
- Un [rapport d’HTML](reports.md#html-report).

Consultez l’exemple d’interface de ligne de commande suivant d’un rapport :

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Consultez la rubrique [Référence du message d’erreur](../upgrade-compatibility-tool/error-messages.md) pour plus d’informations sur les différentes erreurs que ce rapport peut générer.

Ce rapport contient également un résumé détaillé qui indique :

- *Version actuelle* : version actuellement installée.
- *Version cible* : version vers laquelle vous souhaitez effectuer la mise à niveau.
- *Temps d’exécution* : temps nécessaire à l’analyse pour créer le rapport (mm:ss).
- *Modules nécessitant une mise à jour* : pourcentage de modules contenant des problèmes de compatibilité et nécessitant une mise à jour.
- *Fichiers nécessitant une mise à jour* : pourcentage de fichiers contenant des problèmes de compatibilité et nécessitant une mise à jour.
- *Nombre total d&#39;erreurs critiques* : nombre d&#39;erreurs critiques trouvées.
- *Nombre total d&#39;erreurs* : nombre d&#39;erreurs trouvées.
- *Total des avertissements* : nombre d’avertissements trouvés.
- *Utilisation du pic mémoire* : quantité maximale de mémoire atteinte par [!DNL Upgrade Compatibility Tool] lors de l’exécution.

Voir l’exemple d’interface de ligne de commande suivant :

```terminal
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## Fichier JSON

Vous pouvez obtenir la sortie du fichier JSON lors de l’exécution de [!DNL Upgrade Compatibility Tool] sur une interface de ligne de commande. Le fichier `JSON` contient exactement les mêmes informations que celles affichées dans la sortie [!DNL Upgrade Compatibility Tool] :

- Liste des problèmes identifiés.
- Résumé de l’analyse.

Pour chaque problème rencontré, le rapport fournit des informations détaillées telles que la gravité et la description du problème.

Pour exporter ce fichier `JSON` dans un dossier de sortie différent :

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Où les arguments sont les suivants :

- `<dir>` : répertoire d’installation Adobe Commerce.
- `[=JSON-OUTPUT-PATH]` : répertoire de chemin d’accès pour exporter le fichier de sortie `JSON`.

>[!NOTE]
>
> Le chemin par défaut du dossier de sortie est `var/output/[TIME]-results.json`.

## Rapport HTML

Vous pouvez obtenir le rapport d’HTML lors de l’exécution de l’outil sur une interface de ligne de commande ou via le [!DNL Site-Wide Analysis Tool]. Le rapport HTML contient également :

- Liste des problèmes identifiés.
- Résumé de l’analyse.

![Rapport d’HTML - Résumé](../../assets/upgrade-guide/uct-html-summary.png)

Vous pouvez facilement parcourir les problèmes identifiés lors de l’analyse [!DNL Upgrade Compatibility Tool].

Vous pouvez filtrer les problèmes affichés sur le rapport en fonction du niveau de problème minimum (la valeur par défaut est `WARNING`).

Une liste déroulante dans le coin supérieur droit permet de sélectionner un autre niveau. La liste des problèmes identifiés est filtrée en conséquence.

![Rapport d’HTML - Utilisation de la liste déroulante](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Les problèmes avec un niveau de problème plus faible sont supprimés, mais vous recevez une notification pour que vous soyez toujours conscient des problèmes identifiés par module.

Le rapport HTML comprend également quatre graphiques différents :

- **Modules par gravité de problème** : affiche la distribution de la gravité par modules.
- **Fichiers par gravité de problème** : affiche la distribution de gravité par fichiers.
- **Modules classés par nombre total de problèmes** : affiche les 10 modules les plus compromis prenant en compte les avertissements, erreurs et erreurs critiques.
- **Modules avec des tailles et des problèmes relatifs** : plus un module contient de fichiers, plus son cercle est volumineux. Plus un module a de problèmes, plus son cercle rouge apparaît.

Ces graphiques vous permettent d’identifier les modules les plus compromis et ceux qui nécessitent davantage de travail pour effectuer une mise à niveau.

![Rapport d’HTML - Diagrammes](../../assets/upgrade-guide/uct-html-diagrams.png)

Les diagrammes de rapport d’HTML sont également mis à jour en conséquence, à l’exception de `Modules with relative sizes and issues`, qui est généré avec le `min-issue-level` initialement configuré.

Si vous souhaitez afficher des résultats différents pour le diagramme `Modules with relative sizes and issues`, vous devez exécuter à nouveau la commande en fournissant une autre valeur pour l’option `--min-issue-level`.

![Rapport d’HTML - Diagramme de bulles](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Pour exporter ce rapport d&#39;HTML dans un dossier de sortie différent :

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Où les arguments sont les suivants :

- `<dir>` : répertoire d’installation Adobe Commerce.
- `[=HTML-OUTPUT-PATH]` : répertoire de chemin d’accès pour exporter le fichier de sortie `.html`.

>[!NOTE]
>
> Le chemin par défaut du dossier de sortie est `var/output/[TIME]-results.html`.
