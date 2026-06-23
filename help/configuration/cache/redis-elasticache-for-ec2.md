---
title: Configuration de Redis avec AWS ElastiCache
description: Découvrez comment utiliser AWS ElastiCache en tant que serveur principal Redis pour Adobe Commerce sur EC2. Découvrez l’installation, la configuration et la validation de la ligne de commande.
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fbb1d92d5f8537e6f1436cd985af120114883df6
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---


# Configuration de Redis avec AWS ElastiCache

Depuis Commerce version 2.4.3, les instances hébergées sur Amazon EC2 peuvent utiliser un ElastiCache AWS à la place d’une instance Redis locale.

>[!WARNING]
>
>Cette section s’applique uniquement aux instances Commerce s’exécutant sur des VPC EC2 d’Amazon.

## Conditions préalables

- **Créer un cache Redis OSS sans serveur** : à partir de la console de gestion AWS, créez le cache Redis dans la même région et le même VPC de l’instance EC2. Pour obtenir des instructions, consultez la [documentation d’AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Vérifier la connexion à votre instance Commerce EC2**

   - Ouvrez une connexion SSH à votre instance EC2
   - Sur l’instance EC2, installez le client Redis :

     ```shell
     sudo apt-get install redis
     ```

   - Ajoutez une règle entrante au groupe de sécurité EC2 : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Ajoutez une règle entrante au groupe de sécurité de cluster ElastiCache : Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connectez-vous à l’interface de ligne de commande Redis :

     ```shell
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configuration de Commerce pour utiliser le cluster

Commerce prend en charge plusieurs types de configurations de mise en cache. En règle générale, les configurations de mise en cache sont réparties entre le serveur frontal et le serveur principal. La mise en cache front-end est classée comme `default`, utilisée pour tout type de cache. Vous pouvez personnaliser ou diviser les caches en caches de niveau inférieur pour obtenir de meilleures performances. Une configuration Redis courante consiste à séparer le cache par défaut et le cache de page dans leur propre base de données Redis (RDB).

Exécutez `setup` commandes pour spécifier les points d’entrée Redis.

Pour configurer Commerce pour Redis en tant que mise en cache par défaut :

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Pour configurer Commerce pour la mise en cache de page Redis, procédez comme suit :

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Pour configurer Commerce afin d’utiliser Redis pour le stockage de session :

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Vérifier la connectivité

**Pour vérifier que Commerce communique avec ElastiCache** :

1. Ouvrez une connexion SSH à l’instance Commerce EC2.
1. Démarrez le moniteur Redis.

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Ouvrez une page dans l’interface utilisateur de Commerce.
1. Vérifiez la sortie [cache](#verify-connectivity) dans votre terminal.
