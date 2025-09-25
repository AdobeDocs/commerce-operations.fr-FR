---
title: Présentation de l’installation sur site
description: Découvrez le processus d’installation pour les déploiements sur site d’Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 9ad18dac76f171ad0f90330e1a1347baa056403b
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 2%

---


# Présentation de l’installation sur site

Cette page présente un aperçu de l’installation d’Adobe Commerce sur votre propre infrastructure. Le processus d’installation implique la configuration de votre environnement de serveur, l’obtention des logiciels et informations d’identification nécessaires et l’exécution de la commande d’installation.

Vous pouvez installer le logiciel sur site Adobe Commerce en 30 à 60 minutes environ. Toutefois, le temps nécessaire à la configuration de votre environnement de serveur avant l’installation varie en fonction de votre expérience et des technologies que vous sélectionnez.

>[!TIP]
>
>Vous devez disposer de connaissances techniques intermédiaires et d’un accès au serveur pour continuer avec succès.

L’installation permet de créer un magasin Adobe Commerce entièrement fonctionnel avec une [vitrine orientée client](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/storefront/storefront) et un [panneau d’administration](https://experienceleague.adobe.com/fr/docs/commerce-admin/start/admin/admin). Vos informations d’identification de base de données, informations de domaine et clés d’authentification doivent être prêtes avant de commencer le processus.

## Responsabilités du commerçant

Avec Adobe Commerce On-Premise, vous pouvez héberger et gérer votre propre infrastructure, y compris les serveurs, les environnements d’hébergement et la maintenance du système. Adobe fournit une assistance spécifique pour l’application Commerce principale, notamment :

- Accès aux mises à jour et correctifs de produits
- Correctifs de sécurité pour corriger les vulnérabilités
- Documentation complète pour vous aider à gérer et optimiser votre solution d’auto-hébergement

Vous avez un contrôle total sur votre environnement, ce qui vous permet d’offrir une personnalisation et une flexibilité accrues, mais vous êtes tenu de garantir les performances, la sécurité et l’évolutivité de l’infrastructure. Par exemple, vous êtes responsable des éléments suivants :

- La conception, l’implémentation, la configuration, la maintenance, le dépannage et les tests de performance de tous les systèmes Adobe Commerce On-Premise.
   - Serveurs, système d’exploitation, bases de données, [!DNL PHP], recherche, mise en cache, cache de page complète et réseau de diffusion de contenu. Les thèmes communs peuvent inclure (sans s’y limiter) [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] et tout [!DNL CDN] utilisé.
- Planification des capacités, mise à l’échelle automatique, mise en grappe, sauvegardes, reprise après sinistre
- Toutes les données sur les produits et les clients, la conception, la configuration et la configuration, la maintenance des applications et des bases de données, le déploiement du code, les mises à niveau de version et l&#39;application de correctifs
- Surveillance et alertes via APM/journalisation/alertes (par exemple, [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- Correctifs de sécurité pour le système d&#39;exploitation, la [!DNL PHP], la base de données, le renforcement des middleware et les mises à jour

## Workflow

Le diagramme suivant illustre les principales étapes de l’installation d’Adobe Commerce pour les environnements On-Premise :

![Fonctionnement de l’installation](../assets/installation/on-premises-install.drawio.svg)

### Configuration de votre environnement de serveur

Installez et configurez PHP, le serveur web, la base de données et le moteur de recherche selon les [conditions préalables](prerequisites/overview.md).

### Obtenir les clés d’authentification

Générez de nouvelles [clés d’authentification](prerequisites/authentication-keys.md) (ou copiez des clés existantes) à partir du Commerce Marketplace pour accéder aux packages du compositeur d’Adobe Commerce.

### Procurez-vous le logiciel Adobe Commerce.

Téléchargez à l’aide du [compositeur](prerequisites/commerce.md) (recommandé) ou clonez-le à partir de GitHub pour les contributions au développement.

Si vous souhaitez contribuer à la base de code Magento Open Source ou personnaliser l’application, [clonez](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) le référentiel GitHub. Cette méthode nécessite des connaissances préalables sur GitHub et le compositeur.

### Installation de l’application

Exécutez la commande d’installation avec votre configuration spécifique. Consultez le [démarrage rapide](composer.md) pour obtenir des exemples complets.

>[!NOTE]
>
>Si les étapes échouent, car le logiciel requis n’est pas configuré correctement, consultez les [prérequis](prerequisites/overview.md).

### Vérification de l’installation

[Testez](next-steps/verify.md) votre storefront et votre panneau d’administration pour vous assurer que tout fonctionne correctement.

## Problèmes d’installation courants

- **Erreurs d’autorisation** : vérifiez que la propriété et les autorisations du système de fichiers sont correctes
- **Échecs de connexion à la base de données** : vérifiez les informations d’identification de base de données et la connectivité réseau
- **Erreurs de clé d’authentification** : vérifiez que vos clés Commerce Marketplace sont valides et actives
- **Limites de mémoire** : assurez-vous que l&#39;allocation de mémoire PHP est suffisante (minimum 2 Go recommandé)
