---
title: Politique de version
description: Découvrez les différents types de versions d’Adobe Commerce, notamment les versions mineures, les correctifs, les correctifs de sécurité, les fonctionnalités, les correctifs logiciels, les correctifs individuels et les correctifs personnalisés.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Politique de mise à jour d’Adobe Commerce

Adobe Commerce utilise le [contrôle de version sémantique](https://semver.org/) au niveau des modules individuels (par exemple, `magento/framework 101.1.1`), mais pas pour le numéro de version marketing. Par exemple :

- **Version majeure**—2
- **version MINEURE**—2.4
- **Version de PATCH**—2.4.5
   - **Mise à jour du correctif de SÉCURITÉ**-2.4.5-p1
      - Correctif de sécurité
      - Amélioration de la sécurité
- **version du correctif BETA**—2.4.7-beta2
- **Version Extensibilité, Infrastructure et Services**
- **Correctif**
- **Patch individuel**
- **Correctif personnalisé**

## VERSION MINEURE

Les instructions suivantes s’appliquent aux versions mineures :

- Des modifications avec rupture sont possibles ; le code écrit pour Adobe Commerce 2.2.x peut ne plus fonctionner avec Adobe Commerce 2.3.x. Par exemple, les versions mineures peuvent introduire la prise en charge des principales exigences et dépendances du système, telles que PHP.
- Les versions des modules peuvent varier. Par exemple, certaines modifications de module sont introduites dans un nouveau correctif alors que d’autres le sont dans une version mineure.
- Les versions mineures peuvent inclure de nouvelles fonctionnalités qui peuvent nécessiter un travail supplémentaire de votre part ou de la part de votre partenaire de solution lors de la mise à niveau pour garantir la compatibilité.
- Les versions mineures peuvent inclure des correctifs pour les problèmes de sécurité et de qualité.

## Version de PATCH

Les versions de correctifs sont principalement axées sur la fourniture de correctifs de sécurité, de performances, de conformité et de qualité haute priorité pour vous aider à maintenir les performances de vos sites à leur meilleur niveau.

Les instructions suivantes s’appliquent aux versions de correctif :

- La dernière version mineure prise en charge reçoit des correctifs et des améliorations de qualité fonctionnelle complets.
- Les modifications susceptibles d’interrompre la compatibilité des extensions ou du code sont évitées. Par exemple, le code écrit pour la version 2.2.0 doit toujours fonctionner sur la version 2.2.7.
- À titre exceptionnel, des modifications importantes ou des correctifs ou correctifs supplémentaires peuvent être publiés pour résoudre des problèmes de sécurité ou de conformité et des problèmes de qualité à fort impact. Au niveau du module, il s’agit principalement de modifications au niveau du PATCH, parfois mineures.

### Mise à jour du correctif de SÉCURITÉ

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Version du correctif Beta

Les mises à jour de disponibilité pré-générale des fonctionnalités d’Adobe Commerce sont mises à la disposition de tous les clients Adobe Commerce et partenaires Adobe. Cela permet de disposer de plus de temps avant la disponibilité générale pour examiner le code et les composants affectés.

Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’aura aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par l’intermédiaire des services d’assistance Adobe ou d’une autre manière) les versions de Beta. Il est conseillé aux clients d’être prudents et de ne pas se fier, de quelque manière que ce soit, au bon fonctionnement ou aux performances des versions de Beta et/ou de la documentation ou du matériel les accompagnant. Par conséquent, toute utilisation des Versions de Beta est entièrement aux risques et périls du Client.

## Version des fonctionnalités, de l’infrastructure cloud et de l’extensibilité

Les infrastructures cloud et les mises à jour de fonctionnalités contiennent de nouvelles fonctionnalités et mises à jour de fonctionnalités fournies en tant que services indépendants, distincts des versions de correctif. Par exemple, les mises à jour de nos services et infrastructures d’hébergement cloud, les produits B2B et SaaS (service de catalogue, connexion de données, recommandations de produits et recherche en direct), ainsi que la technologie d’extensibilité (maillage API, kit de démarrage d’intégration et génération d’événements).

## Correctif

Les correctifs sont des correctifs de sécurité ou de qualité à fort impact, tels que les correctifs de vulnérabilités de type « jour zéro », qui affectent de nombreux commerçants. Adobe publie des correctifs pour les versions d’Adobe Commerce qui sont toujours prises en charge et affectées par des problèmes de sécurité ou de qualité critiques, selon les besoins. Les correctifs sont publiés dans la section [Problèmes connus](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) de notre base de connaissances. Ces correctifs sont inclus dans la prochaine version prévue du correctif.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications non rétrocompatibles.

## Patch individuel

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs sont appliqués aux versions mineures prises en charge d’Adobe Commerce. Adobe publie les correctifs individuels selon les besoins pour Adobe Commerce conformément à notre [politique de cycle de vie des logiciels](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications non rétrocompatibles.

## Patch isolé

Contient un correctif autonome inclus dans le dernier correctif de sécurité uniquement ou un correctif de sécurité uniquement à venir, qui est publié séparément pour une implémentation plus rapide.

## Correctif personnalisé

Créé par du personnel non Adobe pour résoudre un problème ou modifier le code Adobe Commerce pour diverses raisons. Les correctifs personnalisés sont fournis via l’outil [Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
