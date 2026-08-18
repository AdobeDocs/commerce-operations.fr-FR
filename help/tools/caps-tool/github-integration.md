---
title: Configurez l’intégration GitHub pour  [!DNL CAPS]
description: Découvrez comment installer l’application  [!DNL Cloud Automation Patching Service (CAPS)]  pour activer les opérations de correctif pour les projets Adobe Commerce Cloud connectés à GitHub.
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# Configuration de l’intégration GitHub pour [!DNL CAPS]

Si votre projet Adobe Commerce Cloud est connecté à un référentiel GitHub, vous devez installer l’application GitHub [!DNL CAPS] avant de pouvoir utiliser l’[!DNL Cloud Automation Patching Service] ([!DNL CAPS]) pour appliquer ou rétablir des correctifs. L’application [!DNL CAPS] accorde l’accès dont elle a besoin pour apporter des modifications à votre référentiel en votre nom.

## Conditions préalables

* Un abonnement Adobe Commerce Cloud actif
* Une [&#x200B; intégration GitHub &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) déjà configurée pour votre projet Adobe Commerce Cloud, avec son option [`fetch-branches` activée](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL CAPS] crée et envoie les branches temporaires d’environnement d’intégration. Les opérations de correctif ne parviennent donc pas à créer l’environnement lorsque cette option est désactivée.
* Référentiel hébergé sur [!DNL github.com]. Les intégrations GitHub configurées avec un domaine personnalisé ne sont pas prises en charge.
* Accès du propriétaire ou de l’administrateur à l’organisation ou au référentiel GitHub

## Installation de l’application GitHub [!DNL CAPS]

1. Ouvrez la page d’installation de l’application [CAPS GitHub](https://github.com/apps/adobe-commerce-patching-automation).
1. Cliquez sur **[!UICONTROL Install]**.
1. Sélectionnez l’organisation GitHub propriétaire de votre référentiel Adobe Commerce.
1. Sous **[!UICONTROL Repository access]**, sélectionnez **[!UICONTROL Only select repositories]** et choisissez le référentiel de votre projet Adobe Commerce.
1. Cliquez sur **[!UICONTROL Install]** pour confirmer.

Une fois installé, [!DNL CAPS] détecte automatiquement votre connexion GitHub et utilise l’application pour toutes les opérations de correctif. Aucune configuration supplémentaire n’est requise.

## Désinstallation de l’application GitHub [!DNL CAPS]

Si vous ne souhaitez plus que [!DNL CAPS] accédiez à votre référentiel :

1. Dans GitHub, ouvrez les paramètres du compte propriétaire de l’installation :
   * Pour un référentiel **détenu par l’organisation** : **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Pour un référentiel **personnel** : **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Recherchez `adobe-commerce-patching-automation` et cliquez sur **[!UICONTROL Configure]**.
1. Cliquez sur **[!UICONTROL Uninstall]** et confirmez.

>[!WARNING]
>
>Si des opérations d’application de CAPS ou de rétablissement sont toujours en cours lorsque l’application GitHub est désinstallée, ces opérations peuvent échouer. Après la désinstallation de l’application, les utilisateurs ne peuvent pas non plus démarrer de nouvelles opérations, car les boutons d’action deviennent inactifs.

## Rubriques connexes

* [Présentation de CAPS](intro.md)
* [Accès](access.md)
* [Présentation des workflows](workflow.md)
* [Bonnes pratiques](best-practices.md)
* [Dépannage](troubleshooting.md)
