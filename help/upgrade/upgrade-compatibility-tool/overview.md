---
title: Présentation de  [!DNL Upgrade Compatibility Tool]
description: Découvrez  [!DNL Upgrade Compatibility Tool] et comment il peut vous aider à gérer votre projet Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Présentation du guide

{{commerce-only}}

Ce guide est destiné aux administrateurs et aux ingénieurs logiciels d’Adobe Commerce. Il contient des informations détaillées sur l’installation de [!DNL Upgrade Compatibility Tool], ainsi que sur sa configuration et sa gestion. Elle requiert une compréhension de base de la configuration et des fonctionnalités de base de Commerce.

## Présentation du [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] est un outil qui vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers une version plus récente d’Adobe Commerce.

## Utilisez le [!DNL Upgrade Compatibility Tool]

Vous pouvez utiliser le [!DNL Upgrade Compatibility Tool] via :

- En tant qu&#39;outil [interface de ligne de commande](../upgrade-compatibility-tool/run.md) autonome. Pour obtenir la liste complète des commandes disponibles, consultez la [`bin/uct` référence](../../tools/reference/uct.md).
- Intégration de [!DNL Upgrade Compatibility Tool] à [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Une configuration d’exécution dans le [module externe PHPStorm Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Le diagramme suivant montre les workflows possibles lors de l’exécution de [!DNL Upgrade Compatibility Tool] :

![[!DNL Upgrade Compatibility Tool] Diagramme](../../assets/upgrade-guide/uct-diagram-v5.png)

## Démo [!DNL Upgrade Compatibility Tool]

Regardez cette vidéo pour en savoir plus sur [!DNL Upgrade Compatibility Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Aider à améliorer le [!DNL Upgrade Compatibility Tool]

Si vous avez besoin d’informations ou si vous avez des questions qui ne sont pas abordées dans ce guide, utilisez les ressources suivantes :

Pour nous connecter à l&#39;équipe [!DNL Upgrade Compatibility Tool], contactez-nous sur le canal du Slack d&#39;ingénierie [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Nous voulons entendre vos commentaires, vos problèmes et vos suggestions pour nous aider à améliorer l’outil.

L’ [!DNL Upgrade Compatibility Tool] utilise des règles définies dans nos [normes de codage](https://developer.adobe.com/commerce/php/coding-standards/) pour s’assurer que votre projet suit les bonnes pratiques Adobe Commerce et pour vous aider à améliorer et à étendre le [!DNL Upgrade Compatibility Tool].

Pour plus d’informations sur la contribution des normes de codage, reportez-vous à la rubrique [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) .

## Ressources

Consultez les ressources suivantes pour vous aider à comprendre les mises à niveau d’Adobe Commerce :

- Le [guide de mise à niveau](../overview.md) donne un aperçu du parcours de mise à niveau standard d’Adobe Commerce et des bonnes pratiques à suivre le long de ce parcours.
- La page [prochaines versions](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) indique les dates des versions planifiées et à venir.
- La page [ressources de la communauté](https://developer.adobe.com/commerce/contributor/community/) doit servir à lancer des discussions ou à trouver plus d’informations.
- Consultez la page [ outils connexes](../upgrade-compatibility-tool/related-tools.md) pour obtenir des outils utiles dans votre parcours de mise à niveau classique.
