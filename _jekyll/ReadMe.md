---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Vue d’ensemble

Ce projet comprend plusieurs tâches Rake pour automatiser divers aspects du workflow, tels que la génération de données pour les actualités, le rendu de fichiers modèles, l’optimisation des images et la génération de cartes. Vous trouverez ci-dessous les descriptions et les instructions d’utilisation de chaque tâche de parcours définie dans le fichier de acquisition.

## Rétablir les tâches

### `render`

Rend les fichiers modèles dans le répertoire `_jekyll/templates` avec les données de `_jekyll/_data/`. Le résultat se trouve dans le répertoire `help/includes/templated`.

**Utilisation :**

```sh
rake render
```

### `image_optim`

Optimise les images dans les fichiers non validés modifiés. Pour les autres images, utilisez l’argument `path` pour spécifier le répertoire ou le fichier.

**Utilisation :**

```sh
rake image_optim
```

**Avec argument `path` :**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Génère des données pour un résumé des actualités. La période par défaut est depuis la dernière mise à jour. Vous pouvez spécifier une période différente à l’aide de l’argument `since`.

**Utilisation :**

```sh
rake whatsnew
```

**Avec argument `since` :**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Génère des données pour un résumé des actualités dans les bonnes pratiques. La période par défaut est depuis la dernière mise à jour. Vous pouvez spécifier une période différente à l’aide de l’argument `since`.

**Utilisation :**

```sh
rake whatsnew_bp
```

**Avec argument `since` :**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Génère une carte des régions Azure. Le fichier de données d’entrée doit être placé dans `_jekyll/tmp/azure-regions.json`. Le résultat sera trouvé dans `_jekyll/tmp/azure-regions.svg`. Notez que vous devez installer Python, [PyGMT](https://www.pygmt.org/latest/install.html) et [pdf2svg](https://formulae.brew.sh/formula/pdf2svg).

**Utilisation :**

```sh
rake azure_regions
```

## Conditions préalables

- Ruby et Bundler installés.
- Astuces requises spécifiées dans le fichier Gemfile.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) et [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) pour la tâche `azure_regions`.

## Configuration

1. Installez les gems requis :

   ```sh
   bundle install
   ```

2. Assurez-vous que Python, PyGMT et pdf2svg sont installés pour la tâche `azure_regions`. Pour plus d’informations sur la configuration, consultez la documentation dans les commentaires à l’adresse [_scripts/azure_regions.py](_scripts/azure_regions.py).
