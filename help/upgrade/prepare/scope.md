---
title: Présentation de la portée de la mise à niveau
description: Découvrez les modifications rétrocompatibles dans une version qui peuvent avoir un impact sur les modules personnalisés Adobe Commerce ou les extensions tierces.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 9eeb0e3a1c75b25cc70b092d23f02ebfe355d6bd
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Présentation de la portée de la mise à niveau

Consultez les [notes de mise à jour](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) pour comprendre la portée d’une version, y compris les améliorations, les correctifs et les problèmes connus qui peuvent avoir un impact sur les modules tiers et personnalisés.

## Modifications non rétrocompatibles

Les versions d’Adobe Commerce peuvent contenir des modifications non rétrocompatibles. Consultez la documentation relative aux modifications non rétrocompatibles , consultez les éléments suivants :

- **[Principales modifications mises en évidence](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)**—Modifications ayant un impact majeur et nécessitant une explication détaillée et des instructions spéciales pour s’assurer que les modules tiers continuent à fonctionner.
- **[Référence de modification mineure](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** : documentation de référence générée à partir de la base de code qui décrit les modifications mineures apportées aux classes, à l’appartenance à une API, à la base de données, à l’injection de dépendance, aux interfaces, aux mises en page, au système et au schéma XSD.

## Extensions tierces

La nouvelle politique de compatibilité d’Adobe Commerce Marketplace garantit que les extensions répertoriées _toutes_ sont compatibles avec la dernière version publiée dans les 30 jours suivant la date de disponibilité générale. Pour cette raison, il est important d’obtenir vos extensions tierces, chaque fois que possible, via le Marketplace.

## Modules personnalisés

Tous les modules personnalisés doivent être comparés à la version cible vers laquelle vous souhaitez effectuer la mise à niveau. Il s’agit du processus de mise à niveau qui nécessite le plus de temps et de ressources. Lors de l’évaluation de vos modules personnalisés, vous devez rechercher les modifications non rétrocompatibles et tenir compte des nouvelles pratiques, telles que la décomposition du contrôleur. Pour en savoir plus à ce sujet, consultez les [notes de mise à jour](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview). Veillez également à suivre les [bonnes pratiques](https://developer.adobe.com/commerce/php/best-practices/extensions/) en matière de développement de modules.

## [!DNL Upgrade Compatibility Tool]

Le [!DNL Upgrade Compatibility Tool] est un outil de ligne de commande qui analyse votre instance à la recherche de problèmes de mise à niveau potentiels. Il recherche les problèmes entre la version actuelle que vous avez installée et la version vers laquelle vous essayez d’effectuer la mise à niveau.

L’utilisation de cet outil réduit l’effort requis de votre équipe pour comprendre la portée et l’impact d’une mise à niveau. Cela vous permet d’éviter les problèmes de code courants lors de la mise à niveau et fournit des instructions claires sur la façon de résoudre les problèmes identifiés. Il permet également de hiérarchiser les problèmes les plus critiques nécessaires pour garantir une mise à niveau réussie, ce qui permet de gagner du temps et de réduire les coûts.

Consultez les sections suivantes pour commencer à utiliser le [!DNL Upgrade Compatibility Tool]. Voir le [!DNL Upgrade Compatibility Tool] [guide](../upgrade-compatibility-tool/overview.md) pour plus de détails techniques et de cas d’utilisation avancés.

### Télécharger l’outil

Utilisez le compositeur pour télécharger l’outil. Il nécessite PHP 7.3 ou une version ultérieure, au moins 2 Go de RAM, Node.js (si vous vérifiez la compatibilité GraphQL), et une licence Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Exécution de l’outil

Pour analyser votre instance et rechercher des erreurs, des avertissements et des problèmes critiques :

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> L’argument `<dir>` correspond au répertoire dans lequel votre base de code est stockée. L’option `-c` compare votre base de code à la version spécifiée.

Pour identifier les problèmes les plus critiques à résoudre par votre équipe, procédez comme suit :

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Voici d’autres options à utiliser avec cette commande :

- `--ignore-current-version-compatibility-issues` : supprime tous les problèmes critiques, erreurs et avertissements connus de votre version actuelle. Il fournit uniquement des erreurs par rapport à la version que vous essayez de mettre à niveau.

- `--min-issue-level` : permet de définir le niveau de problème minimal afin de ne classer par priorité que les problèmes les plus importants de la mise à niveau. Les options sont avertissement, erreur et critique dans l’ordre croissant de gravité.

- `-m | [=MODULE-PATH]` : si vous souhaitez analyser uniquement un fournisseur, un module ou même un répertoire spécifique, vous pouvez également spécifier le chemin comme option.

- `--vanilla-dir` : vous permet de vérifier le code de base pour toute implémentation non standard de fonctionnalités ou de personnalisations. Il est important de les nettoyer au préalable. Une instance classique de votre version est automatiquement téléchargée pour référence.

  >[!NOTE]
  >
  > Vous pouvez également le faire à l’aide de la commande `core:code:changes` dans l’outil .)

### Analyse de la sortie

Le [!DNL Upgrade Compatibility Tool] exporte un fichier JSON identifiant le code ou les modules affectés, la gravité et une description du problème pour chaque problème qu’il rencontre. Il génère également un rapport de synthèse avec un score de complexité, ce qui permet à votre équipe de comprendre globalement ce qu’il faut faire pour mettre à niveau à la dernière version. Plus le score de complexité est faible, plus il est facile d’effectuer la mise à niveau.

La sortie suivante présente un exemple de rapport de synthèse :

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

### Conseils et astuces

Tous les problèmes identifiés par l’outil sont répertoriés dans le rapport avec des codes d’erreur spécifiques. Utilisez la [référence du message d’erreur](../upgrade-compatibility-tool/error-messages.md) pour obtenir plus de détails sur chaque problème. Adobe fournit également des suggestions pour résoudre chaque type de problème afin que vous puissiez planifier vos étapes de résolution.

Utilisez le rapport pour estimer la quantité d’effort nécessaire pour mettre à jour votre code pour la mise à niveau. Selon votre expérience, vous pouvez estimer l’effort de mise à niveau requis en fonction du nombre total de problèmes identifiés et de leur gravité. Puisqu’il s’agit d’un outil de ligne de commande, vous pouvez l’incorporer dans des suites de tests automatisés et de vérifications de code, et utiliser la sortie JSON pour générer vos rapports.

Nous vous recommandons d’enregistrer les résultats de chaque projet de mise à niveau afin de pouvoir comparer les résultats des mises à niveau ultérieures aux résultats précédents. Avec une utilisation continue, vous commencerez à avoir une idée précise du niveau d’effort nécessaire pour passer à la version suivante à partir du rapport de synthèse fourni par l’outil.

Nous vous recommandons également d’exécuter l’outil régulièrement pendant que vous travaillez sur la mise à niveau pour avoir une visibilité sur votre progression. Le nombre de problèmes doit diminuer à mesure que vous les corrigez. Cela permet également à votre équipe de décider de la meilleure approche pour distribuer le travail.

Le [!DNL Upgrade Compatibility Tool] continue d’être amélioré et les prochaines versions incluront des fonctionnalités telles que des correctifs automatiques pour vous aider à résoudre les problèmes le plus rapidement possible. Les dernières améliorations publiées en janvier 2022 incluent des tests de compatibilité PHP 8.1 et des fonctionnalités de visualisation HTML qui vous aident à identifier rapidement les domaines qui peuvent nécessiter davantage d’efforts de mise à niveau.
