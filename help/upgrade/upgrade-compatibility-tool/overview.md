---
title: Présentation de la variable [!DNL Upgrade Compatibility Tool]
description: En savoir plus sur les [!DNL Upgrade Compatibility Tool] et comment cela peut vous aider dans votre projet Adobe Commerce.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---


# Présentation de la variable [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Le [!DNL Upgrade Compatibility Tool] est un outil de ligne de commande qui vérifie une instance personnalisée d’Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce. Il identifie également les problèmes potentiels qui doivent être résolus dans votre code avant de tenter une mise à niveau vers une version plus récente d’Adobe Commerce.

Le [!DNL Upgrade Compatibility Tool] vous permet d’identifier le moment où des modifications de code principal ont été apportées à des fonctionnalités personnalisées. Voir [Exécution de l’outil](../upgrade-compatibility-tool/run.md) pour plus d’informations.

Il est distribué sous la forme d’un module Compositeur avec chaque version d’Adobe Commerce. Voir [Développeur](../upgrade-compatibility-tool/developer.md) pour plus d’informations.

Reportez-vous à la section [Installer](../upgrade-compatibility-tool/install.md) pour les premières étapes avec la méthode [!DNL Upgrade Compatibility Tool].

## Workflow

Le diagramme suivant montre le workflow attendu lors de l’exécution de la variable [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramme](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Le [!DNL Upgrade Compatibility Tool] cas pratique

Le cas d’utilisation suivant décrit le processus type de mise à niveau de l’instance d’un client par un partenaire Adobe Commerce :

1. Téléchargez la [!DNL Upgrade Compatibility Tool] du module [Référentiel Adobe Commerce](https://repo.magento.com/). Voir [Téléchargez la [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) pour plus d’informations.
1. Exécutez le [!DNL Upgrade Compatibility Tool] pendant la [bêta](https://devdocs.magento.com/release/beta-program.html) phase la plus récente [Version d’Adobe Commerce](https://devdocs.magento.com/release/).
1. La commande principale est `upgrade:check`. Cette commande analyse votre instance et recherche les erreurs, les avertissements et les problèmes critiques dans l’instance. Pour optimiser les résultats :

   - Option Ajouter `--ignore-current-version-compatibility-issues` pour ignorer tous les problèmes critiques connus, les erreurs et les avertissements par rapport à votre version actuelle d’Adobe Commerce. Affiche uniquement les résultats de la version souhaitée.
   - Option d’utilisation `--min-issue-level` pour définir le niveau de problème minimal. Aide à ne classer par priorité que les problèmes les plus importants liés à la mise à niveau. Si vous souhaitez analyser uniquement un certain fournisseur, module ou même répertoire, vous pouvez également spécifier le chemin d’accès. Voir [Exécution de l’outil](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) pour plus d’informations.

1. Générez une instance Vanilla pour la version spécifique d’Adobe Commerce actuellement installée. Voir [Guide du contributeur](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) pour plus d’informations sur l’utilisation de la variable `instance` pour générer une installation Vanilla.

   >[!NOTE]
   >
   >Une instance Vanilla est une installation propre d’une balise ou d’une branche de version spécifiée pour une version spécifique.

1. Le [!DNL Upgrade Compatibility Tool] Identifie les zones rompues personnalisées. L’ingénieur logiciel peut comprendre la complexité et estimer l’effort de mise à niveau. Ces informations sont partagées avec les parties prenantes.
1. Un budget et une chronologie seront définis pour l&#39;upgrade.
1. Les ingénieurs logiciels peuvent alors travailler sur les modifications de code requises pour corriger les modules endommagés.
1. Le [!DNL Upgrade Compatibility Tool] peut être exécuté pour suivre la progression de la mise à niveau.
1. Les contrôles et l’ingénierie peuvent désormais pousser le code vers un environnement d’évaluation où les tests de régression confirment que tous les tests sont en vert, ce qui leur permet de publier la dernière version d’Adobe Commerce en production le jour même où la version préliminaire d’Adobe Commerce est publiée.

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

## Améliorez les [!DNL Upgrade Compatibility Tool]

Pour vous connecter au [!DNL Upgrade Compatibility Tool] équipe, contactez-nous sur le canal Slack d’ingénierie [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). Nous voulons entendre vos commentaires, vos problèmes et vos suggestions pour nous aider à améliorer l’outil.

Le [!DNL Upgrade Compatibility Tool] utilise des règles définies dans notre [Normes de codage](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) pour vous assurer que votre projet suit les bonnes pratiques d’Adobe Commerce et pour vous aider à améliorer et à étendre la variable [!DNL Upgrade Compatibility Tool].

Reportez-vous à la section [Contribution](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  rubrique pour plus d’informations sur la contribution à ce projet.

## Ressources

Nous avons développé les ressources suivantes pour vous aider à comprendre les mises à niveau d’Adobe Commerce :

- [Guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Versions à venir](https://devdocs.magento.com/release/)
- [Ressources de la communauté](https://devdocs.magento.com/community/resources/resources.html) pour plus d’informations.
