---
title: Présentation de la portée de la mise à niveau
description: Découvrez les modifications incompatibles en amont dans une version pouvant avoir un impact sur les modules personnalisés Adobe Commerce ou les extensions tierces.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Comprendre la portée de la mise à niveau

Passez en revue les [notes de mise à jour](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) pour comprendre la portée d’une version, y compris les améliorations, les correctifs de bogues et les problèmes connus qui peuvent avoir un impact sur les modules tiers et personnalisés.

## Modifications incompatibles avec l’arrière

Les versions d’Adobe Commerce peuvent contenir des modifications incompatibles avec le passé. Consultez notre documentation sur les modifications incompatibles avec l’arrière-plan, voir ce qui suit :

- **[Changements majeurs ](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** : modifications ayant un impact majeur et nécessitant une explication détaillée et des instructions spéciales pour garantir que les modules tiers continuent à fonctionner.
- **[Référence des modifications mineures](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** : documentation de référence générée à partir de la base de code qui décrit les modifications mineures apportées aux classes, à l’appartenance à l’API, à la base de données, à l’injection de dépendances, aux interfaces, aux mises en page, au système et au schéma XSD.

## Extensions tierces

La nouvelle politique de compatibilité d’Adobe Commerce Marketplace garantit que _toutes_ les extensions répertoriées sont compatibles avec la dernière version publiée dans les 30 jours suivant la date de disponibilité générale. Pour cette raison, il est important d’obtenir vos extensions tierces, chaque fois que cela est possible, via le Marketplace.

## Modules personnalisés

Tous les modules personnalisés doivent être comparés à la version cible vers laquelle vous souhaitez effectuer la mise à niveau. Il s’agit du processus de mise à niveau qui nécessite le plus de temps et de ressources. Lors de l’évaluation de vos modules personnalisés, vous devez rechercher des modifications incompatibles avec le passé et être conscient des nouvelles pratiques, telles que la décomposition du contrôleur. Vous pouvez en savoir plus à ce sujet dans les [notes de mise à jour](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Assurez-vous également de suivre les [bonnes pratiques](https://developer.adobe.com/commerce/php/best-practices/extensions/) pour le développement de module.

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] est un outil de ligne de commande qui analyse votre instance pour détecter d’éventuels problèmes de mise à niveau. Il recherche les problèmes entre la version actuelle que vous avez installée et la version vers laquelle vous essayez de mettre à niveau.

L’utilisation de cet outil réduit les efforts requis de votre équipe pour comprendre la portée et l’impact d’une mise à niveau. Elle vous permet d’éviter les problèmes de code courants lors de la mise à niveau et fournit des instructions claires sur la manière de résoudre les problèmes identifiés. Il permet également de hiérarchiser les problèmes les plus critiques nécessaires pour assurer une mise à niveau réussie, ce qui permet de gagner du temps et de réduire les coûts lors de la mise à niveau.

Consultez les sections suivantes pour commencer à utiliser [!DNL Upgrade Compatibility Tool]. Consultez le [!DNL Upgrade Compatibility Tool] [guide](../upgrade-compatibility-tool/overview.md) pour plus de détails techniques et des cas pratiques avancés.

### Téléchargement de l’outil

Utilisez le compositeur pour télécharger l’outil. Il requiert PHP 7.3 ou une version ultérieure, au moins 2 Go de mémoire vive, Node.js (si vous vérifiez la compatibilité avec GraphQL) et une licence Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Exécution de l’outil

Pour analyser votre instance et rechercher les erreurs, les avertissements et les problèmes critiques :

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> L’argument `<dir>` est le répertoire dans lequel votre base de code est stockée. L’option `-c` compare votre base de code à la version spécifiée.

Pour identifier les problèmes les plus critiques à résoudre par votre équipe :

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Voici d’autres options à utiliser avec cette commande :

- `--ignore-current-version-compatibility-issues` : supprime tous les problèmes critiques, erreurs et avertissements connus par rapport à votre version actuelle. Il ne fournit que des erreurs par rapport à la version que vous essayez de mettre à niveau.

- `--min-issue-level` : vous permet de définir le niveau de problème minimum pour vous aider à ne classer par priorité que les problèmes les plus importants de votre mise à niveau. Les options sont avertissement, erreur et critique dans l’ordre croissant de gravité.

- `-m | [=MODULE-PATH]` : si vous souhaitez analyser uniquement un certain fournisseur, module ou même répertoire, vous pouvez également spécifier le chemin d’accès comme option.

- `--vanilla-dir` : permet de vérifier le code principal pour toute mise en oeuvre non standard de fonctionnalités ou de personnalisations. Il est important de les nettoyer au préalable. Une instance Vanilla de votre version est automatiquement téléchargée à titre de référence.

  >[!NOTE]
  >
  > Cela peut également être effectué avec la commande `core:code:changes` de l’outil).

### Analyse de la sortie

[!DNL Upgrade Compatibility Tool] exporte un fichier JSON qui identifie le code ou les modules concernés, la gravité et une description du problème pour chaque problème rencontré. Il génère également un rapport récapitulatif avec un score de complexité, qui permet à votre équipe de comprendre approximativement ce qu’il faut pour effectuer la mise à niveau vers la dernière version. Plus le score de complexité est bas, plus il est facile d’effectuer la mise à niveau.

Le résultat suivant montre un exemple de rapport récapitulatif :

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Conseils et conseils

Tous les problèmes identifiés par l’outil sont répertoriés dans le rapport avec des codes d’erreur spécifiques. Utilisez la [référence du message d’erreur](../upgrade-compatibility-tool/error-messages.md) pour obtenir plus de détails sur chaque problème. Adobe fournit également des suggestions pour corriger chaque type de problème afin que vous puissiez planifier vos étapes de correction.

Utilisez le rapport pour estimer le temps nécessaire à la mise à jour de votre code pour la mise à niveau. Selon votre expérience, vous pouvez estimer l’effort requis pour effectuer la mise à niveau en fonction du nombre total de problèmes identifiés et de la gravité des problèmes. Puisqu’il s’agit d’un outil de ligne de commande, vous pouvez l’incorporer dans des suites de tests et de contrôles de code automatisés et utiliser la sortie JSON pour générer vos rapports.

Nous vous recommandons d’enregistrer les résultats de chaque projet de mise à niveau afin de comparer les résultats futurs de la mise à niveau aux résultats précédents. Grâce à une utilisation continue, vous commencerez à développer une bonne idée du niveau d’effort nécessaire pour effectuer la mise à niveau vers la version suivante, juste à partir du rapport de synthèse fourni par l’outil.

Nous vous recommandons également d’exécuter l’outil régulièrement lors de l’exécution de la mise à niveau afin de bénéficier d’une bonne visibilité sur votre progression. Le nombre de problèmes doit diminuer au fur et à mesure que vous les corrigez. Cela permet également à votre équipe de décider de la meilleure approche pour distribuer le travail.

L’ [!DNL Upgrade Compatibility Tool] continue d’être amélioré et les prochaines versions incluront des fonctionnalités telles que des correctifs automatiques pour vous aider à résoudre les problèmes aussi rapidement que possible. Les dernières améliorations publiées en janvier 2022 comprennent des tests de compatibilité PHP 8.1 et des fonctionnalités de visualisation d’HTML qui vous aident à identifier rapidement les zones nécessitant plus d’efforts pour la mise à niveau.
