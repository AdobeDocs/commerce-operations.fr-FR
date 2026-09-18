---
title: Politique de correctifs de sécurité isolés mensuels
description: Découvrez les correctifs de sécurité isolés mensuels d’Adobe Commerce, publiés le mardi des correctifs, pour fournir des correctifs CVE ciblés entre les versions des correctifs de sécurité.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
    internal-label: PCI
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 66d7c9fd19785e791635d8e8bdf3d6ff3aa27a20
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%
---
# Politique de correctifs de sécurité isolés mensuels

Pour aider les clients Adobe Commerce à appliquer plus rapidement des correctifs de sécurité critiques, Adobe Commerce fournit désormais des correctifs de sécurité isolés mensuels le mardi des correctifs (le deuxième mardi du mois). Consultez le [calendrier de publication d’](schedule.md) pour connaître les dates. Ces correctifs sont disponibles pour les installations Adobe Commerce on Cloud, Adobe Commerce on-premise et Magento Open Source.

Un fichier de correctif de sécurité isolé contient uniquement le code nécessaire pour résoudre une ou plusieurs vulnérabilités de sécurité spécifiques. Il est fourni sous la forme d’un fichier code-diff à portée étroite plutôt que d’un package Composer complet. Étant donné que les modifications sont spécifiques aux vulnérabilités de sécurité, elles peuvent être examinées, testées et appliquées plus rapidement qu’une version de correctif de sécurité, sans déclencher la résolution de dépendance et le test de régression plus larges requis par une mise à niveau de la version du correctif de sécurité. Chaque mois, un fichier de correctif de sécurité isolé est intégré à la prochaine version complète du correctif de sécurité. Ainsi, les clients peuvent obtenir tous les fichiers de correctif isolé publiés dans la prochaine version du correctif de sécurité (`-pN`).

## Adaptation des patchs isolés aux autres types de patchs

Les correctifs de sécurité isolés font partie de plusieurs types de correctifs fournis par Adobe Commerce pour assurer la sécurité et la mise à jour des clients.

| **Type de correctif** | **Objectif** | **Comportement cumulé** | **Diffusion type** | **Rôle** |
| --- | --- | --- | --- | --- |
| Version du correctif de sécurité (-pN) | Mise à jour de sécurité et de conformité pour une ligne de version prise en charge | Cumulatif : établit la base de sécurité actuelle | Package du compositeur | Base de sécurité prise en charge par le Principal |
| Fichier de correctif de sécurité isolé | Correctif ciblé pour un ou plusieurs CVE | Non cumulatif : appliquer en séquence | Fichier de correctif autonome, généralement un fichier ZIP. Certains correctifs peuvent également être inclus dans les correctifs cloud pour Commerce | Correction intermédiaire plus rapide entre les versions des correctifs de sécurité |
| Correctifs cloud pour Commerce | Correctifs critiques requis (y compris les correctifs de sécurité) et modifications spécifiques au cloud | Dépendant de la version du package | Correctifs cloud pour le package Commerce géré via ECE-Tools | Appliqué automatiquement lors du déploiement dans le cloud |
| Correctif de l’outil de correctifs de la qualité (QPT) | Correctif de qualité ou de compatibilité ciblé facultatif pour un problème spécifique | Dépendant de la chaîne de correctifs | Package QPT | Fournit des correctifs de qualité ciblés |
| Correctif | Correctif urgent et de portée étroite (par exemple, un jour zéro) | Spécifique à un cas | Package ZIP/diff ou autonome via QPT | Questions urgentes à fort impact |

Les deux types de correctifs de sécurité jouent des rôles différents :

* **Les correctifs isolés** contiennent uniquement des correctifs de vulnérabilité et ne sont pas cumulatifs. Ils ne regroupent pas les fichiers de correctif isolés publiés précédemment. Les commerçants doivent appliquer les correctifs dans l&#39;ordre, car chaque nouveau correctif suppose que les correctifs précédents sont en place. Pour appliquer un correctif de sécurité isolé, l’installation doit se trouver sur la dernière version du correctif de sécurité uniquement pour sa ligne prise en charge, car les correctifs isolés sont testés exclusivement par rapport à cette version.

* **Les correctifs de sécurité (`-pN`)** sont publiés chaque année pour toutes les lignes de version prises en charge et déployés via le compositeur. Ils comprennent tous les correctifs de sécurité, de conformité et de qualité publiés précédemment. Adobe peut publier des correctifs de sécurité supplémentaires si nécessaire.

