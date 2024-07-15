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

Le flux de déploiement de production [!DNL Commerce] permet à un magasin d’atteindre des performances maximales.

## Installer les dépendances

Les fichiers `composer.json` et `composer.lock` gèrent les dépendances [!DNL Commerce] et installent la version appropriée pour chaque module. Vous devez installer les dépendances avant les [instructions d’injection de dépendance de prétraitement](#preprocess-dependency-injection-instructions) si vous envisagez de mettre à jour l’[outil d’auto-chargement](#update-the-autoloader).

Pour installer les dépendances [!DNL Commerce] :

```bash
composer install --no-dev
```

## Instructions d’injection de dépendance de prétraitement

Lorsque vous prétraitez et compilez des instructions d’injection de dépendance (DI), Magento :

* Lecture et traitement de toutes les configurations présentes
* Analyse les dépendances entre les classes
* Crée des fichiers générés automatiquement (y compris des proxies, des usines, etc.)
* Stocke les données compilées et la configuration dans un cache qui permet d’économiser jusqu’à 25 % du temps sur le traitement des demandes.

Pour prétraiter et compiler les instructions d’ID :

```bash
bin/magento setup:di:compile
```

## Mise à jour du chargeur automatique

Une fois la compilation terminée, vérifiez que [APCu est activé](../performance/software.md#php-settings) et mettez à jour l’outil d’auto-chargement :

Pour mettre à jour l’outil de chargement automatique :

>[!INFO]
>
>L’option `-o` convertit le chargement automatique PSR-0/4 en classmap pour obtenir un chargeur automatique plus rapide. L’option `--apcu` utilise APCu pour mettre en cache les classes trouvées/introuvables.

```bash
composer dump-autoload -o --apcu
```

Si vous prévoyez de mettre à jour l’outil de chargement automatique, vous devez exécuter les commandes suivantes dans l’ordre :

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

Le déploiement de contenu statique entraîne [!DNL Commerce] à effectuer les actions suivantes :

* Analyse de toutes les ressources statiques
* Réaliser la fusion, la minimisation et le regroupement de contenu
* Lecture et traitement des données de thème
* Analyse de la version de secours des thèmes
* Stocker tout le contenu traité et matérialisé dans un dossier spécifique pour une utilisation ultérieure

Si votre contenu statique n’est pas déployé, [!DNL Commerce] effectue toutes les opérations répertoriées à la volée, ce qui entraîne une augmentation significative du temps de réponse.

Vous pouvez utiliser diverses options pour personnaliser les opérations de déploiement en fonction de la taille de magasin et des besoins d’exécution. La stratégie de déploiement compacte est la plus courante. Voir [Stratégies de déploiement de fichiers statiques](../configuration/cli/static-view-file-strategy.md)

Pour déployer du contenu statique :

```bash
bin/magento setup:static-content:deploy
```

Cette commande permet au compositeur de recréer le mappage sur les fichiers de projet afin qu’ils se chargent plus rapidement.

## Définir le mode de production

>[!INFO]
>
>La définition du mode de production exécute automatiquement `setup:di:compile` et `setup:static-content:deploy`.

Enfin, vous devez placer votre magasin en mode Production. Le mode de production est spécifiquement optimisé pour des performances maximales de votre magasin. Elle désactive également toutes les fonctionnalités spécifiques aux développeurs. Vous pouvez le faire dans votre fichier `.htaccess` ou `nginx.conf` :

`SetEnv MAGE_MODE production`

Vous pouvez également déployer du contenu statique, compiler le contenu et définir le mode dans une seule commande d’interface de ligne de commande :

```bash
bin/magento deploy:mode:set production
```

La commande s’exécute en arrière-plan et ne permet pas de définir des options supplémentaires pour chaque étape spécifique.

## Autres actions de prélancement

Ces étapes sont recommandées, mais ne sont pas obligatoires. Vous pouvez les exécuter immédiatement avant de lancer votre boutique en mode de production. La liste comprend :

* Réindexez les données pour éviter toute incohérence des données de vos index.
* Videz le cache pour vous assurer qu’aucune donnée ancienne ou incorrecte n’est conservée dans le cache.
* Réchauffez le cache, qui appelle les pages de magasin les plus populaires ou les plus critiques à l’avance, de sorte que le cache pour elles est généré et stocké. Cette opération peut être effectuée avec n’importe quel moteur de recherche Internet ou manuellement, si vous disposez d’une petite boutique.
