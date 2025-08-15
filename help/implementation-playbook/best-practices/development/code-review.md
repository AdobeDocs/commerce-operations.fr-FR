---
title: Bonnes pratiques relatives à la révision du code
description: Découvrez les bonnes pratiques relatives à la révision du code pour la phase de développement des projets Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 1ef78bce-2e69-4c95-a26e-1bf7196ce546
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---

# Bonnes pratiques en matière de révision du code pour Adobe Commerce

L’objectif principal de la révision du code est de s’assurer que les fonctionnalités implémentées répondent aux exigences de manière optimale du point de vue des performances, de l’architecture et de la sécurité.

En outre, la révision du code a pour but de s’assurer que le code répond aux bonnes pratiques de développement d’Adobe Commerce, est facile à comprendre et à gérer, et respecte les normes de codage. La plupart des normes de codage devraient être vérifiées automatiquement par des outils appropriés.

## Processus de révision du code recommandé

À un niveau élevé, le processus de révision du code doit comprendre les étapes suivantes :

1. Extrayez la branche de fonctionnalité dans l’environnement de développement local.
1. Si un certain temps s’est écoulé depuis l’envoi du code pour révision, fusionnez les dernières modifications de la branche cible (généralement la branche QA) et envoyez les mises à jour à la branche de fonctionnalité distante (le cas échéant).
1. Effectuez une révision de haut niveau pour vérifier que le code met en œuvre toutes les exigences. S’il existe des incohérences majeures, contactez l’équipe de développement pour obtenir des éclaircissements.
1. L’exécution du code est facultative, mais si vous avez des doutes sur le fonctionnement prévu du code ou s’il facilite l’efficacité du processus, testez que la fonctionnalité implémentée fonctionne comme prévu pour les principaux scénarios d’utilisation. En cas de problèmes majeurs, arrêtez le processus de révision, puis rouvrez le ticket avec les commentaires appropriés.
1. Effectuez une révision approfondie pour vérifier que le code met en œuvre toutes les exigences. En cas de problèmes, ajoutez les commentaires appropriés à la demande d’extraction et rouvrez le ticket.
1. Si tout semble correct, fusionnez la demande d’extraction (ou transmettez-la au niveau de révision du code suivant si celui-ci a été établi).

Tenez également compte des points suivants lors de la mise en œuvre des processus de révision du code :

- La révision du code est un outil essentiel pour la communication et le transfert de connaissances au sein d’une équipe. Même si une requête de tirage ne contient pas de problèmes majeurs et implémente la logique commerciale requise, vous pouvez l’utiliser comme une opportunité pour suggérer d’autres améliorations après sa fusion.

- En moyenne, la révision du code ne devrait pas prendre plus de 10 à 20 % de l’effort de développement. Cela suppose que l&#39;équipe de développement est composée d&#39;ingénieurs chevronnés qui travaillent bien ensemble. Si la révision du code prend plus de temps, cela peut affecter le budget et la chronologie du projet.

- Résolvez les problèmes à l’aide d’un effort excessif lors des révisions de code en identifiant la cause première. Habituellement, c&#39;est parce que les exigences sont mal traduites en billets de développement (en raison de problèmes de communication, de mauvaises histoires d&#39;utilisateurs) ou c&#39;est un problème de coaching. Dans le premier cas, il est recommandé de s’assurer que les tickets disposent de suffisamment d’informations pour que les membres de l’équipe puissent répondre efficacement aux exigences. Dans le deuxième cas, vous devrez peut-être ajuster la structure de l&#39;équipe pour inclure des ingénieurs plus expérimentés ou obtenir l&#39;approbation de l&#39;extérieur du mentorat et du coaching.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Éléments à rechercher dans la révision du code

### Style

Le style peut être testé automatiquement en exécutant l&#39;inspection PhpStorm (voir ci-dessous).

