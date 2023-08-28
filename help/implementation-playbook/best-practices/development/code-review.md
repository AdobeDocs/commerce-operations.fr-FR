---
title: Bonnes pratiques relatives à l’examen du code
description: Découvrez les bonnes pratiques de révision du code pour la phase de développement des projets Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Bonnes pratiques relatives à la révision du code pour Adobe Commerce

L’objectif principal de l’examen du code est de vérifier que les fonctionnalités mises en oeuvre répondent aux exigences de manière optimale, du point de vue des performances, de l’architecture et de la sécurité.

En outre, la révision du code est destinée à s’assurer que le code respecte les bonnes pratiques de développement d’Adobe Commerce, qu’il est facile à comprendre et à gérer et qu’il respecte les normes de codage. La plupart des normes de codage doivent être vérifiées automatiquement par les outils appropriés.

## Processus recommandé de révision du code

À un niveau général, le processus de révision du code doit se composer des étapes suivantes :

1. Branche des fonctionnalités de passage en caisse dans un environnement de développement local.
1. S’il s’est écoulé un certain temps depuis que le code a été soumis pour révision, fusionnez les dernières modifications de la branche cible (généralement la branche AQ) et envoyez les mises à jour à la branche de fonctionnalités distantes (le cas échéant).
1. Effectuez une révision de haut niveau pour vérifier que le code met en oeuvre toutes les exigences. En cas d’incohérences majeures, contactez le développeur pour obtenir des éclaircissements.
1. L’exécution du code est facultative, mais si vous doutez que le code fonctionne comme prévu ou s’il facilite l’efficacité du processus, vérifiez que la fonctionnalité mise en oeuvre fonctionne comme prévu pour les scénarios d’utilisation principaux. En cas de problèmes majeurs, arrêtez le processus de révision, puis rouvrez le ticket avec les commentaires appropriés.
1. Effectuez une révision approfondie pour vérifier que le code met en oeuvre toutes les exigences. En cas de problème, ajoutez les commentaires appropriés à la demande d’extraction et rouvrez le ticket.
1. Si tout semble correct, fusionnez la requête de tirage (ou transmettez-la au niveau de révision du code suivant si celui-ci a été établi).

Tenez également compte des points suivants lors de l’implémentation des processus de révision du code :

- L’examen du code est un outil principal de communication et de transfert des connaissances au sein d’une équipe. Même si une requête de tirage ne contient pas de problèmes majeurs et implémente la logique métier requise, vous pouvez l’utiliser comme une opportunité pour suggérer d’autres améliorations après sa fusion.

- En moyenne, l’examen du code ne devrait pas prendre plus de 10 à 20 % de l’effort de développement. Cela suppose que l&#39;équipe de développement soit composée d&#39;ingénieurs de haut niveau qui travaillent bien ensemble. Si la révision du code prend plus de temps, elle peut affecter le budget et la chronologie du projet.

- Résolvez les problèmes avec un effort excessif requis pour les révisions du code en identifiant la cause principale. En général, c&#39;est parce que les exigences sont mal traduites en billets de développement (en raison de problèmes de communication, d&#39;histoires d&#39;utilisateurs médiocres) ou parce que c&#39;est un problème de coaching. Dans le premier cas, la limitation recommandée consiste à s’assurer que les billets disposent de suffisamment d’informations pour que les membres de l’équipe puissent satisfaire efficacement aux exigences. Dans le deuxième cas, vous devrez peut-être ajuster la structure de l’équipe pour inclure plus d’ingénieurs expérimentés ou obtenir l’approbation en dehors du tutorat et de l’encadrement.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Que rechercher dans la révision du code

### Style

Le style peut être testé automatiquement en exécutant l’inspection PhpStorm (voir ci-dessous).

