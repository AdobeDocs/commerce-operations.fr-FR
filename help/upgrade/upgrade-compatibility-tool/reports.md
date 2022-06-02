---
title: '"[!DNL Upgrade Compatibility Tool] reports"'
description: Procédez comme suit pour exécuter la fonction [!DNL Upgrade Compatibility Tool] sur votre projet Adobe Commerce.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Rapports

{{commerce-only}}

L&#39;analyse a permis de déterminer si la variable [!DNL Upgrade Compatibility Tool] exporte un rapport contenant une liste de problèmes pour chaque fichier spécifiant sa gravité, son code d’erreur et sa description de l’erreur.

Voir l’exemple ci-dessous :

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Vérifiez les [Référence des messages d’erreur](../upgrade-compatibility-tool/error-messages.md) pour plus d’informations.

Le rapport contient également un résumé détaillé qui indique :

- *Version actuelle*: la version actuellement installée.
- *Version cible*: la version vers laquelle vous souhaitez effectuer la mise à niveau.
- *Heure d’exécution*: le temps nécessaire à l&#39;analyse pour construire le rapport (mm:ss).
- *Modules nécessitant une mise à jour*: le pourcentage de modules qui contiennent des problèmes de compatibilité et nécessitent une mise à jour.
- *Fichiers nécessitant une mise à jour*: le pourcentage de fichiers qui contiennent des problèmes de compatibilité et nécessitent une mise à jour.
- *Nombre total d’erreurs critiques*: le nombre d’erreurs critiques détectées.
- *Erreurs totales*: le nombre d’erreurs détectées.
- *Avertissements totaux*: le nombre d’avertissements trouvés.

Voir l’exemple ci-dessous :

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Par défaut, la variable [!DNL Upgrade Compatibility Tool] exporte le rapport dans 2 formats différents : `json` et `html`.

## Fichier JSON

Le fichier JSON contient exactement les mêmes informations que celles affichées en sortie :

- Liste des problèmes identifiés.
- Résumé de l&#39;analyse.

Pour chaque problème rencontré, le rapport fournit des informations détaillées telles que la gravité et la description du problème.

Pour exporter ce rapport dans un dossier de sortie différent, exécutez :

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Où les arguments sont les suivants :

- `<dir>`: Répertoire d’installation d’Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Répertoire de chemin d’accès pour l’exportation `.json` fichier de sortie.

>[!NOTE]
>
>Le chemin par défaut du dossier de sortie est `var/output/[TIME]-results.json`.

## Rapport HTML

Le fichier de HTML contient également le résumé de l’analyse et la liste des problèmes identifiés. Vous pouvez obtenir le rapport HTML lors de l’exécution de l’outil sur une interface de ligne de commande ou via le [!DNL Site-Wide Analysis Tool].

![Rapport HTML - Résumé](../../assets/upgrade-guide/uct-html-summary.png)

Vous pouvez facilement parcourir les problèmes identifiés au cours de la [!DNL Upgrade Compatibility Tool] analyse :

![Rapport HTML - Détails](../../assets/upgrade-guide/uct-html-details.png)

Le rapport HTML comprend également quatre graphiques différents :

- **Modules par gravité des problèmes**: Affiche la répartition de la gravité par modules.
- **Fichiers par gravité des problèmes**: Affiche la répartition de la gravité par fichiers.
- **Modules classés par nombre total de problèmes**: Affiche les 10 modules les plus compromis en prenant en compte les avertissements, les erreurs et les erreurs critiques.
- **Modules avec des tailles et des problèmes relatifs**: Plus un module contient de fichiers, plus son cercle est volumineux. Plus un module a de problèmes, plus son cercle rouge apparaît.

Ces graphiques vous permettent d’identifier (en un coup d’oeil) les parties les plus compromises et celles qui nécessitent davantage de travail pour effectuer une mise à niveau.

![Rapport HTML - Diagrammes](../../assets/upgrade-guide/uct-html-diagrams.png)

Vous pouvez filtrer les problèmes affichés sur le rapport en fonction du niveau de problème minimum. La valeur par défaut est `WARNING`.

Une liste déroulante dans le coin supérieur droit vous permet de sélectionner une autre option en fonction de vos besoins. La liste des problèmes identifiés sera filtrée en conséquence.

![Rapport HTML - Utilisation de la liste déroulante](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

Veuillez noter que les problèmes avec un niveau de problème inférieur sont supprimés mais que vous recevez une notification afin que vous soyez toujours conscient des problèmes identifiés par module.

Les diagrammes sont également mis à jour en conséquence, à l’exception du `Modules with relative sizes and issues`, qui est généré avec l’événement `min-issue-level` configuration initiale.

Si vous souhaitez afficher des résultats différents, vous devrez exécuter à nouveau la commande en fournissant une autre valeur pour la variable `--min-issue-level` .

![Rapport de HTML - Diagramme de graphique à bulles](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Pour exporter ce rapport dans un dossier de sortie différent, exécutez :

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Où les arguments sont les suivants :

- `<dir>`: Répertoire d’installation de {{site.data.var.ee}}.
- `[=HTML-OUTPUT-PATH]`: Répertoire de chemin d’accès pour l’exportation `.html` fichier de sortie.

>[!NOTE]
>
> Le chemin par défaut du dossier de sortie est `var/output/[TIME]-results.html`.
