---
title: Options du serveur principal de mise en cache et référence de stockage
description: Découvrez les options du serveur principal de cache dans Adobe Commerce, notamment le système de fichiers, Redis, Valkey et le stockage dans la base de données. Découvrez les approches héritées et modernes.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="Sur Site" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="S’applique uniquement aux projets sur site Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 761
ht-degree: 0%

---

# Mettre en cache les options principales et la référence de stockage

>[!NOTE]
>
>Cette page documente la configuration `app/etc/env.php` locale.
>
>Pour les projets [!DNL Adobe Commerce on Cloud], le package de `ece-tools` génère la configuration de `app/etc/env.php` résultante pendant le déploiement en fonction de la configuration de la variable de déploiement dans `.magento.env.yaml`. Vous ne modifiez pas le fichier `env.php`.  Voir [Bonnes pratiques pour la configuration des services Valkey et Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) et [Déployer des variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy).

L’application Commerce utilise un cache de bas niveau frontal et principal pour permettre l’accès au stockage du cache. Commerce prend en charge plusieurs stratégies et back-ends de mise en cache, chacun adapté à différents cas d’utilisation. Cette page décrit les serveurs principaux disponibles et leurs différences.

>[!NOTE]
>
>[Vernis](config-varnish-install.md) gère la mise en cache complète des pages au niveau HTTP pour les déploiements sur site. Le [service Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) s’en charge pour les déploiements dans le cloud. Aucune solution n’utilise le serveur principal de cache de bas niveau.

## Options de cache du serveur principal

Le tableau suivant résume les caches principaux disponibles :

| Serveur principal | Description | Guide de configuration |
| ------- | ----------- | ------------------- |
| Système de fichiers | Valeur par défaut. Stocke les données de cache dans des fichiers sous `var/cache/`. Aucune configuration requise. | S.O. |
| Redis | Magasin de données en mémoire pour une mise en cache hautes performances. | [Utiliser Redis pour le cache par défaut](redis-pg-cache.md) |
| Valkey | Alternative open source compatible avec Redis. | [Utiliser Valkey pour le cache par défaut](valkey-pg-cache.md) |
| Base de données | Moteur de cache personnalisé soutenu par une base de données | [Création de moteurs de cache personnalisés](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} (documentation Adobe Developer) |

>[!IMPORTANT]
>
>Le cache Redis n’est pas pris en charge pour Adobe Commerce 2.4.9 ou pour les versions de correctif ultérieures à 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 et 2.4.8-p4. Si vous effectuez une mise à niveau vers l’une de ces versions, configurez Valkey et mettez à jour la configuration du cache pour l’utiliser. Pour [!DNL Adobe Commerce on-premises] d’informations, voir [ Configuration de Valkey ](config-valkey.md).

## Implémentations principales et L2 du cache {#implementation-approaches}

Commerce prend en charge les serveurs principaux de cache direct et la mise en cache L2. Un serveur principal direct sélectionne le stockage en cache. La mise en cache L2 ajoute une couche de cache locale devant le stockage distant.

### Serveurs principaux de cache direct

Les exemples PHP suivants configurent le serveur principal du cache dans `<Commerce-install-dir>/app/etc/env.php`. Ils n’activent pas la mise en cache L2.

| Version de Commerce | Mise en œuvre | Serveur principal | Valeur de configuration |
| ---------------- | -------------- | ------- | ------------------- |
| 2.4.8 et versions antérieures, si pris en charge | Hérité | Système de fichiers (par défaut) | Aucune configuration requise |
| 2.4.8 et versions antérieures, si pris en charge | Hérité | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 et versions antérieures, si pris en charge | Hérité | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 et versions ultérieures, et rétroportages pris en charge | Cache Symfony Moderne | Système de fichiers (par défaut) | `file` |
| 2.4.9 et versions ultérieures, et rétroportages pris en charge | Cache Symfony Moderne | Valkey | `valkey` |

Pour obtenir une prise en charge exacte des correctifs, consultez la [Configuration requise](../../installation/system-requirements.md).

>[!NOTE]
>
>La mise en œuvre moderne accepte le nom du type de `redis`, mais Redis n’est pas un service de cache officiellement pris en charge où Valkey est requis. Utilisez `valkey` à la place.

#### Exemples de serveur principal basés sur Zend hérités

Pour les déploiements sur site, les exemples suivants configurent les serveurs principaux de cache direct dans `<Commerce-install-dir>/app/etc/env.php`. Ils n’activent pas la mise en cache L2. N’utilisez pas ces exemples pour les déploiements [!DNL Adobe Commerce on Cloud], qui utilisent le package `ece-tools` pour générer la configuration de `app/etc/env.php` résultante pendant le déploiement.

>[!BEGINTABS]

>[!TAB Redis hérité du serveur principal]

Utilisez le nom de classe Redis complet uniquement sur les versions où Redis est pris en charge :

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Valkey principal hérité]

Utilisez le nom de classe Valkey complet sur les versions qui prennent en charge l’ancien serveur principal Valkey :

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

#### Serveur principal du cache Symphony moderne

Le serveur principal direct par défaut est le système de fichiers. Pour utiliser Valkey avec l’implémentation moderne, utilisez le type de serveur principal `valkey` simplifié.

L’exemple de configuration suivant est correct pour Adobe Commerce 2.4.9 et les versions ultérieures, ainsi que pour les rétroports pris en charge où Valkey est pris en charge, lors de la configuration de la mise en cache directe par défaut avec l’implémentation moderne de Symfony Cache.

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TIP]
>
>L’implémentation de Symfony Cache prend en charge des fonctionnalités de performances facultatives telles que la sérialisation binaire, la compression, les scripts Lua et les connexions persistantes. Pour plus d’informations, consultez [Configuration de Valkey pour le cache de page et par défaut](valkey-pg-cache.md).

### Implémentations du cache L2

La mise en cache L2 (à deux niveaux) ajoute une couche de cache locale sur chaque nœud web devant le stockage de cache distant partagé, réduisant ainsi le trafic réseau entre Commerce et le cache distant.

| Version de Commerce | Implémentation L2 | Serveur principal distant |
| ---------------- | ------------------ | --------------- |
| Antérieur à la version 2.4.9, si pris en charge | RemoteSynchronizedCache | Redis ou Valkey, selon la version de Commerce et la matrice de prise en charge au niveau du correctif |
| 2.4.9 et versions ultérieures | symfony_l2 | Valkey |

Pour la configuration locale, voir Configuration du cache L2 [L2](level-two-cache.md).

Pour les projets cloud, configurez la mise en cache L2 par le biais des variables de déploiement décrites dans [Déployer les variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}.

#### Configuration du cache L2

- Pour **[!DNL Adobe Commerce on-premises]** d’informations sur la configuration, voir Configuration du cache [L2](level-two-cache.md).

- Par **[!DNL Adobe Commerce on Cloud]**, configurez la mise en cache L2 par le biais de la variable de déploiement appropriée plutôt que de modifier `app/etc/env.php` directement. Voir [Déployer les variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"} dans la documentation _Adobe Commerce sur le cloud_.
