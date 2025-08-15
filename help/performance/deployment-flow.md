---
title: Flux de déploiement
description: Découvrez les étapes nécessaires au déploiement d’Adobe Commerce dans un environnement de production.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Flux de déploiement

Le flux de déploiement en production [!DNL Commerce] permet à un magasin d’atteindre des performances maximales.

## Installer les dépendances

Les fichiers `composer.json` et `composer.lock` gèrent les dépendances [!DNL Commerce] et installent la version appropriée pour chaque package. Vous devez installer les dépendances avant [instructions d’injection de dépendance de prétraitement](#preprocess-dependency-injection-instructions) si vous prévoyez de mettre à jour le [autoloader](#update-the-autoloader).

Pour installer [!DNL Commerce] dépendances :

```bash
composer install --no-dev
```

## Instructions d’injection de dépendance de prétraitement

Lorsque vous prétraitez et compilez des instructions d’injection de dépendance (ID), Magento :

* Lit et traite toutes les configurations présentes.
* Analyse les dépendances entre les classes
* Crée des fichiers générés automatiquement (y compris les proxys, les usines, etc.)
* Stocke les données compilées et la configuration dans un cache qui permet de gagner jusqu’à 25 % du temps lors du traitement des requêtes

Pour prétraiter et compiler des instructions d’ID :

```bash
bin/magento setup:di:compile
```

## Mettre à jour le chargeur automatique

Une fois la compilation terminée, confirmez que [APCu est activé](../performance/software.md#php-settings) et mettez à jour le chargeur automatique :

Pour mettre à jour le chargeur automatique :

>[!INFO]
>
>L’option `-o` convertit le chargement automatique PSR-0/4 en classmap pour obtenir un chargeur automatique plus rapide. L’option `--apcu` utilise APCu pour mettre en cache les classes trouvées/introuvables.

```bash
composer dump-autoload -o --apcu
```

Si vous prévoyez de mettre à jour le chargeur automatique, vous devez exécuter les commandes suivantes dans l’ordre :

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Déploiement de contenu statique

Avec le déploiement de contenu statique, [!DNL Commerce] effectuez les actions suivantes :

* Analyse de toutes les ressources statiques
* Effectuer la fusion, la minimisation et le regroupement du contenu
* Lire et traiter les données de thème
* Analyse du thème de secours
* Stocker tout le contenu traité et matérialisé dans un dossier spécifique pour une utilisation ultérieure

Si votre contenu statique n’est pas déployé, [!DNL Commerce] effectue toutes les opérations répertoriées à la volée, ce qui entraîne une augmentation significative du temps de réponse.

Vous pouvez utiliser diverses options pour personnaliser les opérations de déploiement en fonction de la taille du magasin et des besoins en matière d’exécution. La plus courante est la stratégie de déploiement compacte. Voir [Stratégies de déploiement de fichiers statiques](../configuration/cli/static-view-file-strategy.md)

Pour déployer du contenu statique :

```bash
bin/magento setup:static-content:deploy
```

Cette commande permet au compositeur de recréer le mappage aux fichiers de projet afin qu’ils se chargent plus rapidement.

## Définir le mode de production

>[!INFO]
>
>La définition du mode en exploitation s’exécute automatiquement `setup:di:compile` et `setup:static-content:deploy`.

Enfin, vous devez placer votre boutique en mode Production. Le mode de production est spécifiquement optimisé pour optimiser les performances de votre boutique. Toutes les fonctionnalités spécifiques aux développeurs sont également désactivées. Vous pouvez le faire dans votre fichier `.htaccess` ou `nginx.conf` :

`SetEnv MAGE_MODE production`

Vous pouvez également déployer du contenu statique, compiler le contenu et définir le mode dans une seule commande d’interface de ligne de commande :

```bash
bin/magento deploy:mode:set production
```

La commande s’exécute en arrière-plan et ne vous permet pas de définir des options supplémentaires pour chaque étape spécifique.

## Autres actions de pré-lancement

Ces étapes sont recommandées, mais ne sont pas obligatoires. Vous pouvez les exécuter immédiatement avant de lancer votre boutique en mode production. La liste comprend :

* Réindexez les données pour éviter la présence de données incohérentes dans vos index.
* Videz le cache pour vous assurer qu’aucune donnée ancienne ou incorrecte n’y reste.
* Préchauffez le cache, qui indique à l’avance les pages de magasin les plus populaires ou les plus critiques, afin que le cache pour ces pages soit généré et stocké. Cette opération peut être effectuée avec n’importe quel robot d’exploration Internet ou manuellement, si vous disposez d’un petit magasin.
