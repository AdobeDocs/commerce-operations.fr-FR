---
source-git-commit: 9994f486c38df4c0dc2ff477c48f3e8f3259aa9f
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---
# Vue d’ensemble

Ce projet comprend plusieurs tâches de création pour automatiser divers aspects du workflow, comme la génération de données pour les résumés d’actualités, le rendu des fichiers modélisés, l’optimisation des images et la génération de cartes. Vous trouverez ci-dessous les descriptions et les instructions d’utilisation de chaque tâche Rake définie dans le fichier Rakefile.

## Ratifier les tâches

### `render`

Effectue le rendu des fichiers modélisés dans le répertoire `_jekyll/templates` avec les données de `_jekyll/_data/`. Le résultat se trouve dans le répertoire `help/includes/templated`. Cette tâche conserve automatiquement les relations d’inclusion et l’horodatage après le rendu.

**Usage:**

```sh
rake render
```

**Fonctionnement :**
- Exécute le script de rendu pour générer les fichiers modèles
- Exécute `includes:maintain_all` pour mettre à jour les relations d’inclusion et les horodatages
- S’assure que toutes les métadonnées d’inclusion sont à jour après le rendu

### `image_optim`

Optimise les images dans les fichiers non validés modifiés. Pour les autres images, utilisez l’argument `path` pour spécifier le répertoire ou le fichier.

**Usage:**

```sh
rake image_optim
```

**Avec `path` argument :**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Génère des données pour un résumé d’actualités. Le délai par défaut est depuis la dernière mise à jour. Vous pouvez spécifier une autre période à l’aide de l’argument `since`.

**Usage:**

```sh
rake whatsnew
```

**Avec `since` argument :**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Génère des données pour un résumé des actualités au niveau des bonnes pratiques. Le délai par défaut est depuis la dernière mise à jour. Vous pouvez spécifier une autre période à l’aide de l’argument `since`.

**Usage:**

```sh
rake whatsnew_bp
```

**Avec `since` argument :**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Génère un mappage des régions Azure. Le fichier de données d’entrée doit être placé dans `_jekyll/tmp/azure-regions.json`. Le résultat se trouve dans `_jekyll/tmp/azure-regions.svg`. Notez que Python, [PyGMT](https://www.pygmt.org/latest/install.html) et [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) doivent être installés.

**Usage:**

```sh
rake azure_regions
```

### `includes:maintain_relationships`

Découvre et met à jour le fichier `include-relationships.yml` en analysant tous les fichiers Markdown du répertoire `help` pour rechercher les instructions d’inclusion à l’aide du `{{$include /help/_includes/filename.md}}` motif . Cette tâche conserve automatiquement les relations entre les fichiers de contenu principaux et leurs fichiers inclus.

**Usage:**

```sh
rake includes:maintain_relationships
```

**Fonctionnement :**
- Lit la liste des fichiers d’inclusion existants dans le répertoire `help/_includes`
- Effectue des recherches dans tous les fichiers Markdown principaux pour trouver ceux qui font référence à chacun d’eux
- Utilise le modèle de `{{$include /help/_includes/filename.md}}` pour identifier les références
- Met à jour le fichier `include-relationships.yml` avec les relations découvertes
- Fournit un résumé des modifications apportées et identifie les inclusions non référencées

### `includes:maintain_timestamps`

Conserve les horodatages d’inclusion en ajoutant les derniers horodatages de modification de fichier d’inclusion aux fichiers principaux. Cette tâche lit le fichier `include-relationships.yml`, vérifie l’historique Git de chaque fichier d’inclusion et ajoute ou met à jour les horodatages à la fin des fichiers principaux.

**Usage:**

```sh
rake includes:maintain_timestamps
```

**Fonctionnement :**
- Les charges incluent les relations de `include-relationships.yml`
- Pour chaque fichier principal, trouve la dernière date de validation Git parmi ses fichiers d’inclusion
- Ajoute ou met à jour des commentaires HTML avec horodatage à la fin des fichiers principaux
- Utilise le format : `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Fournit une sortie détaillée indiquant les fichiers d’inclusion qui ont été vérifiés et leurs dates et heures

**Exemple de sortie :**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

Tâche pratique qui s’exécute à la fois `includes:maintain_relationships` et `includes:maintain_timestamps` en séquence. Il s’agit de la méthode recommandée pour conserver les relations d’inclusion et les horodatages.

**Usage:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Recherche les fichiers d’inclusion dans le répertoire `help/_includes` qui ne sont référencés par aucun fichier Markdown. Cela permet d’identifier les fichiers d’inclusion orphelins qui peuvent être supprimés en toute sécurité.

**Usage:**

```sh
rake unused_includes
```

## Liste des tâches disponibles

Pour afficher toutes les tâches de classement disponibles avec leurs descriptions, utilisez :

```sh
rake --tasks
```

Pour plus d’informations sur une tâche spécifique, utilisez :

```sh
rake -T [task_name]
```

## Inclure les tâches de gestion

Toutes les tâches liées aux inclusions sont organisées sous l’espace de noms `includes` pour une meilleure organisation :

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Inclure le format de fichier de relations

Le fichier `include-relationships.yml` suit les relations entre les fichiers de contenu principaux et leurs fichiers inclus. Ce fichier est automatiquement conservé par la tâche Rake `maintain_include_relationships`, qui détecte les relations en lisant les fichiers d’inclusion existants et en recherchant les fichiers principaux qui y font référence.

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
- Gemmes requises spécifiées dans le fichier Gemme.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) et [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) pour la tâche `azure_regions`.

## Configuration

1. Installez les gemmes requises :

   ```sh
   bundle install
   ```

2. Assurez-vous que Python, PyGMT et pdf2svg sont installés pour la tâche `azure_regions`. Pour plus d’informations sur la configuration, consultez la documentation dans les commentaires à l’adresse [_scripts/azure_regions.py](_scripts/azure_regions.py).