## Avantages mensuels des correctifs isolés

La découverte de vulnérabilités s’est accélérée dans l’ensemble du secteur. Les outils d&#39;analyse assistés par l&#39;IA peuvent désormais analyser les grandes bases de code et les défauts de surface beaucoup plus rapidement que la révision manuelle, réduisant ainsi le délai entre la divulgation et l&#39;exploitation. Une cadence mensuelle de correctifs isolés permet de combler cet écart en fournissant des correctifs dès qu’ils sont prêts au lieu d’attendre la prochaine version de correctifs de sécurité prévue.

L’objectif est d’atteindre une vitesse maximale sans surcoût inutile. Un correctif prêt à l’emploi ne reste pas en file d’attente jusqu’à la prochaine version du correctif de sécurité, et les commerçants ne corrigent pas plus souvent que nécessaire. Les fichiers de correctifs de sécurité isolés résolvent cette tension : chacun est une comparaison étroite et axée uniquement sur la sécurité, beaucoup plus simple à examiner et à appliquer qu’une version de correctif de sécurité, car sa portée est délibérément limitée.

Cette approche fonctionne car les correctifs à usage unique ignorent les tests de résolution des dépendances et de régression complète requis pour les versions du compositeur, ce qui permet de les créer, de les valider par rapport à une base connue et de les envoyer rapidement. Sur les infrastructures cloud, ces correctifs sont regroupés dans Correctifs cloud pour Commerce, une mise à jour des commerçants de packages dans le cadre de leur compositeur et de leur workflow de déploiement. Une fois mis à jour, le correctif s’applique automatiquement pendant le déploiement sans fichier de correctif distinct à localiser ou à appliquer. Le workflow manuel de fichiers de correctifs décrit dans les bulletins de sécurité est destiné aux installations sur site et Magento Open Source qui n’exécutent pas le pipeline Cloud.

## Application de correctifs isolés mensuels

Pour appliquer le fichier de correctif de sécurité isolé mensuel et rester à jour sur les derniers correctifs, procédez comme suit :

1. **Vérifiez le [calendrier des versions](schedule.md).**

   Les nouveaux fichiers de correctifs isolés mensuels sont expédiés conformément au calendrier de publication. Consultez le bulletin de sécurité correspondant pour les composants et les fichiers CVE concernés. Chaque bulletin contient des liens vers les notes de mise à jour avec des instructions détaillées pour installer le fichier de correctif isolé de ce mois-là.

1. **Vérifiez le statut de sécurité de votre installation Commerce à l’aide de l’outil [Version de Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro).**

   L’outil signale les correctifs mensuels actuellement installés, ceux qui sont manquants et les fichiers CVE auxquels l’installation reste exposée. Cela permet d’évaluer de manière définitive l’action requise, plutôt que de se fier uniquement au numéro de version.

1. **Confirmer votre version de référence.**

   Les correctifs isolés sont testés uniquement par rapport à la dernière version de `-p` de sécurité uniquement pour votre ligne. Si vous êtes en retard sur cette ligne de base, appliquez-la d&#39;abord.

1. **Appliquez tous les correctifs manquants dans l’ordre.**

   Comme ils ne sont pas cumulatifs, vous ne pouvez pas passer au fichier le plus récent.

   >[!NOTE]
   >
   >**Clients Cloud :** d’abord vérifier les correctifs cloud installés pour Commerce [version](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). Le correctif peut déjà être inclus et son application manuelle peut créer un conflit ou dupliquer le correctif.

1. **Faire correspondre les fichiers aux composants installés.**

   Appliquez uniquement le fichier correspondant à votre version CE, EE, B2B ou d’un autre composant.

1. **Réexécutez l’outil de version de Commerce pour confirmer.**

   Vérifiez que le nouveau correctif s’affiche comme installé et que les fichiers CVE correspondants sont désormais déclarés comme protégés.

1. **Test, puis déploiement.**

   Validez dans l’évaluation avant de passer en production, conformément à votre processus de modification normal.

Les clients Cloud peuvent également utiliser l’[automatisation des correctifs ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/caps-tool/intro) pour appliquer ou annuler des correctifs par le biais du panneau d’administration au lieu des étapes manuelles Git et Compositeur ci-dessus.

## Actions Patch par type de déploiement

