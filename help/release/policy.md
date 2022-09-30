---
title: Stratégie de publication
description: Découvrez les différents types de versions d’Adobe Commerce, notamment les versions mineures, les correctifs, les correctifs de sécurité, les fonctionnalités, les correctifs, les correctifs individuels et les correctifs personnalisés.
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Stratégie de mise à jour Adobe Commerce

Utilisation d’Adobe Commerce et de Magento Open Source [contrôle de version sémantique](https://semver.org/) au niveau du module individuel (par exemple `magento/framework 101.1.1`), mais pas pour le numéro de version marketing. Par exemple :

- **Version MAJOR**—2
- **Version mineure**—2.4
- **Version du PATCH**—2.4.1
   - **Version de correctif de sécurité**—2.4.1-p1
      - Correctif de bogue de sécurité
      - Amélioration de la sécurité
- **Mise à jour des fonctionnalités**
- **Correctif**
- **Correctif individuel**
- **Correctif personnalisé**

## Version mineure

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
- Sur une base exceptionnelle, des modifications de rupture ou des correctifs ou correctifs supplémentaires peuvent être publiés pour résoudre les problèmes de sécurité ou de conformité et de qualité à fort impact. Au niveau du module, il s’agit principalement de modifications au niveau du PATCH ; parfois des changements de niveau mineur.

## Version de correctif de sécurité

**Correctif du bogue de sécurité**: Un changement de code logiciel qui résout un problème de sécurité identifié et fournit les résultats attendus dans une zone de produit affectée. Ces correctifs sont généralement rétrocompatibles.

**Amélioration de la sécurité**: Amélioration ou modification de configuration d’un logiciel afin d’améliorer de manière proactive la sécurité au sein de l’application. Ces améliorations de sécurité permettent de résoudre les risques de sécurité qui affectent la position de sécurité de l’application Adobe Commerce, mais qui peuvent être rétrocompatibles.

Avec les mises à jour de correctifs de sécurité, vous pouvez maintenir votre site plus sécurisé sans appliquer d’autres correctifs de qualité et améliorations contenus dans une version trimestrielle complète de correctifs. Les mises à jour des correctifs de sécurité sont ajoutées avec &quot;-pN&quot;, où N est la version incrémentielle des correctifs commençant par 1 (par exemple, 2.3.5-p1). Les mises à jour des correctifs de sécurité peuvent également inclure les correctifs nécessaires pour résoudre les problèmes critiques qui affectent l’application Adobe Commerce.

Chaque version de correctif de sécurité est basée sur la version de correctif complète précédente. Il contient des correctifs de qualité et de sécurité issus d’une version de correctif précédente et des correctifs de sécurité créés entre la version de correctif complète précédente et la version de correctif de sécurité.

Avec l’annonce de notre [nouvelle stratégie de mise à jour et stratégie de cycle de vie mise à jour](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (9/16/2021), nos mises à jour de correctifs de sécurité sont différenciées selon qu’elles s’appliquent à la dernière version mineure prise en charge ou qu’elles font partie d’une ligne de mise à jour mineure précédente encore prise en charge :

- **Versions des correctifs de sécurité pour la dernière version mineure prise en charge**:

   - La version de correctif de sécurité de la dernière version mineure prise en charge (actuellement Adobe Commerce 2.4) comprend :

      - Correctifs de bogues de sécurité créés depuis la version précédente complète du correctif.

      - Ces mises à jour de correctifs de sécurité peuvent également inclure des correctifs nécessaires pour résoudre les problèmes critiques qui peuvent affecter l’application Adobe Commerce.
   - La version de correctif de sécurité de la dernière version mineure prise en charge (actuellement Adobe Commerce 2.4) n’inclut généralement pas d’améliorations de sécurité. Elles sont incluses dans la version complète du correctif pour la dernière version mineure prise en charge.


- **Versions de correctifs de sécurité pour les versions mineures antérieures prises en charge**:

   - La version de correctif de sécurité d’une version mineure précédente qui est toujours prise en charge (actuellement Adobe Commerce 2.3) comprend :

      - Correctifs de bogues de sécurité créés depuis la version précédente du correctif ou du correctif de sécurité, ainsi que de nouvelles améliorations de sécurité.

      - Ces mises à jour de correctifs de sécurité peuvent également inclure les correctifs nécessaires pour résoudre les problèmes critiques qui affectent l’application Adobe Commerce.

      |  | Bogue de sécurité | Amélioration de la sécurité |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Versions de correctifs de sécurité pour la dernière version mineure prise en charge (actuellement 2.4) | X |  |
      | Versions de correctifs de sécurité pour les versions mineures antérieures prises en charge (actuellement 2.3) | X | X |


Pour obtenir des informations générales sur les versions de sécurité, voir [Présentation de la nouvelle version du correctif uniquement pour la sécurité](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Pour plus d’informations sur le téléchargement et l’application de correctifs de sécurité, voir [Installation de démarrage rapide](../installation/composer.md).

## Mise à jour des fonctionnalités

Les mises à jour de fonctionnalités contiennent de nouvelles fonctionnalités et des mises à jour de fonctionnalités qui sont diffusées en tant que services indépendants, indépendamment des mises à jour de correctifs. Par exemple, les services tels que Recommendations de produit et Live Search, les modules indépendants tels que PWA Studio et Inventory management (MSI) et les mises à jour de nos services cloud et de notre infrastructure.

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

- [Planification et budget pour les cycles de mise à niveau de commerce](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Contrôle de version](https://developer.adobe.com/commerce/php/development/versioning/)
- [Versions à venir](schedule.md)
- [Stratégie de cycle de vie logicielle](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
