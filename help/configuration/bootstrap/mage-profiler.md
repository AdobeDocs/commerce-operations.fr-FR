---
title: Activer le profilage
description: En savoir plus sur l’activation de MAGE Profiler pour l’utiliser avec vos outils d’analyse.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Activer le profilage

Avec le profilage Commerce, vous pouvez :

- Activez un profileur intégré.

  Vous pouvez utiliser un profileur intégré avec Commerce pour effectuer des tâches telles que l’analyse des performances. La nature du profilage dépend des outils d’analyse que vous utilisez. Nous prenons en charge plusieurs formats, y compris HTML. Lorsque vous activez le profileur, un fichier `var/profiler.flag` est généré pour indiquer que le profileur est activé et les configurations. Lorsqu’il est désactivé, ce fichier est supprimé.

- Affichez des graphiques de dépendance sur une page Commerce.

  Un _graphique de dépendance_ est une liste de dépendances d’objet et de toutes leurs dépendances, ainsi que de toutes les dépendances de ces dépendances, etc.

  Vous devriez être particulièrement intéressé par la liste des _dépendances inutilisées_, qui sont des objets qui ont été créés parce qu&#39;ils ont été demandés dans certains constructeurs, mais qui n&#39;ont jamais été utilisés (c&#39;est-à-dire qu&#39;aucune de leurs méthodes n&#39;a été appelée). Le temps et la mémoire consacrés par le processeur à la création de ces dépendances sont donc gaspillés.

Commerce fournit la fonctionnalité de base dans [`Magento\Framework\Profiler`][profiler].

Vous pouvez activer et configurer le profileur à l’aide d’une variable MAGE_PROFILER ou de la ligne de commande.

## Définir MAGE_PROFILER

Vous pouvez définir la valeur de `MAGE_PROFILER` de l’une des manières décrites dans la section [Définir la valeur des paramètres d’amorçage](../bootstrap/set-parameters.md).

`MAGE_PROFILER` prend en charge les valeurs suivantes :

- `1` pour activer la sortie d&#39;un profileur spécifique.

  Vous pouvez utiliser l’une des valeurs suivantes pour activer un profileur spécifique :

   - `csvfile` qui utilise [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Toute autre valeur (sauf `2`), y compris une valeur vide, qui utilise [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` d’activer les graphiques de dépendance.

  Les graphiques de dépendances s’affichent généralement au bas d’une page. La figure suivante montre une partie de la sortie :

  ![Graphiques de dépendances](../../assets/configuration/depend-graphs.png)

## Commandes de l’interface de ligne de commande

Vous pouvez activer ou désactiver le profileur à l’aide des commandes de l’interface de ligne de commande :

- `dev:profiler:enable <type>` active le profileur avec des `type` de `html` (par défaut) ou de `csvfile`. Lorsqu’elle est activée, une `var/profiler.flag` de fichier indicateur est créée.
- `dev:profiler:disable` désactive le profileur. Lorsqu&#39;il est désactivé, le fichier de drapeau `var/profiler.flag` est supprimé.

Pour activer les graphiques de dépendance, utilisez l’option variable .

**Pour activer ou désactiver le profileur** :

1. Connectez-vous à votre serveur Commerce.
1. Modifiez votre répertoire d’installation Commerce.
1. En tant que propriétaire du système de fichiers, activez le profileur :

   Pour activer le profileur à l’aide du type `html` et créer un fichier indicateur :

   ```bash
   bin/magento dev:profiler:enable html
   ```

   Pour activer le profileur à l’aide du type `csvfile` et créer un fichier indicateur :

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   La sortie est enregistrée dans `<project-root>/var/log/profiler.csv`. Le `profiler.csv` est remplacé à chaque actualisation de page.

   Pour désactiver le profileur et supprimer le fichier indicateur :

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