| **Vous exécutez...** | **Qu’est-ce qui change pour vous** |
| --- | --- |
| Adobe Commerce on Cloud | Les correctifs cloud pour Commerce, fournis par le biais d&#39;ECE-Tools, appliquent automatiquement les correctifs requis lors de votre prochain déploiement. Vous contrôlez toujours les étapes de branche, de fusion et de validation, et devez vérifier les notes de mise à jour des correctifs cloud pour Commerce avant d’appliquer manuellement le même correctif. |
| Adobe Commerce On-Premise | Confirmez votre version de `-p` de base, téléchargez le fichier correspondant à chaque composant installé, appliquez-le dans l’ordre et vérifiez avec l’outil de version Commerce. |

## FAQ

Le correctif de sécurité isolé mensuel est une nouvelle politique de version. Les questions suivantes portent sur des préoccupations courantes.

### Dois-je appliquer chaque correctif isolé précédent ou simplement la dernière version du correctif de sécurité ?

Vous avez besoin des deux. Avant d’appliquer un correctif isolé, effectuez une mise à jour vers la dernière version de base de la version `-p` pour la sécurité uniquement. Chaque dispositif transdermique est testé uniquement par rapport à cette ligne de base. Les patchs isolés ne sont pas cumulatifs, appliquez donc les patchs manqués l’un après l’autre.

Par exemple, si vous êtes sur la base de la version actuelle de `-p` mais que vous avez oublié les correctifs isolés de juillet et août, appliquez juillet, puis août, puis septembre. La prochaine version complète de `-p` réinitialise la séquence, car elle inclut tous les correctifs isolés émis précédemment.

### Pourquoi ne pas simplement livrer un package de compositeur au lieu de fichiers de correctifs distincts ?

Dans une installation comportant plusieurs composants (CE, EE, B2B et Page Builder), une version mensuelle peut nécessiter des fichiers correctifs distincts, car chaque fichier cible une version de composant installée spécifique. La combinaison de tous les correctifs dans un seul package Composer réintroduirait les problèmes de résolution des dépendances et nécessiterait des tests de régression de toute la surface, les risques que les correctifs isolés sont conçus pour éviter. Les clients Cloud n’ont pas besoin d’appliquer de correctifs manuellement. Les correctifs cloud pour Commerce fournissent les mêmes correctifs par le biais du pipeline de déploiement existant.

### Avec des correctifs superposés, comment savoir dans quel état de sécurité se trouve mon installation ?

Avec la publication mensuelle des correctifs de sécurité, Adobe Commerce a introduit l’[outil de version de Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro), un utilitaire autonome qui signale les correctifs installés ou manquants et les fichiers CVE contre lesquels votre installation est protégée. Plutôt que de compter sur des numéros de version, l’outil lit les métadonnées des correctifs et fournit une sortie lisible par ordinateur pour la création de rapports et l’intégration continue (CI).

### Cela signifie-t-il qu’Adobe a abandonné les versions de sécurité cumulatives ?

Non. La version `-p` annuelle reste le principal point de contrôle de sécurité cumulatif. Les patchs isolés complètent cette cadence pour les EVC qui ne peuvent pas l’attendre en toute sécurité. Elles ne remplacent pas les versions `-p`. Si vous appliquez chaque année la mise à jour de correctif de sécurité prévue pour votre ligne, vous restez sur un chemin d’accès entièrement pris en charge et recevez chaque correctif qui a été émis sous la forme d’un fichier isolé entre les deux.

### L’envoi de correctifs en dehors du compositeur ne rend-il pas une installation par défaut moins sécurisée ?

Non. Le mécanisme de diffusion n’affecte pas les résultats de sécurité du correctif. Un correctif isolé applique la même modification de code que celle incluse ultérieurement dans une version complète de correctif (`-p`). Que le correctif soit fourni sous la forme d’un package de compositeur ou d’un fichier autonome n’a aucune incidence sur son efficacité. Les commerçants qui n’appliquent pas le correctif conservent leur base de sécurité existante jusqu’à la prochaine version de sécurité prévue. L&#39;application de correctifs isolés peut réduire l&#39;exposition en fournissant des correctifs plus tôt, plutôt que d&#39;attendre un cycle de publication complet.

## Plus d’aide sur cette rubrique

>[!MORELIKETHIS]
>
>* [Politique relative au cycle de vie des logiciels](lifecycle-policy.md)
>* [Politique de version](versioning-policy.md)
>* [Calendrier de publication des correctifs](schedule.md)
>* [Outil de version ](../tools/commerce-version-tool/intro.md)
>* [Bulletins et conseils de sécurité ](https://helpx.adobe.com/security/security-bulletin.html)
