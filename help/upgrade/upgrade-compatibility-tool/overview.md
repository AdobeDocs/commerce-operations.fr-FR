---
title: '"Présentation de la variable [!DNL Upgrade Compatibility Tool]"'
description: En savoir plus sur les [!DNL Upgrade Compatibility Tool] et comment cela peut vous aider dans votre projet Adobe Commerce.
source-git-commit: 9b0f97d36092d2a1057cdc905671cda8540881c9
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Présentation du guide

{{commerce-only}}

Ce guide est destiné aux administrateurs et aux ingénieurs logiciels d’Adobe Commerce. Il contient des informations détaillées sur l’installation de la variable [!DNL Upgrade Compatibility Tool], ainsi que sa configuration et sa gestion. Elle requiert une compréhension de base de la configuration et des fonctionnalités de base de Commerce.

## Présentation de la variable [!DNL Upgrade Compatibility Tool]

Le [!DNL Upgrade Compatibility Tool] est un outil qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers une version plus récente d’Adobe Commerce.

## Utilisez la variable [!DNL Upgrade Compatibility Tool]

Vous pouvez utiliser la variable [!DNL Upgrade Compatibility Tool] via :

- En tant qu’autonome [interface de ligne de commande](../upgrade-compatibility-tool/run.md) outil.
- Intégration de la variable [!DNL Upgrade Compatibility Tool] avec le [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Une configuration d’exécution dans la fonction [Module externe PHPStorm Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Le diagramme suivant montre les workflows possibles lors de l’exécution de la variable [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramme](../../assets/upgrade-guide/uct-diagram-v5.png)

## Améliorez les [!DNL Upgrade Compatibility Tool]

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

Pour vous connecter au [!DNL Upgrade Compatibility Tool] équipe, contactez-nous sur le canal Slack d’ingénierie [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Nous voulons entendre vos commentaires, vos problèmes et vos suggestions pour nous aider à améliorer l’outil.

Le [!DNL Upgrade Compatibility Tool] utilise des règles définies dans notre [Normes de codage](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) pour vous assurer que votre projet suit les bonnes pratiques d’Adobe Commerce et pour vous aider à améliorer et à étendre la variable [!DNL Upgrade Compatibility Tool].

Reportez-vous à la section [Contribution](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) rubrique pour plus d’informations sur l’apport de normes de codage.

## Ressources

Consultez les ressources suivantes pour vous aider à comprendre les mises à niveau d’Adobe Commerce :

- Le [guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) fournit un aperçu du parcours de mise à niveau standard d’Adobe Commerce ou de Magento Open Source et des bonnes pratiques à suivre le long de ce parcours.
- Le [versions à venir](https://devdocs.magento.com/release/) indique les dates des versions planifiées et à venir.
- Le [ressources communautaires](https://developer.adobe.com/commerce/contributor/community/) pour commencer des discussions ou pour trouver plus d’informations.
- Vérifiez les [outils connexes](../upgrade-compatibility-tool/related-tools.md) pour des outils utiles dans votre parcours de mise à niveau classique.
