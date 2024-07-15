---
title: Activation du profilage
description: En savoir plus sur l’activation du profileur MAGE à utiliser avec vos outils d’analyse.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Activation du profilage

Avec le profilage Commerce, vous pouvez :

- Activez un profileur intégré.

  Vous pouvez utiliser un profileur intégré avec Commerce pour exécuter des tâches telles que l’analyse des performances. La nature du profilage dépend des outils d’analyse que vous utilisez. Nous prenons en charge plusieurs formats, y compris HTML. Lorsque vous activez le profileur, un fichier `var/profiler.flag` est généré pour indiquer que le profileur est activé et les configurations. Lorsque cette option est désactivée, ce fichier est supprimé.

- Affichage des graphiques de dépendances sur une page Commerce.

  Un _graphique de dépendance_ est une liste de dépendances d’objets et de toutes leurs dépendances, ainsi que toutes les dépendances de ces dépendances, etc.

  Vous devriez être particulièrement intéressé par la liste des _dépendances inutilisées_, qui sont des objets qui ont été créés car ils ont été demandés dans un constructeur, mais n’ont jamais été utilisés (c’est-à-dire qu’aucune de leurs méthodes n’a été appelée). Par conséquent, le temps passé par le processeur et la mémoire pour créer ces dépendances est gaspillé.

Commerce fournit la fonctionnalité de base dans [`Magento\Framework\Profiler`][profiler].

Vous pouvez activer et configurer le profileur à l’aide d’une variable MAGE_PROFILER ou d’une ligne de commande.

## Définir MAGE_PROFILER

Vous pouvez définir la valeur de `MAGE_PROFILER` de n’importe quelle manière décrite dans [Définir la valeur des paramètres de bootstrap](../bootstrap/set-parameters.md).

`MAGE_PROFILER` prend en charge les valeurs suivantes :

- `1` pour activer la sortie d’un profileur spécifique.

  Vous pouvez utiliser l’une des valeurs suivantes pour activer un profileur spécifique :

   - `csvfile` qui utilise [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Toute autre valeur (sauf `2`), y compris une valeur vide, qui utilise [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` pour activer les graphiques de dépendances.

  Les graphiques de dépendance s’affichent généralement au bas d’une page. La figure suivante montre une partie de la sortie :

  ![Graphiques de dépendances](../../assets/configuration/depend-graphs.png)

## Commandes de ligne de commande

Vous pouvez activer ou désactiver le profileur à l’aide des commandes de l’interface de ligne de commande :

- `dev:profiler:enable <type>` active le profileur avec `type` de `html` (par défaut) ou `csvfile`. Une fois activé, un fichier flagfile `var/profiler.flag` est créé.
- `dev:profiler:disable` désactive le profileur. Lorsque cette option est désactivée, le fichier flagfile `var/profiler.flag` est supprimé.

Pour activer les graphiques de dépendance, utilisez l’option de variable .

**Pour activer ou désactiver le profileur** :

1. Connectez-vous à votre serveur Commerce.
1. Accédez au répertoire d’installation de Commerce.
1. En tant que propriétaire du système de fichiers, activez le profileur :

   Pour activer le profileur à l’aide du type `html` et créer un fichier flagfile :

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Pour activer le profileur à l’aide du type `csvfile` et créer un fichier flagfile :

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   La sortie est enregistrée dans `<project-root>/var/log/profiler.csv`. L’élément `profiler.csv` est remplacé à chaque actualisation de page.

   Pour désactiver le profileur et supprimer le fichier flagfile :

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
