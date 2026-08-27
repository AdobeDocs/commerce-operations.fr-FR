---
title: Accès [!DNL Adobe Commerce Patching Automation]
description: Découvrez comment accéder à et utiliser  [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Accès à [!DNL Adobe Commerce Patching Automation]

## Conditions préalables

[!DNL Patching Automation] utilise le contrôle d’accès basé sur les rôles d’Adobe Commerce Cloud. Votre niveau d’accès dans la console cloud détermine ce que vous pouvez faire avec le service.

### Qui peut utiliser [!DNL Patching Automation]

* **Administrateur de projet** - Peut appliquer ou rétablir des correctifs sur tous les environnements
* **Contributeur** - Peut appliquer ou rétablir des correctifs sur les environnements qui lui sont affectés
* **Visionneuse** - Peut uniquement afficher le projet et les environnements, aucune action n’est autorisée.

### Comment demander l’accès à un projet

Si vous ne voyez aucun projet dans l’interface utilisateur d’[!DNL Patching Automation], demandez l’accès à la personne appropriée :

* Contactez le propriétaire du compte ou l’administrateur du projet
* Ils vous accorderont le rôle approprié via la console cloud
* Une fois l’accès accordé, vous pouvez vous connecter à la console cloud pour utiliser le service

>[!NOTE]
>
>[!DNL Patching Automation] suit le même modèle d’autorisation qu’Adobe Commerce Cloud. Votre niveau d’accès dans la console cloud détermine donc ce que vous pouvez faire avec le service.

## Accès aux [!DNL Patching Automation]

[!DNL Patching Automation] est disponible sous la forme d’un onglet dans le tableau de bord [!DNL Site-Wide Analysis Tool]. Vous pouvez y accéder à partir de votre panneau d’administration en accédant à **Rapports** > **Informations système** > **Outil d’analyse à l’échelle du site** sur la barre latérale d’administration. Consultez [Accès à l’outil d’analyse à l’échelle du site](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/site-wide-analysis-tool/access) pour connaître les conditions préalables et la configuration des autorisations.

Une fois que vous êtes dans le tableau de bord :

1. Cliquez sur l’onglet [!UICONTROL Patching Automation] dans l’interface.
1. Sélectionnez le projet et l’environnement dans lesquels vous souhaitez appliquer des correctifs.
1. Examinez les correctifs disponibles et leur statut de compatibilité.
1. Sélectionnez les correctifs à appliquer ou à rétablir.

## Accès à l’environnement de production

Pour les environnements de production, des mesures de protection supplémentaires s’appliquent par défaut :

* **Mode de maintenance** - Doit être activé
* **Tâches cron** - Doivent être désactivées
* **Boîte de dialogue de confirmation** - Doit être renseignée avant de continuer

>[!IMPORTANT]
>
>L’application de correctifs à l’environnement de production nécessite une préparation et des mesures de protection appropriées pour éviter les perturbations accidentelles.

>[!NOTE]
>
>Vous pouvez ignorer les vérifications du mode de maintenance et de la tâche cron en cochant la case Remplacer dans l’interface utilisateur (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*). N’utilisez cette option que si vous comprenez le risque lié à l’application de correctifs à la production sans ces mesures de protection.

## Rubriques connexes

* [Présentation de l&#39;automatisation des correctifs](intro.md)
* [Présentation des workflows](workflow.md)
* [Intégration de GitHub](github-integration.md)
* [Bonnes pratiques](best-practices.md)
* [Dépannage](troubleshooting.md)
