---
source-git-commit: 7f23a1b123d2ca2e1d116eb66344a67cfe45e409
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 3%

---
# Documentation technique opérationnelle d’Adobe Commerce

Nous acceptons les contributions de la communauté ainsi que des employés d’Adobe qui ne font pas partie des équipes de documentation.

## Points d’extension de pré-validation pour l’optimisation des images

Ce référentiel comprend des hooks de prévalidation automatisés qui optimisent les images avant validation. **Tous les contributeurs doivent activer ces raccordements** afin d’assurer une optimisation cohérente des images et une taille de référentiel réduite.

### Configuration rapide

Après avoir cloné le référentiel, exécutez :

```bash
.githooks/setup-hooks.sh
```

### Ce que font les crochets

- Détecter automatiquement les fichiers image intermédiaires (PNG, JPG, JPEG, GIF, SVG)
- Exécutez `image_optim` pour compresser et optimiser les images.
- Réévaluation automatique des images optimisées
- Vérifiez que toutes les images validées sont correctement optimisées.

### Avantages

- Taille réduite du référentiel
- Chargement plus rapide des pages pour la documentation
- Qualité d’image cohérente pour tous les contributeurs et contributrices
- Aucune optimisation manuelle requise

Pour obtenir des instructions détaillées sur la configuration, le dépannage et la configuration, voir [`.githooks/README.md`](.githooks/README.md).

## Code de conduite d’Adobe Open Source

Ce projet respecte le [Code de conduite d’Adobe Open Source](code-of-conduct.md) ou le [Code de conduite .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Pour plus d’informations, consultez l’article [Contribution](contributing.md).

## À propos de vos contributions au contenu d’Adobe

Consultez le Guide du contributeur aux documents Adobe [](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

La façon dont vous contribuez dépend de qui vous êtes et du type de changements que vous souhaitez apporter :

### Modifications mineures

Si vous contribuez à des mises à jour mineures, consultez l’article et cliquez sur la zone de commentaires qui s’affiche au bas de l’article, cliquez sur **Options de commentaires détaillées**, puis cliquez sur **Suggérer une modification** pour accéder au fichier source Markdown sur GitHub. Utilisez l’interface utilisateur GitHub pour effectuer vos mises à jour. Pour plus d’informations[ consultez le guide du contributeur aux ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)documents Adobe .

Les modifications ou précisions mineures que vous apportez aux documents et aux exemples de code dans ce référentiel sont soumises aux conditions d’utilisation d’Adobe.

### Modifications majeures ou nouveaux articles des membres de la communauté

Si vous faites partie de la communauté Adobe et que vous souhaitez rédiger un nouvel article ou apporter des modifications majeures, utilisez l’onglet Problèmes du référentiel Git pour soumettre un problème et commencer une conversation avec l’équipe de documentation. Une fois que vous avez accepté un plan, vous devez travailler avec un employé pour vous aider à introduire ce nouveau contenu en utilisant à la fois les référentiels publics et privés.

### Modifications majeures apportées par les employés d’Adobe

Si vous êtes rédacteur technique, responsable de programme ou développeur au sein de l’équipe produit d’une solution Adobe Experience Cloud et qu’il vous incombe de contribuer ou de rédiger des articles techniques, vous devez utiliser le référentiel privé à l’adresse `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Outils et configuration

Les contributeurs de la communauté peuvent utiliser l’interface utilisateur de GitHub pour apporter des modifications mineures, ou dupliquer le référentiel pour apporter des contributions majeures.

Pour plus d’informations, consultez le Guide du contributeur aux documents Adobe [](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

## Comment utiliser Markdown pour formater votre rubrique

Tous les articles de ce référentiel utilisent GitHub Flavored Markdown. Si vous ne connaissez pas Markdown, voir :

- [Principes de base de Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [Aide-mémoire imprimable Markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modèles

Pour certaines rubriques, nous utilisons des fichiers de données et des modèles pour générer du contenu publié. Les cas d’utilisation de cette approche sont les suivants :

- Publication de grands ensembles de contenu généré par programmation
- Fournir une source unique de vérité aux clients sur plusieurs systèmes qui nécessitent des formats de fichiers lisibles par machine, tels que YAML, pour l’intégration (par exemple, outil d’analyse à l’échelle du site)

Voici quelques exemples de contenu modélisé, sans s’y limiter :

- [Référence des outils de l’interface de ligne de commande](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [Tables de disponibilité des produits](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [Tableaux de la configuration requise](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Générer le contenu modélisé

En règle générale, la plupart des auteurs et des autrices n’ont besoin d’ajouter qu’une version aux tableaux Disponibilité du produit et Configuration requise . La maintenance de tous les autres contenus modélisés est automatisée ou gérée par un membre de l’équipe dédié. Ces instructions sont destinées à la plupart des rédacteurs.

>**REMARQUE :**
>
>- La génération de contenu modélisé nécessite de travailler sur la ligne de commande dans un terminal.
>- Ruby doit être installé pour exécuter le script de rendu. Voir [_jekyll/.ruby-version](_jekyll/.ruby-version) pour la version requise.

Pour obtenir une description de la structure de fichiers pour le contenu modélisé, reportez-vous aux sections suivantes :

- `_jekyll` : contient des rubriques modélisées et les ressources requises.
- `_jekyll/_data` : contient les formats de fichiers lisibles par machine utilisés pour le rendu des modèles
- `_jekyll/templated` : contient les fichiers de modèle basés sur HTML utilisant le langage de modèle Liquid
- `help/_includes/templated` : contient la sortie générée pour le contenu modélisé au format de fichier `.md` afin qu&#39;il puisse être publié dans les rubriques Experience League ; le script de rendu écrit automatiquement la sortie générée dans ce répertoire pour vous

Pour mettre à jour le contenu modélisé :

1. Dans l’éditeur de texte, ouvrez un fichier de données dans le répertoire `/jekyll/_data`. Par exemple :

   - [Tables de disponibilité des produits](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) : `/jekyll/_data/product-availability.yml`
   - [Tables de configuration requise](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) : `/jekyll/_data/system-requirements.yml`

1. Utilisez la structure YAML existante pour créer des entrées.

   Par exemple, pour ajouter une version d’Adobe Commerce aux tableaux de disponibilité des produits, ajoutez ce qui suit à chaque entrée dans les sections `extensions` et `services` du fichier `/jekyll/_data/product-availability.yml` (modifiez les numéros de version si nécessaire) :

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Accédez au répertoire `_jekyll`.

   ```bash
   cd _jekyll
   ```

1. Générez le contenu modélisé et écrivez la sortie dans le répertoire `help/_includes/templated`.

   ```bash
   rake render
   ```

   >**REMARQUE :** vous devez exécuter le script à partir du répertoire `_jekyll`. Si c’est la première fois que vous exécutez le script, vous devez d’abord installer les dépendances Ruby avec la commande `bundle install`.

1. Revenez au répertoire `root`.

   ```bash
   cd ..
   ```

1. Vérifiez que les fichiers `help/_includes/templated` attendus ont été modifiés.

   ```bash
   git status
   ```

   Vous devriez voir une sortie similaire à ce qui suit :

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Envoyez vos modifications.

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Consultez la documentation Jekyll pour plus d’informations sur [Fichiers de données](https://jekyllrb.com/docs/datafiles), [Filtres liquides](https://jekyllrb.com/docs/liquid/filters/) et d’autres fonctionnalités.
