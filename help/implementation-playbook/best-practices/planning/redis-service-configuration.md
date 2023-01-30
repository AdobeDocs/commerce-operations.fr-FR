---
title: Bonnes pratiques relatives à la configuration du service Redis
description: Découvrez comment améliorer les performances de mise en cache à l’aide de la mise en oeuvre étendue du cache Redis pour Adobe Commerce 2.3.5.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 12de523cc7ea1486c894d54efe6944d92d87ded0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Bonnes pratiques relatives à la configuration du service Redis

- Pour Adobe Commerce 2.3.3 et versions ultérieures déployées sur l’infrastructure cloud, effectuez une mise à niveau vers Redis version 5.0.
- Pour Adobe Commerce version 2.3.5 ou ultérieure, utilisez l’implémentation étendue du cache Redis. Cette implémentation comprend les optimisations suivantes afin de minimiser le nombre de requêtes Redis exécutées sur chaque requête d’Adobe Commerce :
   - Diminuer la taille des transferts de données réseau entre Redis et Adobe Commerce
   - Réduit la consommation des cycles du processeur en améliorant la capacité de l’adaptateur à déterminer automatiquement ce qui doit être chargé.
   - Réduction des conditions de concurrence sur les opérations d’écriture Redis

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud avec la version 2.3.3 ou ultérieure.
Adobe Commerce (toutes les méthodes de déploiement), version 2.3.5 et ultérieure

## Mise à jour de la version de Redis pour les déploiements cloud

Pour les déploiements Adobe Commerce sur l’infrastructure cloud avec Adobe Commerce 2.3.3 ou version ultérieure, mettez à niveau le service Redis vers la version 5.0. Pour obtenir des instructions, reportez-vous aux rubriques suivantes dans Adobe Commerce sur la documentation de l’infrastructure cloud :

- [Configuration du service Redis](https://devdocs.magento.com/cloud/project/services-redis.html)
- [Modification de la version du service](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## Configuration de l’implémentation étendue du cache Redis

Pour Adobe Commerce 2.3.5 et versions ultérieures, mettez à jour votre configuration afin d’utiliser l’implémentation étendue du cache Redis . `\Magento\Framework\Cache\Backend\Redis`.

### Configuration pour les déploiements cloud

Avec `ece-tools` 2002.1.1 ou version ultérieure, configurez le cache Redis amélioré en définissant la variable `REDIS_BACKEND` variable de déploiement dans le fichier de configuration de l&#39;environnement, `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Pour plus d’informations, voir [Déployer des variables > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) dans la documentation d’Adobe Commerce sur l’infrastructure cloud.

>[!NOTE]
>
> Vérifiez la version des outils de l’environnement cloud local à partir de la ligne de commande à l’aide de la fonction `composer show magento/ece-tools` . Si nécessaire, [mettre à jour la version de cee-tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

>[!WARNING]
>
>Do _not_ configurer une connexion Redis Secondaire pour les projets d’infrastructure cloud avec une [architecture mise à l’échelle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Cela entraîne des erreurs de connexion Redis. Voir [les instructions de configuration Redis ;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) dans le _Commerce sur l’infrastructure cloud_ guide.


### Configuration pour les déploiements sur site

Pour les déploiements sur site d’Adobe Commerce, configurez la nouvelle mise en oeuvre du cache Redis à l’aide du `bin/magento:setup` des commandes. Pour obtenir des instructions, voir [Utiliser des redis pour le cache par défaut](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Informations supplémentaires

- [Adobe Commerce version v2.3.5 - Amélioration des performances](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)


