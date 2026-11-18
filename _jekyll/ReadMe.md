---
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
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%
---

# Vue d’ensemble

Ce projet utilise des tâches Rake pour automatiser des parties du workflow de documentation. La plupart des tâches sont partagées entre les référentiels de documents ExL Commerce et proviennent de la gemme [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks). Certaines tâches ci-dessous sont spécifiques à ce référentiel.

**Pour les tâches courantes (rendu des modèles, gestion des inclusions, optimisation/audit des images, génération du résumé Quoi de neuf), consultez le [fichier README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) adobe-comdox-exl-rake-tasks.**

> Toutes les commandes `bundle exec rake` ci-dessous doivent être exécutées à partir du répertoire `_jekyll/`, puisque c&#39;est là que se trouvent Gemfile et Rakefile.

## Tâches Rake spécifiques au référentiel

### `whatsnew_bp`

Génère des données pour un résumé des actualités au niveau des bonnes pratiques. Le délai par défaut est depuis la dernière mise à jour. Vous pouvez spécifier une période différente à l’aide de l’argument `since`.

**Utilisation :**

```sh
bundle exec rake whatsnew_bp
```

**Avec l’argument `since` :**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `whatsnew_consolidated`

Consolide les nouveaux tableaux publiés des projets de documentation Commerce configurés dans `help/_includes/automated/whatsnew/consolidated.md`.

```sh
bundle exec rake whatsnew_consolidated
```

Configurez les projets sous `whatsnew_consolidated.projects` dans [`_config.yml`](_config.yml). Chaque entrée nécessite un nom de référentiel, un titre de projet et une URL de site web HTTP(S) absolue :

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/en/docs/commerce
```

Déplacez les entrées pour modifier l’ordre des sections. Vous pouvez librement entrelacer des projets depuis les deux plateformes. Les noms de référentiel se terminant par `.en` utilisent le chemin d’accès source ExL, `help/_includes/templated/whats-new.md`. Tous les autres référentiels utilisent le chemin d’accès source DevSite, `src/pages/_includes/templated/whats-new.md`.

La tâche récupère les fichiers publics `main` de l’organisation GitHub `AdobeDocs`. Il affiche chaque titre de projet sous la forme d&#39;un en-tête en texte brut et introduit chaque tableau avec une phrase liant le titre du projet à la page d&#39;accueil de la documentation configurée dans `website` comme source des nouvelles mises à jour de la rubrique Nouveautés. Il utilise `Description | Type | Date/source` en-têtes de tableau dans l’ensemble. Pour les projets DevSite uniquement, les balises d’échappement `\<br/\>` deviennent `<br/>`. Dans le cas contraire, les lignes du corps, les doublons, les liens et l’ordre des lignes sources restent inchangés. Chaque source définit sa propre période.

Les projets dont le message de non-mise à jour est reconnu sont omis. Si chaque projet ne comporte aucune entrée, l’inclusion contient un message global de non-mise à jour. Les échecs de configuration, de récupération, d’analyse ou d’écriture échouent sans remplacer une inclusion existante.

La tâche ne planifie pas la génération ni ne met à jour les pages consommatrices.

La suite de tests ciblée comprend des tests de point d’entrée Rake qui chargent le fichier Rakefile `_jekyll` et s’exécutent via le bundle. Installez d’abord le bundle et le bundle `_jekyll` :

```sh
cd _jekyll && bundle install
```

Exécutez ensuite les tests à partir de la racine du référentiel :

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

Crée `help/_includes/automated/whatsnew/consolidated-feedback.md` en filtrant l’inclusion `help/_includes/automated/whatsnew/consolidated.md` locale existante.

```sh
bundle exec rake whatsnew_feedback
```

La tâche correspond à `Feedback` en tant que valeur Type complète séparée par des virgules, ignorant la casse et l&#39;espace environnant. Les types combinés tels que `Feedback, technical` sont inclus. Les mentions dans les descriptions, les liens source ou les noms de type partiels ne sont pas qualifiés.

Les lignes, doublons, en-têtes de projet en texte brut, les phrases sources si présentes et l’ordre du projet et des lignes correspondants restent inchangés. Les projets sans entrées correspondantes sont omis. Si rien ne correspond, la sortie contient un message global de non-retour.

L’entrée doit déjà exister. Exécutez `bundle exec rake whatsnew_consolidated` séparément lorsque vous souhaitez l&#39;actualiser. La tâche de retour d’informations ne récupère pas le contenu distant, ne lit pas la configuration du projet ou ne régénère pas ses entrées.

Une entrée manquante ou incorrecte échoue sans remplacer une inclusion filtrée existante. Le fichier d’entrée n’est jamais modifié et la sortie filtrée est publiée automatiquement.

### `get_released_versions`

Obtient les 10 dernières versions publiées du référentiel `magento/magento2`. Nécessite l’installation et l’authentification de [l’interface de ligne de commande GitHub](https://cli.github.com/).

**Utilisation :**

```sh
bundle exec rake get_released_versions
```

**Sortie :** génère `tmp/core-release.txt` avec les noms et les dates des balises de publication.

### `first_merge_date`

Obtient la date de la première fusion dans une branche spécifiée. Nécessite l’installation et l’authentification de [l’interface de ligne de commande GitHub](https://cli.github.com/).

**Utilisation :**

```sh
bundle exec rake first_merge_date base=develop
```

**Arguments :**

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

Le fichier `include-relationships.yml` effectue le suivi des relations entre les fichiers de contenu principaux et leurs fichiers inclus. Ce fichier est automatiquement conservé par la tâche `includes:maintain_relationships` (consultez le [README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) adobe-comdox-exl-rake-tasks pour l’utilisation des tâches), qui détecte les relations en lisant les fichiers d’inclusion existants et en recherchant les fichiers principaux qui les référencent.

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

**Champs :**
- `metadata.last_updated` : date et heure de la dernière mise à jour
- `metadata.total_relationships` : nombre total de fichiers principaux incluant
- `metadata.auto_discovered` : indique que le fichier a été généré automatiquement
- `metadata.discovery_date` : date de découverte initiale des relations
- `relationships` : mappage des fichiers principaux à leurs fichiers inclus

**Inclure le format d&#39;instruction :**
Les fichiers de contenu principaux utilisent la syntaxe suivante pour inclure d’autres fichiers :

```markdown
{{$include /help/_includes/filename.md}}
```

## Conditions préalables

- Ruby et Bundler installés.
- Gems obligatoires spécifiés dans le fichier Gem (les tâches courantes sont fournies par `adobe-comdox-exl-rake-tasks` ; la tâche `whatsnew` nécessite en outre `whatsup_github`).
- [Interface de ligne de commande GitHub](https://cli.github.com/) pour les tâches `get_released_versions` et `first_merge_date`.

## Configuration

Installez les gemmes requises :

```sh
bundle install
```
