---
title: Politique de version
description: Découvrez les différents types de versions d’Adobe Commerce.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Politique de mise à jour d’Adobe Commerce

Adobe Commerce utilise le [contrôle de version sémantique](https://semver.org/) au niveau des modules individuels (par exemple, `magento/framework 101.1.1`), mais pas pour le numéro de version marketing. Par exemple :

- **Version majeure**—2
- **version MINEURE**—2.4
- **Version de PATCH**—2.4.8
   - **Mise à jour du correctif de SÉCURITÉ**-2.4.8-p1
      - Correctif de sécurité
      - Amélioration de la sécurité
- **version du correctif ALPHA**-2.4.8-alpha1
- **version du correctif BETA**—2.4.8-beta1
- **Version Extensibilité, Infrastructure et Services**
- **Correctif**
- **Patch individuel**
- **Correctif personnalisé**

## VERSION MINEURE

Les instructions suivantes s’appliquent aux versions mineures :

- Des modifications avec rupture sont possibles ; le code écrit pour Adobe Commerce 2.2.x peut ne plus fonctionner avec Adobe Commerce 2.3.x. Par exemple, les versions mineures peuvent introduire la prise en charge des principales exigences et dépendances du système, telles que PHP.
- Les versions des modules peuvent varier. Par exemple, certaines modifications de module sont introduites dans un nouveau correctif alors que d’autres le sont dans une version mineure.
- Les versions mineures peuvent inclure de nouvelles fonctionnalités qui peuvent nécessiter un travail supplémentaire de votre part ou de la part de votre partenaire de solution lors d’une mise à niveau pour garantir la compatibilité.
- Les versions mineures peuvent inclure des correctifs pour les problèmes de sécurité et de qualité.

## Version de PATCH

Les versions de correctifs sont principalement axées sur la fourniture de correctifs de sécurité, de performances, de conformité et de qualité haute priorité pour vous aider à maintenir les performances de vos sites à leur meilleur niveau.

Les instructions suivantes s’appliquent aux versions de correctif :

- La dernière version mineure prise en charge reçoit des correctifs et des améliorations de qualité fonctionnelle complets.
- Les modifications susceptibles d’interrompre la compatibilité des extensions ou du code sont évitées. Par exemple, le code écrit pour la version 2.2.0 doit toujours fonctionner sur la version 2.2.7.
- À titre exceptionnel, des modifications importantes ou des correctifs ou correctifs supplémentaires peuvent être publiés pour résoudre des problèmes de sécurité ou de conformité et des problèmes de qualité à fort impact. Au niveau du module, ces modifications sont principalement au niveau du PATCH ; parfois au niveau MINEUR.

### Mise à jour du correctif de SÉCURITÉ

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## Version du correctif ALPHA

Les versions pré-Beta des fonctionnalités d’Adobe Commerce sont mises à la disposition de l’ensemble de la clientèle Adobe Commerce et des partenaires Adobe. Les versions d’Alpha sont destinées aux commentaires et à l’évaluation précoces des fonctionnalités qui sont toujours en cours de développement. Ces versions offrent la possibilité d’effectuer des tests précoces et de planifier l’intégration en amont des versions Beta et de disponibilité générale.

Les versions d’Alpha peuvent être incomplètes et sont susceptibles de contenir des défauts. Ils sont fournis « EN L&#39;ÉTAT » sans garantie d&#39;aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge d’une autre manière (via les services d’assistance Adobe ou autre) les versions d’Alpha. Les clients ne doivent pas s’appuyer sur le bon fonctionnement ou les performances des versions d’Alpha ou de toute documentation ou documentation d’accompagnement. L’utilisation des versions d’Alpha s’effectue entièrement aux risques et périls du client.

## Version du correctif Beta

Les versions de disponibilité pré-générale des fonctionnalités d’Adobe Commerce sont mises à la disposition de l’ensemble de la clientèle Adobe Commerce et des partenaires Adobe. Cela permet de disposer de plus de temps avant la disponibilité générale pour examiner le code et les composants affectés.

Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge d’une autre manière (via les services d’assistance Adobe ou autre) les versions de Beta. Les clients ne doivent pas se fier au bon fonctionnement ou aux performances des versions de Beta ou de toute documentation ou documentation d’accompagnement. Par conséquent, toute utilisation des Versions de Beta est entièrement aux risques et périls du client.

## Version des fonctionnalités, de l’infrastructure cloud et de l’extensibilité

Les infrastructures cloud et les mises à jour de fonctionnalités contiennent de nouvelles fonctionnalités et mises à jour de fonctionnalités fournies en tant que services indépendants, distincts des versions de correctif. Voici quelques exemples :

- Mises à jour des services et de l’infrastructure d’hébergement dans le cloud
- B2B
- Produits SaaS (service de catalogue, connexion de données, recommandations de produits et recherche en direct)
- Technologie d’extensibilité (SDK de l’interface utilisateur d’administration, maillage API, kits de démarrage App Builder, événements et Webhooks)

## Correctif

Les correctifs sont des correctifs de sécurité ou de qualité à fort impact, tels que les correctifs de vulnérabilités de type « jour zéro », qui affectent de nombreux commerçants. Adobe publie des correctifs (si nécessaire) pour les versions d’Adobe Commerce prises en charge lorsque des problèmes de sécurité ou de qualité critiques les affectent. Les correctifs sont publiés dans la section [Problèmes connus](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) de la base de connaissances. Ces correctifs sont inclus dans la prochaine version prévue du correctif.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications non rétrocompatibles.

## Patch individuel

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs sont appliqués aux versions mineures prises en charge d’Adobe Commerce. Adobe publie les correctifs individuels selon les besoins pour Adobe Commerce conformément à la [politique de cycle de vie des logiciels](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications non rétrocompatibles.

## Patch isolé

Les correctifs isolés sont des correctifs de sécurité publiés indépendamment d&#39;un correctif de sécurité complet pour permettre une implémentation plus rapide. Chaque correctif isolé résout un problème de sécurité spécifique et est inclus dans le dernier correctif de sécurité complet ou un correctif à venir. Vous trouverez des informations détaillées sur le problème dans le bulletin de sécurité correspondant, qui contient des liens vers un article de la base de connaissances (Base de connaissances) contenant les détails du correctif, la manière d’appliquer le correctif et des informations supplémentaires.

Consultez le [Centre de sécurité](https://helpx.adobe.com/security/products/magento.html) pour connaître les dernières mises à jour de sécurité disponibles pour Adobe Commerce.

## Correctif personnalisé

Créé par du personnel non Adobe pour résoudre un problème ou modifier le code Adobe Commerce pour diverses raisons. Les correctifs personnalisés sont fournis via l’outil [Quality Patches Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).

<!-- Last updated from includes: 2025-05-28 16:37:31 -->