Veillez à configurer [PHPMD et PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) et à exécuter l’outil [Coding Standard](https://github.com/magento/magento-coding-standard) à partir de l’interface de ligne de commande (également ci-dessous). Il y a des chevauchements, mais les deux ont également des tests uniques.

### Convention et structure

Les révisions de la convention et de la structure sont effectuées manuellement.

- La fonctionnalité de classe est-elle limitée à une seule responsabilité ?
- La structure de répertoires a-t-elle un sens ?
- Les fonctionnalités sont-elles exécutées au niveau approprié (serveur, client, CSS, JS, base de données, framework, infrastructure) ?
- Le contrôle de version est-il correct ?
- Le code ne semble-t-il pas conventionnel ou essaie-t-il de contourner un problème de la mauvaise façon ?
- La convention d’affectation des noms de module, de package et de référentiel est-elle correctement appliquée ?
- Vérifiez que les styles CSS globaux sont appliqués de manière réfléchie et ne sont pas surutilisés.

### Exhaustivité

Les révisions d&#39;exhaustivité sont effectuées manuellement.

- Le code peut-il être activé ou désactivé par configuration et tout le code nécessaire se comporte-t-il comme prévu ?
- Toute la configuration mentionnée dans le ticket est-elle présente ? Vérifiez la portée, le type de données, la validation, la traduction et les valeurs par défaut.
- La configuration est-elle toujours récupérée au niveau le plus bas possible (niveau d’affichage du magasin, niveau du site web ou niveau global) ? La récupération de la configuration doit correspondre à la définition de l’étendue dans le fichier `system.xml`.
- Tous les chemins de l’organigramme de la spécification technique sont-ils couverts ? Toutes les autres spécifications techniques sont-elles couvertes ?
- Des listes de contrôle d’accès sont-elles définies pour la nouvelle fonctionnalité ?
- Les PhpDocs sont-ils clairs ? Les messages de validation sont-ils clairs ?
- Un code est-il commenté ou voyez-vous du code de débogage ?

### Performances

Les révisions des performances sont effectuées manuellement, ce qui peut être facilité par l’exécution du code en cas de doute.

- Les requêtes sont-elles exécutées en boucle ? Cette boucle peut se trouver en dehors des fichiers modifiés.
- Pouvez-vous repérer des attributs de `cachable="false"` ? Sont-elles correctement appliquées ?

### Sécurité

Les révisions pour la sécurité sont effectuées manuellement, ce qui peut être aidé par la recherche de texte. Une partie du contrôle de sécurité est assurée par des tests automatisés.

- Les exceptions sont-elles consignées lorsque nécessaire ? Les bons types d’exceptions sont-ils utilisés ?
- Les plug-ins `around` peuvent-ils être évités ?
- Les modules externes renvoient-ils les types de données corrects ?
- Pouvez-vous trouver des requêtes SQL brutes qui doivent être créées à l’aide de la couche d’abstraction de base de données ?
- Un nouveau type de données est-il exposé à un type d’utilisateur, d’administrateur ou de système frontal ? Cette exposition constitue-t-elle un risque pour la sécurité ?
- Les données générées par l’utilisateur sont-elles validées ? Tout ce qui provient du navigateur est considéré comme généré par l’utilisateur, y compris les valeurs de cookie et les en-têtes de serveur.

### Confidentialité et RGPD

Les révisions relatives à la confidentialité et au [RGPD](../../../security-and-compliance/privacy/gdpr.md) sont effectuées manuellement.

- Le code gère-t-il les données ou les e-mails des clients ? Faites particulièrement attention.
- Si ce code peut être exécuté en boucle, peut-il faire passer les données client d’un cycle de boucle à un autre ?
- Les indicateurs de risque sont les imports, les traitements cron, les e-mails transactionnels et les gestionnaires de file d&#39;attente par lots.
- Garantissez l’isolation des données utilisateur dans les boucles. Adobe conseille d&#39;utiliser des usines ou des référentiels pour créer des modèles dans le cycle de boucle, qui ne sont pas accessibles en dehors de la boucle.

### Mentorat

Les examens pour le mentorat sont effectués manuellement.

- Cherchez des endroits où partager des connaissances dans le but d&#39;éduquer l&#39;équipe.
- Si votre commentaire est purement pédagogique, mais pas essentiel au respect des normes, indiquez qu&#39;il n&#39;est pas obligatoire pour l&#39;auteur de le résoudre.
- Si vous voyez quelque chose d’intéressant, dites-le au développeur, en particulier lorsqu’il a répondu de manière satisfaisante à l’un de vos commentaires. Les révisions du code se concentrent souvent sur les erreurs, mais elles doivent également offrir des encouragements et une appréciation des bonnes pratiques. Il est parfois encore plus utile, en termes de mentorat, de dire à un développeur ce qu&#39;il a fait de bien que de lui dire ce qu&#39;il a fait de mal.

## Automatisation

Les développeurs peuvent utiliser l’automatisation pour examiner la compilation d’identifiants, le schéma de base de données, la validation du compositeur et la conformité aux normes de codage :

- Compilation du code : exécutez les commandes d&#39;interface de ligne de commande suivantes pour voir si le code peut être compilé sans problème.

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

- Schéma de base de données `whitelist.json` : exécutez la commande CLI suivante et vérifiez que le fichier `db_schema_whitelist.json` n&#39;est ni ajouté ni modifié.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer validate : valide le fichier `composer.json` en exécutant la commande CLI suivante dans le répertoire contenant le fichier `composer.json`.

  ```bash
  composer validate
  ```

- Norme de codage : installez et exécutez l&#39;outil Norme de codage et exécutez-le sur votre module. Le fichier suivant montre comment l’activer pour qu’il s’exécute n’importe où en saisissant `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- Inspection PhpStorm

- PhpStorm Détecteur de copier/coller PHP
