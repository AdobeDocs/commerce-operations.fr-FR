---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---
# Vue d’ensemble

Ce projet utilise des tâches Rake pour automatiser des parties du workflow de documentation. La plupart des tâches sont partagées dans les référentiels de documents ExL Commerce et proviennent de la [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks) gem. Certaines tâches ci-dessous sont spécifiques à ce référentiel.

**Pour les tâches courantes (rendu des modèles, gestion des inclusions, optimisation/contrôle des images, génération du résumé Quoi de neuf ?), consultez le fichier README [adobe-comdox-exl-rake-tasks](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md).**

> Toutes `bundle exec rake` commandes ci-dessous doivent être exécutées à partir du répertoire `_jekyll/`, puisque c&#39;est là que se trouvent Gemfile et Rakefile.

## Tâches Rake spécifiques au référentiel

### `whatsnew_bp`

Génère des données pour un résumé des actualités au niveau des bonnes pratiques. Le délai par défaut est depuis la dernière mise à jour. Vous pouvez spécifier une autre période à l’aide de l’argument `since`.

**Usage:**

```sh
bundle exec rake whatsnew_bp
```

**Avec `since` argument :**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `get_released_versions`

Obtient les 10 dernières versions publiées à partir du référentiel `magento/magento2`. Nécessite [GitHub CLI](https://cli.github.com/) à installer et à authentifier.

**Usage:**

```sh
bundle exec rake get_released_versions
```

**Output :** génère des `tmp/core-release.txt` avec les noms et les dates des balises de publication.

### `first_merge_date`

Obtient la date de la première fusion dans une branche spécifiée. Nécessite [GitHub CLI](https://cli.github.com/) à installer et à authentifier.

**Usage:**

```sh
bundle exec rake first_merge_date base=develop
```

**Arguments:**

- `base` (obligatoire) : nom de la branche cible à vérifier pour les fusions.

## Liste des tâches disponibles

Pour afficher toutes les tâches de classement disponibles avec leurs descriptions, utilisez :

```sh
bundle exec rake --tasks
```

Pour plus d’informations sur une tâche spécifique, utilisez :

```sh
bundle exec rake -T [task_name]
```

## Inclure le format de fichier de relations

Le fichier `include-relationships.yml` suit les relations entre les fichiers de contenu principaux et leurs fichiers inclus. Ce fichier est automatiquement conservé par la tâche `includes:maintain_relationships` (consultez le fichier README [adobe-comdox-exl-rake-tasks](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) pour l’utilisation des tâches), qui détecte les relations en lisant les fichiers d’inclusion existants et en recherchant les fichiers principaux qui les référencent.

**Structure de fichier :**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Champs:**
- `metadata.last_updated` : date et heure de la dernière mise à jour
- `metadata.total_relationships` : nombre total de fichiers principaux avec inclusions
- `metadata.auto_discovered` : indique que le fichier a été généré automatiquement
- `metadata.discovery_date` : date de découverte initiale des relations
- `relationships` : mappage des fichiers principaux à leurs fichiers inclus

**Inclure le format d’instruction :**
Les fichiers de contenu principaux utilisent la syntaxe suivante pour inclure d’autres fichiers :

```markdown
{{$include /help/_includes/filename.md}}
```

## Conditions préalables

- Ruby et Bundler installés.
- Gemmes requises spécifiées dans le fichier Gem (les tâches courantes sont fournies par `adobe-comdox-exl-rake-tasks` ; la tâche `whatsnew` nécessite en outre `whatsup_github`).
- [interface de ligne de commande GitHub](https://cli.github.com/) pour les tâches `get_released_versions` et `first_merge_date`.

## Configuration

Installez les gemmes requises :

```sh
bundle install
```
