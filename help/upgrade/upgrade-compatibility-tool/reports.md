---
title: '[!DNL Upgrade Compatibility Tool] des rapports'
description: Pour exécuter le sur votre projet Adobe Commerce [!DNL Upgrade Compatibility Tool]  procédez comme suit.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Rapports

{{commerce-only}}

Suite à l’analyse, l’[!DNL Upgrade Compatibility Tool] peut exporter un rapport contenant une liste des problèmes de chaque fichier en spécifiant sa gravité, son code d’erreur et sa description. Le [!DNL Upgrade Compatibility Tool] exporte le rapport dans deux formats différents :

- Un [fichier JSON](reports.md#json-file).
- Rapport HTML [&#128279;](reports.md#html-report).

Consultez l’exemple de rapport suivant d’interface de ligne de commande :

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Consultez la rubrique [Référence du message d’erreur](../upgrade-compatibility-tool/error-messages.md) pour plus d’informations sur les différentes erreurs que ce rapport peut produire.

Ce rapport comprend également un résumé détaillé qui indique :

- *Version actuelle* : version actuellement installée.
- *Version cible* : version vers laquelle vous souhaitez effectuer la mise à niveau.
- *Temps d’exécution* : durée nécessaire à l’analyse pour générer le rapport (mm:ss).
- *Modules qui nécessitent une mise à jour* : pourcentage de modules qui contiennent des problèmes de compatibilité et qui nécessitent une mise à jour.
- *Fichiers nécessitant une mise à jour* : pourcentage de fichiers contenant des problèmes de compatibilité et nécessitant une mise à jour.
- *Nombre total d’erreurs critiques* : nombre d’erreurs critiques détectées.
- *Nombre total d’erreurs* : nombre d’erreurs détectées.
- *Nombre total d’avertissements* : nombre d’avertissements trouvés.
- *Utilisation maximale de la mémoire* : quantité maximale de mémoire que le [!DNL Upgrade Compatibility Tool] a atteinte lors de l’exécution.

Consultez l’exemple d’interface de ligne de commande suivant :

```
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

Vous pouvez obtenir la sortie du fichier JSON lors de l’exécution du [!DNL Upgrade Compatibility Tool] sur une interface de ligne de commande. Le fichier `JSON` contient exactement les mêmes informations que celles affichées sur la sortie [!DNL Upgrade Compatibility Tool] :

- Une liste des problèmes identifiés.
- Résumé de l’analyse.

Pour chaque problème rencontré, le rapport fournit des informations détaillées, telles que la gravité et la description du problème.

Pour exporter ce fichier `JSON` vers un autre dossier de sortie :

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Où les arguments sont les suivants :

- `<dir>` : répertoire d’installation d’Adobe Commerce.
- `[=JSON-OUTPUT-PATH]` : répertoire du chemin d’accès pour l’exportation du fichier de sortie `JSON`.

>[!NOTE]
>
> Le chemin d’accès par défaut au dossier de sortie est `var/output/[TIME]-results.json`.

## Rapport HTML

Vous pouvez obtenir le rapport HTML lors de l’exécution de l’outil sur une interface de ligne de commande ou via le [!DNL Site-Wide Analysis Tool]. Le rapport HTML contient également les éléments suivants :

- Une liste des problèmes identifiés.
- Résumé de l’analyse.

![Rapport HTML - Résumé &#x200B;](../../assets/upgrade-guide/uct-html-summary.png)

Vous pouvez facilement parcourir les problèmes identifiés lors de l’analyse de la [!DNL Upgrade Compatibility Tool].

Vous pouvez filtrer les événements affichés dans le rapport en fonction du niveau minimal d’événement (la valeur par défaut est `WARNING`).

Une liste déroulante se trouve dans le coin supérieur droit et vous permet de sélectionner un autre niveau. La liste des problèmes identifiés est filtrée en conséquence.

![Rapport HTML - Liste déroulante d’utilisation](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Les problèmes de niveau inférieur sont supprimés, mais vous recevez une notification afin d’être toujours au courant des problèmes identifiés par module.

Le rapport HTML comprend également quatre graphiques différents :

- **Modules par gravité de problème** : affiche la répartition de la gravité par module.
- **Fichiers par gravité de problème** : affiche la répartition de la gravité par fichier.
- **Modules classés par nombre total d’événements** : affiche les 10 modules les plus compromis en tenant compte des avertissements, des erreurs et des erreurs critiques.
- **Modules avec des tailles et des problèmes relatifs** : plus un module contient de fichiers, plus son cercle est grand. Plus un module présente de problèmes, plus son cercle apparaît en rouge.

Ces graphiques vous permettent d’identifier les modules les plus compromis et ceux qui nécessitent le plus de travail pour effectuer une mise à niveau.

![Rapport HTML - Diagrammes](../../assets/upgrade-guide/uct-html-diagrams.png)

Les diagrammes de rapports d’HTML sont également mis à jour en conséquence, à la seule exception de la `Modules with relative sizes and issues`, qui est générée avec la `min-issue-level` configurée à l’origine.

Si vous souhaitez afficher des résultats différents pour le diagramme `Modules with relative sizes and issues`, vous devez réexécuter la commande en fournissant une autre valeur pour l’option `--min-issue-level`.

![Rapport HTML - Diagramme de graphique à bulles](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Pour exporter ce rapport HTML vers un autre dossier de sortie :

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Où les arguments sont les suivants :

- `<dir>` : répertoire d’installation d’Adobe Commerce.
- `[=HTML-OUTPUT-PATH]` : répertoire du chemin d’accès pour l’exportation du fichier de sortie `.html`.

>[!NOTE]
>
> Le chemin d’accès par défaut au dossier de sortie est `var/output/[TIME]-results.html`.
