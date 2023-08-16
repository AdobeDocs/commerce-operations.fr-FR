---
title: Présentation du déploiement
description: Découvrez les stratégies de déploiement de l’application Commerce.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Présentation du déploiement

Ces rubriques abordent le processus de déploiement de l’application Commerce sur un site de production pour Adobe Commerce version 2.2 et ultérieure. Adobe recommande cette méthode de déploiement pour toute personne disposant d’un site de grande taille qui ne souhaite pas subir de temps d’arrêt pendant le déploiement.

Si vous déployez Commerce sur une seule machine et que vous pouvez tolérer un temps d’arrêt pendant le déploiement, reportez-vous à la section [Déploiement mono-machine](../deployment/single-machine.md).

## Déploiement du pipeline

Avec Commerce version 2.2, Adobe a été introduit. _déploiement du pipeline_ en tant que nouvelle méthode de déploiement en production avec un temps d’arrêt minimal. Ce processus de déploiement se produit sur différents systèmes et permet de maintenir des configurations cohérentes pour tous les systèmes de déploiement de pipeline. Il s’agit d’un modèle simple mais puissant qui vous permet de séparer les paramètres de configuration ordinaires des paramètres spécifiques au système (comme l’hôte et le port) ou des paramètres sensibles (tels que les noms et les mots de passe).

Pour utiliser le déploiement de pipeline, Adobe suppose que vous êtes :

- Intégrateur système expérimenté avec une excellente connaissance des options de configuration Adobe Commerce.
- Gestion d’un site Commerce volumineux (des milliers d’unités de gestion des stocks) et volonté de maintenir le temps d’arrêt du site de production à un minimum.
- Connaissances en programmation PHP.
- Expérience des méthodes de contrôle de code source.
- Votre code se trouve dans un référentiel de contrôle de code source. Dans ce guide, nous supposons que vous utilisez un référentiel basé sur Git.

### Réduction des temps d’arrêt

Lorsque vous déployez des ressources statiques et compilez du code sur une machine distincte de votre système de production, vous réduisez le temps d’arrêt. Le temps d’arrêt sur votre système de production est limité au temps nécessaire au transfert des fichiers statiques et du code compilé vers le serveur.

## Systèmes de déploiement

Nous utilisons les termes suivants pour décrire les systèmes impliqués dans le déploiement.

- **Système de développement**: machine sur laquelle les développeurs travaillent pour personnaliser le code et installer des extensions, des thèmes et des modules de langue de Commerce Marketplace. En outre, vous apportez toutes les modifications de configuration à votre système de développement. Vous pouvez avoir de nombreux systèmes de développement.

- **Système de création**: système sur lequel vous déployez des ressources statiques et compilez du code pour votre système de production. Comme vous créez ces ressources sur un système qui n’est pas en production, le temps d’arrêt de votre système de production est réduit.

  Commerce ne doit pas être installé sur votre système de génération. Il ne nécessite que le code Commerce, mais aucune connexion à la base de données n’est requise. En outre, votre système de génération n’a pas besoin d’être un serveur physiquement distinct.

- **Système d’évaluation**—_Facultatif_. Vous pouvez éventuellement configurer un système d’évaluation à utiliser pour le test final de tout le code intégré, y compris le test d’acceptation utilisateur (UAT). Configurez un système intermédiaire de la même manière que vous configurez un système de production. À l’exception du fait que l’évaluation n’est pas votre boutique en ligne et ne traite pas les commandes des clients, elle est identique à la production.

- **Système de production**— Votre magasin en ligne. Vous devez effectuer ici des modifications de configuration directes minimales, et certainement rien qui n’a pas été testé sur une instance d’évaluation. Si possible, apportez des modifications à la configuration avec [Correctifs de données](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) qui ont été testées sur une instance d’évaluation/de développement.

## Autres méthodes de déploiement

Vous pouvez éventuellement utiliser d’autres méthodes de déploiement, notamment :

- Copie sécurisée avec SCP ou rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- La variable [Outil de déploiement](https://deployer.org/)

## Gestion de la configuration

La modélisation après [facteur 3 dans la conception d’applications à 12 facteurs](https://12factor.net/config), Commerce stocke désormais la configuration de chaque système dans le système lui-même. (Les paramètres de configuration de développement sont stockés sur le système de développement, les paramètres de production sont stockés sur le système de production.)

Nous vous offrons un moyen de synchroniser la configuration de vos systèmes :

- **Configuration partagée**: paramètres qui ne sont ni spécifiques au système, ni sensibles.

  Les paramètres partagés sont des paramètres que vous souhaitez uniformiser sur les systèmes de développement et de production. Définissez la configuration partagée dans l’administrateur de votre développement (ou dans Adobe Commerce sur l’infrastructure cloud). _integration_).

  le fichier de configuration partagé, `app/etc/config.php`, doit être inclus dans le contrôle de code source afin qu’il puisse être partagé entre les systèmes de développement, de génération et de production.

- **Configuration spécifique au système**: paramètres qui varient selon le système, tels que les noms d’hôte et les ports des moteurs de recherche.

- **Configuration sensible**: paramètres qui doivent être _not_ être dans le contrôle de code source, car ils exposent des informations d’identification personnelle (PII) ou des paramètres tels que des clés d’API ou des mots de passe.

  le fichier de configuration spécifique au système, `app/etc/env.php`, devrait _not_ être inclus dans le contrôle de code source ou partagé d’une autre manière entre les systèmes ; Utilisez plutôt la variable [`magento config:set` et `magento:sensitive:set` Commandes](../cli/set-configuration-values.md) pour fournir des valeurs pour ces paramètres dans votre système de production.

>[!INFO]
>
>Ces nouvelles méthodes de gestion de votre configuration sont facultatives. Il n’est pas nécessaire de le faire, mais il est vivement recommandé de l’utiliser.

La plupart du temps, les options de configuration que vous définissez dans la configuration partagée, spécifique au système ou sensible ne peuvent pas être modifiées dans l’administrateur. Cela permet de maintenir la cohérence de vos paramètres sur tous les systèmes. (Vous pouvez éventuellement utiliser la variable [`magento config:set` command](../cli/set-configuration-values.md) sans le `--lock` pour configurer les paramètres modifiables dans l’administrateur.)

Chaque option de configuration Commerce possède une _chemin de configuration_. Pour définir une valeur pour une option de configuration, vous pouvez utiliser une commande d’interface de ligne de commande ou une variable d’environnement pour définir la valeur de ce chemin de configuration sur un système spécifique.
