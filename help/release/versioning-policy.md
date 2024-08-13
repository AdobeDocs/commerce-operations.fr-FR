---
title: Stratégie de publication
description: Découvrez les différents types de versions d’Adobe Commerce, notamment les versions mineures, les correctifs, les correctifs de sécurité, les fonctionnalités, les correctifs, les correctifs individuels et les correctifs personnalisés.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b5d120893668f4315e289a204649270db4f7a6bc
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Stratégie de mise à jour Adobe Commerce

Adobe Commerce utilise le [contrôle de version sémantique](https://semver.org/) au niveau du module individuel (par exemple `magento/framework 101.1.1`), mais pas pour le numéro de version marketing. Par exemple :

- **MAJOR release**—2
- **MINOR release**—2.4
- **Version du PATCH**—2.4.5
   - **Version de correctif de sécurité**—2.4.5-p1
      - Correctif de bogue de sécurité
      - Amélioration de la sécurité
- **Version de correctif BETA**—2.4.7-beta2
- **Extensibilité, infrastructure et mise à jour des services**
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

## Publication de correctifs Beta

Les versions de disponibilité prégénérales des fonctionnalités d’Adobe Commerce sont mises à la disposition de tous les clients et partenaires d’Adobe d’Adobe Commerce. Il permet de disposer de davantage de temps avant la disponibilité générale pour examiner le code et les composants affectés.

Les versions de Beta peuvent contenir des défauts et sont fournies &quot;EN L’ÉTAT&quot; sans garantie de quelque type que ce soit. Adobe n’aura aucune obligation de gérer, corriger, mettre à jour, modifier, modifier ou d’autre manière prendre en charge les versions de Beta (via les services d’assistance d’Adobe ou autres). Il est conseillé aux clients de faire preuve de prudence et de ne pas s’appuyer d’aucune manière sur le bon fonctionnement ou sur les performances correctes des versions de Beta et/ou de la documentation ou des documents associés. Par conséquent, toute utilisation des versions de Beta est entièrement à la merci du client.

## Fonctionnalités, infrastructure cloud et version de l’extensibilité

L’infrastructure cloud et les mises à jour de fonctionnalités contiennent de nouvelles fonctionnalités et des mises à jour de fonctionnalités fournies sous la forme de services indépendants, distinctes des mises à jour de correctifs. Par exemple, les mises à jour de nos services et infrastructures d’hébergement dans le cloud, les produits B2B, SaaS (service de catalogue, connexion aux données, Recommendations de produit et recherche en direct), ainsi que les technologies d’extensibilité (maillage d’API, kit de démarrage d’intégration et mode Eventing).

## Correctif

Les correctifs sont des correctifs qui contiennent des correctifs de sécurité ou de qualité à fort impact, tels que des correctifs de vulnérabilités de jour zéro, qui affectent de nombreux marchands. Adobe publie des correctifs pour les versions d’Adobe Commerce qui sont toujours prises en charge et affectées par des problèmes critiques de sécurité ou de qualité, si nécessaire. Les correctifs sont publiés dans la [section Problèmes connus](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) de notre base de connaissances. Ces correctifs sont inclus dans la prochaine version de correctif planifiée.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications incompatibles avec le passé.

## Correctif individuel

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs s’appliquent aux versions mineures prises en charge d’Adobe Commerce. Adobe publie des correctifs individuels, selon les besoins, pour Adobe Commerce conformément à notre [Politique de cycle de vie des logiciels](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications incompatibles avec le passé.

## Correctif isolé

Contient un correctif autonome inclus dans le dernier correctif de sécurité uniquement ou un correctif de sécurité uniquement à venir, qui est publié séparément pour une mise en oeuvre plus rapide.

## Correctif personnalisé

Créé par le personnel non-Adobe pour résoudre un problème ou modifier le code Adobe Commerce pour diverses raisons. Les correctifs personnalisés sont fournis par l’[ outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
