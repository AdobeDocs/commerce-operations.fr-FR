---
title: Configuration de Redis avec AWS ElastiCache
description: Pour les instances Commerce hébergées sur EC2, découvrez comment utiliser ElastiCache d’AWS au lieu d’une instance Redis locale. Découvrez l’installation de la ligne de commande, les options de configuration et les techniques de validation.
feature: Configuration, Cache
source-git-commit: b66479ee1350d92c1d59212283222e5068c263a6
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Configuration de Redis avec AWS ElastiCache

Depuis Commerce version 2.4.3, les instances hébergées sur Amazon EC2 peuvent utiliser un ElastiCache AWS à la place d’une instance Redis locale.

>[!WARNING]
>
>Cette section s’applique uniquement aux instances Commerce s’exécutant sur des VPC EC2 d’Amazon. Il ne fonctionne pas pour les installations sur site.

## Conditions préalables

- **Créer un cache Redis OSS sans serveur** : à partir de la console de gestion AWS, créez le cache Redis dans la même région et le même VPC de l’instance EC2. Pour obtenir des instructions, consultez la [documentation d’AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Vérifier la connexion à votre instance Commerce EC2**

   - Ouvrez une connexion SSH à votre instance EC2
   - Sur l’instance EC2, installez le client Redis :

     ```bash
     sudo apt-get install redis
     ```

   - Ajoutez une règle entrante au groupe de sécurité EC2 : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Ajoutez une règle entrante au groupe de sécurité de cluster ElastiCache : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connectez-vous à l’interface de ligne de commande Redis :

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configuration de Commerce pour utiliser le cluster

Commerce prend en charge plusieurs types de configurations de mise en cache. En règle générale, les configurations de mise en cache sont réparties entre le serveur frontal et le serveur principal. La mise en cache front-end est classée comme `default`, utilisée pour tout type de cache. Vous pouvez personnaliser ou diviser les caches en caches de niveau inférieur pour obtenir de meilleures performances. Une configuration Redis courante consiste à séparer le cache par défaut et le cache de page dans leur propre base de données Redis (RDB).

Exécutez `setup` commandes pour spécifier les points d’entrée Redis.

Pour configurer Commerce pour Redis en tant que mise en cache par défaut :

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Pour configurer Commerce pour la mise en cache de page Redis, procédez comme suit :

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Pour configurer Commerce afin d’utiliser Redis pour le stockage de session :

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Vérifier la connectivité

**Pour vérifier que Commerce communique avec ElastiCache** :

1. Ouvrez une connexion SSH à l’instance Commerce EC2.
1. Démarrez le moniteur Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Ouvrez une page dans l’interface utilisateur de Commerce.
1. Vérifiez la sortie [cache](#verify-the-redis-connection) dans votre terminal.
