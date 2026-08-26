---
title: Configurez l’intégration GitHub pour  [!DNL Adobe Commerce Patching Automation]
description: Découvrez comment installer l’application  [!DNL Adobe Commerce Patching Automation]  pour activer les opérations de correctif pour les projets Adobe Commerce Cloud connectés à GitHub.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---


# Configuration de l’intégration GitHub pour [!DNL Patching Automation]

Si votre projet Adobe Commerce Cloud est connecté à un référentiel GitHub, vous devez installer l’application GitHub [!DNL Patching Automation] avant de pouvoir utiliser le service pour appliquer ou rétablir des correctifs. L’application accorde au service l’accès dont il a besoin pour apporter des modifications à votre référentiel en votre nom.

## Conditions préalables

* Un abonnement Adobe Commerce Cloud actif
* Une [&#x200B; intégration GitHub &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) déjà configurée pour votre projet Adobe Commerce Cloud, avec son option [`fetch-branches` activée](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL Patching Automation] crée et envoie les branches temporaires d’environnement d’intégration. Les opérations de correctif ne parviennent donc pas à créer l’environnement lorsque cette option est désactivée.
* Référentiel hébergé sur [!DNL github.com]. Les intégrations GitHub configurées avec un domaine personnalisé ne sont pas prises en charge.
* Accès du propriétaire ou de l’administrateur à l’organisation ou au référentiel GitHub

## Installation de l’application GitHub [!DNL Patching Automation]

Vous pouvez démarrer l’installation à partir de [!DNL Patching Automation] en cliquant sur **[!UICONTROL Install GitHub App]** dans l’interface utilisateur, ce qui vous redirige vers la page d’installation, ou en accédant directement à la page d’installation.

1. Ouvrez la page [&#x200B; Installation de l’application GitHub d’automatisation des correctifs &#x200B;](https://github.com/apps/adobe-commerce-patching-automation).
1. Cliquez sur **[!UICONTROL Install]**.
1. Sélectionnez l’organisation GitHub propriétaire de votre référentiel Adobe Commerce.
1. Sous **[!UICONTROL Repository access]**, sélectionnez **[!UICONTROL Only select repositories]** et choisissez le référentiel de votre projet Adobe Commerce.
1. Cliquez sur **[!UICONTROL Install]** pour confirmer.

Une fois installé, le service détecte automatiquement votre connexion GitHub et utilise l’application pour toutes les opérations de correctif. Aucune configuration supplémentaire n’est requise.

## Vérifier et gérer l’état de la connexion

L’interface utilisateur [!DNL Patching Automation] affiche le statut actuel de votre connexion GitHub, avec des actions disponibles en fonction de ce statut :

* **[!UICONTROL Refresh]**/**[!UICONTROL Refresh status]** - Vérifie à nouveau le statut de la connexion sans apporter de modifications.
* **[!UICONTROL Reinstall]** - Affiché si l’installation n’est plus valide (par exemple, si elle a été suspendue ou si le référentiel connecté à votre projet cloud a été modifié). Démarre le même flux d’installation que celui décrit ci-dessus.
* **[!UICONTROL Unlink GitHub App]** - Supprime la connexion enregistrée de [!DNL Patching Automation] à l’application GitHub. Cette opération ne désinstalle **pas** l’application à partir de votre référentiel GitHub. Pour supprimer entièrement l’accès, consultez la section Désinstaller ci-dessous.

## Désinstallation de l’application GitHub [!DNL Patching Automation]

Si vous ne souhaitez plus que le service accède à votre référentiel :

1. Dans GitHub, ouvrez les paramètres du compte propriétaire de l’installation :
   * Pour un référentiel **détenu par l’organisation** : **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Pour un référentiel **personnel** : **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Recherchez `adobe-commerce-patching-automation` et cliquez sur **[!UICONTROL Configure]**.
1. Cliquez sur **[!UICONTROL Uninstall]** et confirmez.

>[!WARNING]
>
>Si des opérations d’application ou de restauration sont toujours en cours lors de la désinstallation de l’application GitHub, ces opérations peuvent échouer. Après la désinstallation de l’application, les utilisateurs ne peuvent pas non plus démarrer de nouvelles opérations, car les boutons d’action deviennent inactifs.

## Rubriques connexes

* [Présentation de l&#39;automatisation des correctifs](intro.md)
* [Accès](access.md)
* [Présentation des workflows](workflow.md)
* [Bonnes pratiques](best-practices.md)
* [Dépannage](troubleshooting.md)
