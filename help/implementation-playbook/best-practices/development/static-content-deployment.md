---
title: Bonnes pratiques de déploiement de contenu statique
description: Découvrez comment éviter les problèmes liés au contenu statique qui n’apparaît pas sur votre vitrine Adobe Commerce ou Magento Open Source.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# Bonnes pratiques de déploiement de contenu statique

Cet article présente les bonnes pratiques de déploiement de contenu statique (SCD) dans Adobe Commerce afin d’éviter les problèmes où le contenu statique ne serait pas disponible sur votre site web.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

* Adobe Commerce sur l’infrastructure cloud
* Adobe Commerce sur site
* Magento Open Source

## Bonnes pratiques

Pour éviter qu’un problème lié au contenu statique ne soit pas disponible sur votre site web, suivez les bonnes pratiques suivantes pour vous assurer que votre contenu statique est correctement configuré et déployé :

1. Veillez à suivre les instructions de déploiement :
   * Pour Adobe Commerce On-Premise et Magento Open Source (toutes versions), voir [Présentation du déploiement](../../../configuration/deployment/overview.md) dans notre documentation destinée aux développeurs.
   * Pour Adobe Commerce sur l’infrastructure cloud (toutes les versions), voir [Processus de déploiement dans le cloud](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) et [Stratégies de déploiement de contenu statique](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) dans notre documentation destinée aux développeurs.

1. Pour Adobe Commerce sur l’infrastructure cloud (toutes les versions), assurez-vous que les outils de la nouvelle version sont disponibles. Voir : [Mise à jour de la version de ece-tools](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) dans notre documentation destinée aux développeurs.
1. Pour Adobe Commerce sur l’infrastructure cloud (toutes les versions), assurez-vous que le contenu statique est déployé pendant la phase de création plutôt que pendant la phase de déploiement. Voir : [Gestion des configurations des paramètres de magasin - Performances de déploiement de contenu statique](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) dans notre documentation destinée aux développeurs.
1. Assurez-vous de ne pas avoir de tâches cron longues et de supprimer tout processus cron long terme. Les tâches cron de longue durée peuvent prendre en charge les ressources du processeur et éventuellement augmenter considérablement le temps de déploiement.
1. Pour Adobe Commerce On-Premise et Magento Open Source (toutes versions), vérifiez que la variable `php` Le processus dans l’interface de ligne de commande a accès à `pub/static` répertoire . Dans le cas contraire, vous pourriez rencontrer un problème en raison duquel un déploiement de contenu statique ne peut pas écrire de fichiers dans ce répertoire. Pour plus d’informations : [Autorisations d’accès aux systèmes de fichiers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) dans notre documentation destinée aux développeurs.
1. Assurez-vous que la variable `generated` Le répertoire n’est pas un répertoire partagé entre les versions ; dans le cas contraire, les versions peuvent échouer de manière aléatoire. Pour plus d’informations :
   * Adobe Commerce On-Premise et Magento Open Source (toutes versions) : [Détails techniques](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) dans notre documentation destinée aux développeurs.
   * Adobe Commerce sur l’infrastructure cloud (toutes versions) : [Processus de déploiement - Phase 2 : build](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) dans notre documentation destinée aux développeurs.

1. Vérifiez votre stratégie SCD. Le *quick* stratégie est la valeur par défaut. Pour plus d’informations :
   * Adobe Commerce On-Premise et Magento Open Source (toutes versions) : [Stratégies de déploiement des fichiers statiques](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) dans notre documentation destinée aux développeurs.
   * Adobe Commerce sur l’infrastructure cloud (toutes versions) : [Déployer des variables - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) dans notre documentation destinée aux développeurs.

## Informations supplémentaires

Dans notre documentation destinée aux développeurs :

* [Conteneur de contenu statique](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Signature de contenu statique](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Déployer des variables - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Flux de déploiement](../../../performance/deployment-flow.md)
* [Déploiement sans interruption](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Optimisation du déploiement dans le cloud](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

