---
title: Accès [!DNL Cloud Automation Patching Service (CAPS)]
description: Découvrez comment accéder à et utiliser  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Accès à [!DNL Cloud Automation Patching Service (CAPS)]

## Conditions préalables

[!DNL CAPS] utilise le contrôle d’accès basé sur les rôles d’Adobe Commerce Cloud. Votre niveau d’accès dans la console cloud détermine ce que vous pouvez faire avec [!DNL CAPS].

### Qui peut utiliser [!DNL CAPS]

* **Administrateur de projet** - Peut appliquer ou rétablir des correctifs sur tous les environnements
* **Contributeur** - Peut appliquer ou rétablir des correctifs sur les environnements qui lui sont affectés
* **Visionneuse** - Peut uniquement afficher le projet et les environnements, aucune action n’est autorisée.

### Comment demander l’accès à un projet

Si vous ne voyez aucun projet dans l’interface utilisateur [!DNL CAPS], vous devez demander l’accès à la personne appropriée :

* Contactez le propriétaire du compte ou l’administrateur du projet
* Ils vous accorderont le rôle approprié via la console cloud
* Une fois l’accès accordé, vous pouvez vous connecter à la console Cloud pour utiliser [!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS] suit le même modèle d’autorisation qu’Adobe Commerce Cloud. Votre niveau d’accès dans la console Cloud détermine donc ce que vous pouvez faire avec [!DNL CAPS].

## Accès aux [!DNL CAPS]

L’outil CAPS est disponible dans le tableau de bord de l’outil d’analyse à l’échelle du site à l’adresse [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/). Sous l’onglet Automatisation de l’application de correctifs , vous pouvez sélectionner votre projet et votre environnement.

1. Accédez à l’outil d’analyse à l’échelle du site sur [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/).
1. Cliquez sur l’onglet [!UICONTROL Patching Automation] dans l’interface.
1. Sélectionnez le projet et l’environnement dans lesquels vous souhaitez appliquer des correctifs.
1. Examinez les correctifs disponibles et leur statut de compatibilité.
1. Sélectionnez les correctifs à appliquer ou à rétablir.

## Accès à l’environnement de production

Pour les environnements de production, des mesures de protection supplémentaires s’appliquent :

* **Mode de maintenance** - Doit être activé
* **Tâches cron** - Doivent être désactivées
* **Boîte de dialogue de confirmation** - Doit être renseignée avant de continuer

>[!IMPORTANT]
>
>L’application de correctifs à l’environnement de production nécessite une préparation et des mesures de protection appropriées pour éviter les perturbations accidentelles.

## Rubriques connexes

* [Présentation de CAPS](intro.md)
* [Workflow](workflow.md)
* [Bonnes pratiques](best-practices.md)
* [Dépannage](troubleshooting.md)
