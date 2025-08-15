---
title: Bonnes pratiques de déploiement de contenu statique
description: Découvrez comment éviter les problèmes liés au contenu statique qui n’apparaît pas sur votre storefront Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Bonnes pratiques de déploiement de contenu statique

Cet article aborde les bonnes pratiques de déploiement de contenu statique (SCD) dans Adobe Commerce afin d’éviter les problèmes où le contenu statique n’est pas disponible sur votre site web.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

* Adobe Commerce sur les infrastructures cloud
* Adobe Commerce On-Premise

## Bonnes pratiques

Pour éviter tout problème d’indisponibilité du contenu statique sur votre site web, suivez ces bonnes pratiques pour vous assurer que votre contenu statique est configuré et déployé correctement :

1. Veillez à suivre les directives de déploiement :
   * Pour Adobe Commerce On-premise (toutes les versions), consultez [Présentation du déploiement](../../../configuration/deployment/overview.md) dans notre documentation destinée aux développeurs.
   * Pour Adobe Commerce sur les infrastructures cloud (toutes les versions), consultez les sections [Processus de déploiement dans le cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) et [Stratégies de déploiement de contenu statique](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/static-content) dans la documentation destinée aux développeurs et développeuses.

1. Pour Adobe Commerce sur les infrastructures cloud (toutes les versions), assurez-vous que ece-tools figure dans la version la plus récente. Voir : [Mise à jour de la version ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) dans notre documentation destinée aux développeurs.
1. Pour Adobe Commerce sur les infrastructures cloud (toutes les versions), assurez-vous que le contenu statique est déployé pendant la phase de création plutôt que pendant la phase de déploiement. Voir : [Gestion de la configuration pour les paramètres de magasin - Performances de déploiement de contenu statique](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over) dans notre documentation destinée aux développeurs.
1. Assurez-vous que vous ne disposez pas de tâches cron de longue durée et supprimez tous les processus cron de longue durée. Les tâches cron de longue durée peuvent utiliser des ressources CPU et potentiellement augmenter considérablement le temps de déploiement.
1. Pour Adobe Commerce On-Premise (toutes les versions), vérifiez que le processus `php` dans l’interface de ligne de commande a accès au répertoire `pub/static`. Sinon, vous pourriez rencontrer un problème en raison duquel un déploiement de contenu statique ne pourra pas écrire de fichiers dans ce répertoire. Pour plus d’informations : [ Autorisations d’accès aux systèmes de fichiers ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) dans notre documentation destinée aux développeurs.
1. Assurez-vous que le répertoire `generated` n’est pas un répertoire partagé entre les versions ; dans le cas contraire, les versions peuvent échouer de manière aléatoire. Pour plus d’informations :
   * Adobe Commerce On-premise (toutes les versions) : [Détails techniques](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) dans notre documentation destinée aux développeurs.
   * Adobe Commerce sur les infrastructures cloud (toutes versions) : [Processus de déploiement - Phase 2 : build](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) dans notre documentation destinée aux développeurs.

1. Vérifiez votre stratégie SCD. La stratégie *rapide* est la stratégie par défaut. Pour plus d’informations :
   * Adobe Commerce On-premise (toutes les versions) : [stratégies de déploiement de fichiers statiques](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) dans notre documentation destinée aux développeurs.
   * Adobe Commerce sur les infrastructures cloud (toutes les versions) : [Déployer les variables - SCD\_STRATEGY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy) dans notre documentation destinée aux développeurs.

## Informations supplémentaires

Dans notre documentation destinée aux développeurs :

* [ Conteneur de contenu statique ](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Signature de contenu statique](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Déployer des variables - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [Flux de déploiement](../../../performance/deployment-flow.md)
* [Aucun déploiement sans interruption](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [Optimisation du déploiement dans le cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
