---
title: Stratégie de publication
description: Découvrez les différents types de versions d’Adobe Commerce, notamment les versions mineures, les correctifs, les correctifs de sécurité, les fonctionnalités, les correctifs, les correctifs individuels et les correctifs personnalisés.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Stratégie de mise à jour Adobe Commerce

Adobe Commerce utilise [contrôle de version sémantique](https://semver.org/) au niveau du module individuel (par exemple `magento/framework 101.1.1`), mais pas pour le numéro de version marketing. Par exemple :

- **Version MAJOR**—2
- **Version MINEURE**—2.4
- **Version du PATCH**—2.4.5
   - **Version de correctif de sécurité**—2.4.5-p1
      - Correctif de bogue de sécurité
      - Amélioration de la sécurité
- **Version de correctif BÊTA**—2.4.7-beta2
- **Extension, infrastructure et version des services**
- **Correctif**
- **Correctif individuel**
- **Correctif personnalisé**

## Version MINEURE

Les directives suivantes s’appliquent aux versions mineures :

- Des modifications de rupture sont possibles ; le code écrit pour Adobe Commerce 2.2.x peut ne plus fonctionner avec Adobe Commerce 2.3.x. Par exemple, des versions mineures peuvent introduire la prise en charge des principales exigences et dépendances du système, telles que PHP.
- Les versions des modules peuvent varier. Par exemple, certaines modifications de module sont introduites dans un nouveau correctif, tandis que d’autres le sont dans une version mineure.
- Les mises à jour mineures peuvent inclure de nouvelles fonctionnalités qui peuvent nécessiter un travail supplémentaire de votre part ou de votre partenaire de solution au cours de la mise à niveau pour garantir la compatibilité.
- Les versions mineures peuvent inclure des correctifs pour les problèmes de sécurité et de qualité.

## Version du PATCH

Les versions de correctifs visent principalement à offrir des correctifs de sécurité, de performances, de conformité et de qualité prioritaires afin de vous aider à maintenir les performances de vos sites à leur maximum.

Les directives suivantes s’appliquent aux versions de correctif :

- La dernière version mineure prise en charge contient des correctifs de qualité fonctionnelle complets et des améliorations.
- Les modifications susceptibles de rompre les extensions ou la compatibilité du code sont évitées. Par exemple, le code écrit pour la version 2.2.0 doit toujours fonctionner sur la version 2.2.7.
- Sur une base exceptionnelle, des modifications de rupture ou des correctifs ou correctifs supplémentaires peuvent être publiés pour résoudre les problèmes de sécurité ou de conformité et de qualité à fort impact. Au niveau du module, il s’agit principalement de modifications au niveau du PATCH ; parfois de modifications de niveau mineur.

### Version de correctif de sécurité

{{$include /help/_includes/security-patch-release-overview.md}}

## Version de correctif BÊTA

Les versions de disponibilité prégénérales des fonctionnalités d’Adobe Commerce sont mises à la disposition de tous les clients et partenaires d’Adobe d’Adobe Commerce. Il permet de disposer de davantage de temps avant la disponibilité générale pour examiner le code et les composants affectés.

Les versions bêta peuvent contenir des défauts et sont fournies &quot;EN L’ÉTAT&quot; sans aucune garantie de quelque type que ce soit. Adobe n’aura aucune obligation de gérer, corriger, mettre à jour, modifier, modifier ou d’autre manière prendre en charge (via les services d’assistance d’Adobe ou d’une autre manière) les versions bêta. Il est conseillé aux clients de faire preuve de prudence et de ne pas s’appuyer d’aucune manière sur le bon fonctionnement ou les performances des versions bêta et/ou de la documentation ou des documents associés. Par conséquent, toute utilisation des versions bêta est entièrement à la charge du client.

## Extension, infrastructure et version des services

Description des nouvelles fonctionnalités qui contiennent de nouvelles fonctionnalités et des mises à jour de fonctionnalités diffusées en tant que services indépendants, indépendamment des mises à jour de correctifs. Parmi les exemples, citons les technologies d’extensibilité telles que le Mesh et l’Eventing de l’API, les produits SaaS tels que Recommendations de produit et Live Search, les modules indépendants tels que B2B et PWA Studio, ainsi que les mises à jour de nos services d’hébergement de cloud et de notre infrastructure.

## Correctif

Les correctifs sont des correctifs qui contiennent des correctifs de sécurité ou de qualité à fort impact, tels que des correctifs de vulnérabilités de jour zéro, qui affectent de nombreux marchands. Adobe publie des correctifs pour les versions d’Adobe Commerce qui sont toujours prises en charge et affectées par des problèmes critiques de sécurité ou de qualité, si nécessaire. Les correctifs sont publiés dans la [Section Problèmes connus](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) de notre base de connaissances. Ces correctifs sont inclus dans la prochaine version de correctif planifiée.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications rétrocompatibles.

## Correctif individuel

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs s’appliquent aux versions mineures prises en charge d’Adobe Commerce. Adobe publie les correctifs individuels nécessaires pour Adobe Commerce conformément à nos [Stratégie de cycle de vie logicielle](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications rétrocompatibles.

## Correctif personnalisé

Créé par le personnel non-Adobe pour résoudre un problème ou modifier le code Adobe Commerce pour diverses raisons. Les correctifs personnalisés sont fournis par l’intermédiaire de la fonction [Outil Correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Rubriques connexes

- [Contrôle de version](https://developer.adobe.com/commerce/php/development/versioning/)
- [Versions à venir](schedule.md)
- [Stratégie de cycle de vie logicielle](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
