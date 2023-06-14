---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---
# Documentation technique d’Adobe Commerce

Nous acceptons les contributions de notre communauté ainsi que des employés d’Adobe qui ne font pas partie des équipes de documentation.

## Adobe de code de conduite Open Source

Ce projet a adopté la méthode [Adobe de code de conduite Open Source](code-of-conduct.md) ou le [Code de conduite .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Pour plus d’informations, voir [Contribution](contributing.md) article.

## À propos de vos contributions pour Adobe du contenu

Voir [Guide du contributeur de documents d’Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Votre contribution dépend de qui vous êtes et du type de modifications que vous souhaitez apporter :

### Modifications mineures

Si vous contribuez à des mises à jour mineures, consultez l’article et cliquez sur le bouton **Modifier** lien dans l’article qui accède à la source GitHub de l’article. Ensuite, utilisez simplement l’interface utilisateur GitHub pour effectuer vos mises à jour. Voir le [Guide du contributeur pour Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) pour plus d’informations.

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

Voir [Guide du contributeur de documents d’Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) pour plus d’informations.

## Utilisation de Markdown pour formater votre rubrique

Tous les articles de ce référentiel utilisent GitHub Flavored Markdown. Si vous ne connaissez pas Markdown, voir :

* [Concepts de base de Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Markdown cheatsheet imprimable](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modèles

Le `_jekyll` contient des rubriques sous forme de modèles et les ressources requises.
Les modèles qui utilisent le langage de modèle Liquid résident dans la variable `_jekyll/templated` comme fichiers HTML.
Le `_jekyll/_data` contient des fichiers contenant les données utilisées pour le rendu des modèles.

Pour effectuer le rendu de tous les modèles :

1. Accédez au `_jekyll` répertoire .

   cd_jekyll

1. Exécutez le script de rendu.

```
_scripts/render
```

> **REMARQUE :** Vous devez exécuter le script à partir de la fonction `_jekyll` répertoire .
> **REMARQUE :** Ruby doit être installé pour exécuter ce script.

Le script exécute le rendu et écrit les modèles rendus dans le `help/_includes/templated` répertoire .

Pour plus d’informations sur la documentation Jekyll [Fichiers de données](https://jekyllrb.com/docs/datafiles), [Filtres liquides](https://jekyllrb.com/docs/liquid/filters/), ainsi que d’autres fonctionnalités.
