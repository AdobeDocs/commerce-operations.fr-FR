---
source-git-commit: a6086afc0a1f099b62014ad61098a5a1dc9d4675
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Documentation technique d’Adobe Commerce

Nous acceptons les contributions de la communauté ainsi que des employés d’Adobe qui ne font pas partie des équipes de documentation.

## Adobe Ouvrir le code de conduite Source

Ce projet respecte le [Code de conduite d’Adobe Open Source](code-of-conduct.md) ou le [Code de conduite .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Pour plus d’informations, consultez l’article [Contribution](contributing.md).

## À propos de vos contributions pour Adobe du contenu

Voir le [Guide du contributeur de documents d’Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=fr).

Votre contribution dépend de qui vous êtes et du type de modifications que vous souhaitez apporter :

### Modifications mineures

Si vous contribuez à des mises à jour mineures, consultez l’article et cliquez sur la zone de commentaires qui s’affiche au bas de l’article, cliquez sur **Options de commentaires détaillées**, puis sur **Suggérer une modification** pour accéder au fichier source Markdown sur GitHub. Utilisez l’interface utilisateur de GitHub pour effectuer vos mises à jour. Pour plus d’informations, consultez le [Guide du contributeur à la documentation d’Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=fr) .

Les corrections mineures ou les clarifications que vous envoyez pour la documentation et les exemples de code dans ce référentiel sont couvertes par les conditions d’utilisation Adobe.

### Modifications majeures ou nouveaux articles des membres de la communauté

Si vous faites partie de la communauté Adobe et que vous souhaitez créer un nouvel article ou envoyer des modifications majeures, utilisez l’onglet Problèmes du référentiel Git pour soumettre un problème afin de démarrer une conversation avec l’équipe de documentation. Une fois que vous avez accepté un plan, vous devez collaborer avec un employé pour intégrer ce nouveau contenu par le biais d’une combinaison de travaux dans les référentiels publics et privés.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Modifications majeures par les employés d’Adobe

Si vous êtes rédacteur technique, chef de programme ou développeur de l’équipe produit d’une solution Adobe Experience Cloud et qu’il vous incombe de contribuer ou de rédiger des articles techniques, vous devez utiliser le référentiel privé à l’adresse `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Outils et configuration

Les contributeurs de la communauté peuvent utiliser l’interface utilisateur GitHub pour effectuer des modifications de base ou dupliquer le référentiel pour apporter des contributions majeures.

Pour plus d’informations, consultez le [Guide du contributeur de documents d’Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=fr) .

## Utilisation de Markdown pour formater votre rubrique

Tous les articles de ce référentiel utilisent GitHub Flavored Markdown. Si vous ne connaissez pas Markdown, voir :

* [ Concepts de base de Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Aide-mémoire imprimable pour le markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modèles

Pour certaines rubriques, nous utilisons des fichiers de données et des modèles pour générer du contenu publié. Voici quelques cas d’utilisation de cette approche :

* Publier de grands ensembles de contenu généré par programmation
* Fournir une source unique de vérité pour les clients sur plusieurs systèmes qui nécessitent des formats de fichiers lisibles par ordinateur, tels que YAML, pour l’intégration (par exemple, l’outil d’analyse à l’échelle du site)

Voici quelques exemples de contenu modélisé :

* [Référence des outils de l’interface de ligne de commande](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [ Tables de disponibilité des produits](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=fr)
* [ Tables de configuration système ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=fr)

### Générer du contenu modèle

En règle générale, la plupart des auteurs n’ont besoin que d’ajouter une version à la disponibilité du produit et aux tableaux de configuration système requise. La maintenance de tout autre contenu modèle est automatisée ou gérée par un membre dédié de l’équipe. Ces instructions sont destinées à la plupart des auteurs.

>**REMARQUE :**
>
>* La génération de contenu modèle nécessite de travailler sur la ligne de commande d’un terminal.
>* Ruby doit être installé pour exécuter le script de rendu. Voir [_jekyll/.ruby-version] (_jekyll/.ruby-version) pour connaître la version requise.

Pour obtenir une description de la structure de fichiers pour le contenu modèle, reportez-vous aux sections suivantes :

* `_jekyll` : contient des rubriques modélisées et les ressources requises
* `_jekyll/_data` : contient les formats de fichiers lisibles par l’ordinateur utilisés pour le rendu des modèles.
* `_jekyll/templated` : contient des fichiers de modèle basés sur l’HTML qui utilisent le langage de modèle Liquid.
* `help/_includes/templated` : contient la sortie générée pour le contenu modèle au format de fichier `.md` afin qu’il puisse être publié dans des rubriques Experience League ; le script de rendu écrit automatiquement la sortie générée dans ce répertoire pour vous.

Pour mettre à jour le contenu du modèle :

1. Dans votre éditeur de texte, ouvrez un fichier de données dans le répertoire `/jekyll/_data`. Par exemple :

   * [ Tables de disponibilité des produits ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=fr) : `/jekyll/_data/product-availability.yml`
   * [ Tables de configuration système ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=fr) : `/jekyll/_data/system-requirements.yml`

1. Utilisez la structure YAML existante pour créer des entrées.

   Par exemple, pour ajouter une version d’Adobe Commerce aux tables de disponibilité du produit, ajoutez le code suivant à chaque entrée des sections `extensions` et `services` du fichier `/jekyll/_data/product-availability.yml` (modifiez les numéros de version si nécessaire) :

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Accédez au répertoire `_jekyll`.

   ```
   cd _jekyll
   ```

1. Générez du contenu modèle et écrivez la sortie dans le répertoire `help/_includes/templated`.

   ```
   rake render
   ```

   >**REMARQUE :** Vous devez exécuter le script à partir du répertoire `_jekyll`. Si c’est la première fois que vous exécutez le script, vous devez d’abord installer les dépendances Ruby avec la commande `bundle install`.

1. Revenez au répertoire `root`.

   ```
   cd ..
   ```

1. Vérifiez que les fichiers `help/_includes/templated` attendus ont été modifiés.

   ```
   git status
   ```

   Vous devriez voir une sortie similaire à ce qui suit :

   ```
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Envoyez vos modifications.

   ```
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Pour plus d’informations sur les [fichiers de données](https://jekyllrb.com/docs/datafiles), les [filtres liquides](https://jekyllrb.com/docs/liquid/filters/) et d’autres fonctionnalités, consultez la documentation de Jekyll .
