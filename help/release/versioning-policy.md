---
title: Politique de version
description: Découvrez les différents types de versions d’Adobe Commerce.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: e0905f357c5ab84b30304eeaad00d9ae4ec0c168
workflow-type: tm+mt
source-wordcount: '680'
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
- Minor releases can include fixes for security and quality issues.

## PATCH release

Patch releases are primarily focused on delivering security, performance, compliance, and high-priority quality fixes to help you keep your sites performing at their peak.

The following guidelines apply to patch releases:

- The latest-supported minor release receives full functional quality fixes and enhancements.
- Changes that could break extensions or code compatibility are avoided. For example, code written for version 2.2.0 should still work on version 2.2.7.
- On an exceptional basis, breaking changes or additional patches or hotfixes may be released to address security or compliance issues and high-impact quality issues. On the module level, these changes are mostly PATCH-level; sometimes MINOR-level.

### SECURITY patch release

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## ALPHA patch release

Pre-Beta releases of Adobe Commerce features are made publicly available to all Adobe Commerce customers and Adobe partners. Alpha releases are intended for early feedback and evaluation of features that are still in active development. These releases provide an opportunity for early testing and integration planning ahead of Beta and General Availability releases.

Alpha releases may be incomplete, and are likely to contain defects. They are provided &quot;AS IS&quot; without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify, or otherwise support (via Adobe Support Services or otherwise) Alpha releases. Customers should not rely on the correct functioning or performance of Alpha releases or any accompanying documentation or materials. Use of Alpha releases is entirely at the customer&#39;s own risk.

## BETA patch release

Pre-General Availability releases of Adobe Commerce features are made publicly available to all Adobe Commerce customers and Adobe partners. It allows for extra time before General Availability to review code and affected components.

Beta releases may contain defects and are provided &quot;AS IS&quot; without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify, or otherwise support (via Adobe Support Services or otherwise) Beta releases. Customers should not rely on the correct functioning or performance of Beta releases or any accompanying documentation or materials. Accordingly, any use of the Beta Releases is entirely at a customer&#39;s own risk.

## Correctif

Les correctifs sont des correctifs de sécurité ou de qualité à fort impact, tels que les correctifs de vulnérabilités de type « jour zéro », qui affectent de nombreux commerçants. Adobe publie des correctifs (si nécessaire) pour les versions d’Adobe Commerce prises en charge lorsque des problèmes de sécurité ou de qualité critiques les affectent. Les correctifs sont fournis via l’[outil de correctifs de qualité](../tools/quality-patches-tool/usage.md). These fixes are included in the next planned patch release.

>[!NOTE]
>
>Les correctifs peuvent contenir des modifications non rétrocompatibles.

## Patch individuel

Les correctifs individuels contiennent des correctifs de qualité à faible impact pour un problème spécifique. Ces correctifs sont appliqués aux versions mineures prises en charge d’Adobe Commerce. Adobe publie les correctifs individuels selon les besoins pour Adobe Commerce conformément à la [politique de cycle de vie des logiciels](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf). They are delivered through the [Quality Patches Tool](../tools/quality-patches-tool/usage.md).

>[!NOTE]
>
>Les correctifs individuels ne contiennent pas de modifications non rétrocompatibles.

## Correctif personnalisé

Créé par du personnel non Adobe pour résoudre un problème ou modifier le code Adobe Commerce pour diverses raisons.

<!-- Last updated from includes: 2026-04-20 10:12:04 -->
