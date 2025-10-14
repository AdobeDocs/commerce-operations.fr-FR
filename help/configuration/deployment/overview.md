---
title: Présentation du déploiement
description: Découvrez les stratégies de déploiement de l’application Commerce.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Présentation du déploiement

Ces rubriques décrivent le processus de déploiement de l’application Commerce sur un site de production pour Adobe Commerce version 2.2 et ultérieures. Adobe recommande cette méthode de déploiement aux personnes disposant d’un site volumineux qui ne souhaitent pas subir de temps d’arrêt pendant le déploiement.

Si vous déployez Commerce sur un seul ordinateur et que vous pouvez tolérer certains temps d’arrêt pendant le déploiement, consultez [Déploiement sur un seul ordinateur](../deployment/single-machine.md).

## Déploiement du pipeline

Avec Commerce version 2.2, Adobe a introduit le _déploiement de pipeline_ comme une nouvelle façon de déployer en production avec un temps d’arrêt minimal. Ce processus de déploiement se produit sur différents systèmes et permet de maintenir des configurations cohérentes pour tous les systèmes de déploiement de pipeline. Il s’agit d’un modèle simple mais puissant qui vous permet de séparer les paramètres de configuration ordinaires des paramètres spécifiques au système (comme l’hôte et le port) ou des paramètres sensibles (comme les noms et les mots de passe).

Pour utiliser le déploiement de pipeline, Adobe suppose que vous êtes :

- Un intégrateur système expérimenté avec une excellente connaissance des options de configuration Adobe Commerce.
- Gestion d’un site Commerce volumineux (des milliers d’unités de gestion des stocks (SKU)) et volonté de réduire au minimum les temps d’arrêt du site de production.
- Connaissant la programmation PHP.
- Expérimenté avec les méthodes de commande source.
- Votre code se trouve dans un référentiel de contrôle de code source. Dans ce guide, nous supposons que vous utilisez un référentiel Git.

### Temps d’arrêt réduit

Lorsque vous déployez des ressources statiques et compilez du code sur une machine distincte de votre système de production, vous réduisez les temps d’arrêt. Le temps d’arrêt sur votre système de production est limité à la durée nécessaire au transfert des fichiers statiques et du code compilé vers le serveur.

## Systèmes de déploiement

Nous utilisons les termes suivants pour décrire les systèmes impliqués dans le déploiement.

- **Système de développement** : machine sur laquelle les développeurs travaillent pour personnaliser le code et installer des extensions, des thèmes et des packages de langue à partir de Commerce Marketplace. En outre, vous apportez toutes les modifications de configuration à votre système de développement. Vous pouvez avoir de nombreux systèmes de développement.

- **Système de build** : système sur lequel vous déployez des ressources statiques et compilez le code pour votre système de production. Étant donné que vous créez ces ressources sur un système qui n’est pas en production, le temps d’arrêt de votre système de production est réduit au minimum.

  Il n’est pas nécessaire que Commerce soit installé sur votre système de génération. Il ne nécessite que le code Commerce, mais aucune connexion à la base de données n’est requise. En outre, votre système de génération n’a pas besoin d’être un serveur physiquement distinct.

- **Système d&#39;évaluation**—_facultatif_. Vous pouvez éventuellement configurer un système d’évaluation à utiliser pour les tests finaux de tout le code intégré, y compris les tests d’acceptation utilisateur (UAT). Configurez un système d’évaluation de la même manière que vous configurez un système de production. À l’exception du fait que l’évaluation n’est pas votre boutique en ligne et ne traite pas les commandes des clients, elle est identique à la production.

- **Système de production**—Votre boutique en ligne. Vous devez apporter ici un minimum de modifications directes à la configuration, et certainement rien qui n’ait été testé sur une instance d’évaluation. Si possible, apportez des modifications à la configuration avec les [correctifs de données](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) qui ont été testés sur une instance d’évaluation/de développement.

## Autres méthodes de déploiement

Vous pouvez éventuellement utiliser d’autres méthodes de déploiement, notamment :

- Copie sécurisée avec SCP ou rsync
- [&#x200B; Capistrano &#x200B;](https://capistranorb.com/documentation/overview/what-is-capistrano)
- L’outil [Deployer](https://deployer.org/)

## Gestion de la configuration

Modélisation selon le [facteur 3 dans la conception d’application à 12 facteurs](https://12factor.net/config), Commerce stocke désormais la configuration de chaque système dans le système lui-même. (Les paramètres de configuration de développement sont stockés sur le système de développement, les paramètres de production sont stockés sur le système de production.)

Nous proposons un moyen de synchroniser la configuration de vos systèmes :

- **Configuration partagée**—Paramètres qui ne sont ni spécifiques au système ni sensibles.

  Les paramètres partagés sont des paramètres que vous souhaitez uniformiser sur les systèmes de développement et de production. Définissez la configuration partagée dans Admin sur votre système de développement (ou Adobe Commerce sur l’infrastructure cloud _intégration_).

  Le fichier de configuration partagé, `app/etc/config.php`, doit être inclus dans le contrôle de code source afin qu’il puisse être partagé entre les systèmes de développement, de génération et de production.

- **Configuration spécifique au système** : paramètres qui varient selon le système, tels que les noms d’hôte et les ports du moteur de recherche.

- **Configuration sensible** : paramètres qui ne doivent _pas_ être dans le contrôle de code source, car ils exposent des informations d’identification personnelle (PII) ou des paramètres tels que des clés API ou des mots de passe.

  Le fichier de configuration spécifique au système, `app/etc/env.php`, ne doit _pas_ être inclus dans le contrôle de code source ou autrement partagé entre les systèmes. Utilisez plutôt les commandes [`magento config:set` et `magento:sensitive:set` pour fournir des valeurs pour ces paramètres dans votre système d’exploitation](../cli/set-configuration-values.md)

>[!INFO]
>
>Ces nouvelles méthodes de gestion de la configuration sont facultatives. Pas besoin, mais il est fortement recommandé de les utiliser.

La plupart du temps, les options de configuration que vous définissez dans la configuration partagée, spécifique au système ou sensible ne peuvent pas être modifiées dans l’administration. Cela permet de garantir la cohérence de vos paramètres sur tous les systèmes. (Vous pouvez éventuellement utiliser la commande [`magento config:set`](../cli/set-configuration-values.md) sans l’option `--lock` pour configurer les paramètres modifiables dans l’Administration.)

Chaque option de configuration Commerce comporte un _chemin de configuration_ unique. Pour définir une valeur pour une option de configuration, vous pouvez utiliser une commande d’interface de ligne de commande ou une variable d’environnement pour définir la valeur de ce chemin de configuration sur un système spécifique.
