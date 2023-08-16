---
title: Présentation de la variable [!DNL Upgrade Compatibility Tool]
description: En savoir plus sur les [!DNL Upgrade Compatibility Tool] et comment cela peut vous aider à gérer votre projet Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Présentation du guide

{{commerce-only}}

Ce guide est destiné aux administrateurs et aux ingénieurs logiciels d’Adobe Commerce. Il contient des informations détaillées sur l’installation de la variable [!DNL Upgrade Compatibility Tool], ainsi que sa configuration et sa gestion. Elle requiert une compréhension de base de la configuration et des fonctionnalités de base de Commerce.

## Présentation de la variable [!DNL Upgrade Compatibility Tool]

La variable [!DNL Upgrade Compatibility Tool] est un outil qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers une version plus récente d’Adobe Commerce.

## Utilisez la variable [!DNL Upgrade Compatibility Tool]

Vous pouvez utiliser la variable [!DNL Upgrade Compatibility Tool] via :

- Comme autonome [interface de ligne de commande](../upgrade-compatibility-tool/run.md) outil. Pour obtenir la liste complète des commandes disponibles, voir la section [`bin/uct` reference](/help/reference/uct.md).
- Intégration de la variable [!DNL Upgrade Compatibility Tool] avec la propriété [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Une configuration d’exécution dans la fonction [Module externe PHPStorm Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Le diagramme suivant montre les workflows possibles lors de l’exécution de la variable [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramme](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demo

Regardez cette vidéo pour en savoir plus sur les [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Améliorez les [!DNL Upgrade Compatibility Tool]

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

Pour vous connecter au [!DNL Upgrade Compatibility Tool] équipe, contactez-nous sur le canal Slack d’ingénierie [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Nous voulons entendre vos commentaires, vos problèmes et vos suggestions pour nous aider à améliorer l’outil.

La variable [!DNL Upgrade Compatibility Tool] utilise des règles définies dans notre [Normes de codage](https://developer.adobe.com/commerce/php/coding-standards/) pour vous assurer que votre projet suit les bonnes pratiques d’Adobe Commerce et pour vous aider à améliorer et à étendre la variable [!DNL Upgrade Compatibility Tool].

Voir [Contribution](https://developer.adobe.com/commerce/php/coding-standards/contributing/) rubrique pour plus d’informations sur l’apport de normes de codage.

## Ressources

Consultez les ressources suivantes pour vous aider à comprendre les mises à niveau d’Adobe Commerce :

- La variable [guide de mise à niveau](../overview.md) fournit un aperçu du parcours de mise à niveau standard d’Adobe Commerce ou de Magento Open Source et des bonnes pratiques à suivre le long de ce parcours.
- La variable [versions à venir](https://devdocs.magento.com/release/) indique les dates des versions planifiées et à venir.
- La variable [ressources communautaires](https://developer.adobe.com/commerce/contributor/community/) pour commencer des discussions ou pour trouver plus d’informations.
- Vérifiez les [outils connexes](../upgrade-compatibility-tool/related-tools.md) pour des outils utiles dans votre parcours de mise à niveau classique.