Assurez-vous de configurer [PHPMD et PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) et pour exécuter la fonction [Codage standard](https://github.com/magento/magento-coding-standard) de l’interface en ligne de commande (également ci-dessous). Il existe un certain chevauchement, mais les deux présentent également des tests uniques.

### Convention et structure

Les révisions des conventions et de la structure sont effectuées manuellement.

- La fonctionnalité de classe est-elle limitée à une seule responsabilité ?
- La structure de répertoires a-t-elle un sens ?
- Fonctionnalités exécutées au bon niveau (serveur, client, CSS, JS, base de données, structure, infrastructure).
- Le contrôle de version est-il correct ?
- Le code a-t-il l’air non conventionnel ou est-il en train d’essayer de contourner un problème de la mauvaise manière ?
- La convention d’affectation des noms pour le nom du module, le nom du module et le nom du référentiel est-elle correctement appliquée ?
- Vérifiez que les styles CSS globaux sont appliqués de manière réfléchie et qu’ils ne sont pas surutilisés.

### Complétude

Les révisions pour l’exhaustivité sont effectuées manuellement.

- Le code peut-il être activé ou désactivé par la configuration et tout le code nécessaire se comporte-t-il comme prévu ?
- Est-ce que toute la configuration mentionnée dans le ticket est présente ? Vérifiez la portée, le type de données, la validation, la traduction et les valeurs par défaut.
- La configuration est-elle toujours récupérée au niveau le plus bas possible (niveau d’affichage de la boutique, niveau du site web ou niveau global) ? La récupération de configuration doit correspondre à la définition de la portée dans la variable `system.xml` fichier .
- Tous les chemins dans le diagramme de flux de la spécification technique sont-ils pris en compte ? Toutes les autres spécifications techniques sont-elles couvertes ?
- Les listes de contrôle d’accès sont-elles définies pour la nouvelle fonctionnalité ?
- PhpDocs est-il clair ? Les messages de validation sont-ils clairs ?
- Le code est-il commenté ou le code de débogage s’affiche-t-il ?

### Performances

Les révisions des performances sont effectuées manuellement, ce qui peut être aidé par l’exécution du code en cas de doute.

- Les requêtes sont-elles exécutées dans une boucle ? Cette boucle peut se trouver en dehors des fichiers modifiés.
- Pouvez-vous repérer n&#39;importe lequel ? `cachable="false"` attributs ? Sont-elles correctement appliquées ?

### Sécurité

Les révisions pour la sécurité sont effectuées manuellement, ce qui peut être aidé par la recherche de texte. Une partie de la vérification de sécurité est gérée par des tests automatisés.

- Les exceptions sont-elles consignées si nécessaire ? Les types d’exceptions appropriés sont-ils utilisés ?
- Peut `around` les modules externes doivent être évités ?
- Les modules externes renvoient-ils les types de données corrects ?
- Pouvez-vous trouver des requêtes SQL brutes qui doivent être créées à l’aide de la couche d’abstraction de base de données ?
- Un nouveau type de données est-il exposé à tout type d’utilisateur, d’administrateur ou de frontal ? Cette exposition présente-t-elle un risque pour la sécurité ?
- Les données générées par l’utilisateur sont-elles validées ? Tout ce qui provient du navigateur est considéré comme généré par l’utilisateur, y compris les valeurs de cookie et les en-têtes de serveur.

### Confidentialité et RGPD

Révisions pour la confidentialité et [RGPD](../../../security-and-compliance/privacy/gdpr.md) sont effectuées manuellement.

- Le code traite-t-il les données ou les e-mails des clients ? Faites attention.
- Si ce code peut être exécuté dans une boucle, peut-il laisser passer les données client d’un cycle de boucle à un autre ?
- Les indicateurs d’un risque sont les imports, les traitements cron, les emails transactionnels et les gestionnaires de file d’attente par lots.
- Veillez à l’isolation des données utilisateur dans les boucles. Adobe conseille d’utiliser des usines ou des référentiels pour créer des modèles dans le cycle de boucle, qui ne sont pas accessibles en dehors de la boucle.

### Mentorat

Les révisions pour le tutorat sont effectuées manuellement.

- Recherchez des endroits où partager les connaissances dans le but d&#39;éduquer l&#39;équipe.
- Si votre commentaire est purement éducatif, mais n’est pas essentiel pour répondre aux normes, indiquez qu’il n’est pas obligatoire pour l’auteur de le résoudre.
- Si vous voyez quelque chose de bien, dites-le au développeur, en particulier quand il a très bien traité l&#39;un de vos commentaires. Les examens de code se concentrent souvent sur les erreurs, mais ils devraient aussi encourager et apprécier les bonnes pratiques. C&#39;est parfois encore plus précieux, en termes de tutorat, de dire à un développeur ce qu&#39;il a fait de bien plutôt que de leur dire ce qu&#39;il a fait de mal.

## Automatisation

Les développeurs peuvent utiliser l’automatisation pour passer en revue la compilation d’ID, le schéma de base de données, la validation de compositeur et la conformité aux normes de codage :

- Compilation d’ID : exécutez les commandes d’interface de ligne de commande suivantes pour voir si le code peut être compilé sans problème.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Schéma de base de données `whitelist.json`: exécutez la commande d’interface de ligne de commande suivante et validez que la variable `db_schema_whitelist.json` n’est pas ajouté ni modifié.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer validate : validation de la variable `composer.json` en exécutant la commande d’interface de ligne de commande suivante dans le répertoire contenant la variable `composer.json` fichier .

  ```bash
  composer validate
  ```

- Coding standard : installez et exécutez l’outil Coding Standard et exécutez-le par rapport à votre module. Le fichier suivant montre comment l’exécuter n’importe où en saisissant `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- Inspection PhpStorm

- Détecteur de copier/coller PHP PhpStorm
