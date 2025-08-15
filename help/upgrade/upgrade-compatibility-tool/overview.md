---
title: Vue d’ensemble du  [!DNL Upgrade Compatibility Tool]
description: Découvrez le  [!DNL Upgrade Compatibility Tool]  et comment il peut vous aider à réaliser votre projet Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Présentation du guide

{{commerce-only}}

Ce guide est destiné aux administrateurs et aux ingénieurs logiciel d’Adobe Commerce. Elle contient des informations détaillées sur l’installation du [!DNL Upgrade Compatibility Tool], ainsi que sur sa configuration et sa gestion. Il suppose une compréhension de base de la configuration et des fonctionnalités de base de Commerce.

## Présentation de l’[!DNL Upgrade Compatibility Tool]

Le [!DNL Upgrade Compatibility Tool] est un outil qui compare une instance personnalisée Adobe Commerce à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers une version plus récente d’Adobe Commerce.

## Utiliser le [!DNL Upgrade Compatibility Tool]

Vous pouvez utiliser le [!DNL Upgrade Compatibility Tool] via :

- Comme outil autonome [interface de ligne de commande](../upgrade-compatibility-tool/run.md). Pour obtenir la liste complète des commandes disponibles, reportez-vous à la référence [`bin/uct`](../../tools/reference/uct.md).
- Intégration de la [!DNL Upgrade Compatibility Tool] au [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Une configuration d’exécution dans le plug-in [Magento PHPStorm](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Le diagramme suivant montre les workflows possibles lors de l’exécution du [!DNL Upgrade Compatibility Tool] :

![[!DNL Upgrade Compatibility Tool] Diagramme](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] de démonstration

Regardez cette vidéo pour en savoir plus sur le [!DNL Upgrade Compatibility Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Contribuez à améliorer l’[!DNL Upgrade Compatibility Tool]

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

Pour entrer en contact avec l&#39;équipe [!DNL Upgrade Compatibility Tool], contactez-nous sur le canal Engineering Slack [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Nous voulons connaître vos commentaires, problèmes et suggestions pour nous aider à améliorer l’outil.

Le [!DNL Upgrade Compatibility Tool] utilise les règles définies dans nos [normes de codage](https://developer.adobe.com/commerce/php/coding-standards/) pour vous assurer que votre projet respecte les bonnes pratiques d’Adobe Commerce et pour vous aider à améliorer et à étendre l’[!DNL Upgrade Compatibility Tool].

Reportez-vous à la rubrique [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) pour plus d’informations sur les normes de codage contributives.

## Ressources

Consultez les ressources suivantes pour mieux comprendre les mises à niveau d’Adobe Commerce :

- Le [ guide de mise à niveau ](../overview.md) présente un aperçu du parcours de mise à niveau d’Adobe Commerce type et des bonnes pratiques à suivre le long de ce parcours.
- La page [prochaines versions](https://experienceleague.adobe.com/fr/docs/commerce-operations/release/planning/schedule) indique les dates des versions planifiées et à venir.
- La page [Ressources de la communauté](https://developer.adobe.com/commerce/contributor/community/) est un endroit où commencer les discussions ou trouver plus d’informations.
- Consultez la page [Outils associés](../upgrade-compatibility-tool/related-tools.md) pour découvrir des outils utiles dans votre parcours de mise à niveau standard.
