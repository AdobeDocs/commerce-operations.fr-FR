---
title: Présentation de la mise en cache et options de configuration
description: Découvrez la mise en cache dans Adobe Commerce, notamment le stockage principal, la configuration frontale et la mise en cache de pages complètes avec les caches Varnish, Redis, Valkey et L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: dbc1f6d0edff87130604d4762477ee5892a7aafc
workflow-type: tm+mt
source-wordcount: 589
ht-degree: 0%

---

# Présentation de la mise en cache et options de configuration

Adobe Commerce repose sur une architecture de mise en cache à plusieurs couches pour réduire la charge de la base de données, minimiser le traitement redondant et accélérer la diffusion des pages. Au niveau de l’application, Commerce gère plus d’une douzaine [types de cache](../cli/manage-cache.md#clean-and-flush-cache-types) tels que la configuration, la disposition, le blocage d’HTML et les collections, que vous pouvez acheminer vers un serveur principal de stockage dédié tel que [Redis](config-redis.md) ou [Valkey](config-valkey.md). Pour la mise en cache de toutes les pages dans les déploiements sur site, Adobe recommande vivement d’utiliser [Varnish](config-varnish.md). Commerce sur les déploiements cloud utilisent Fastly. D’autres couches, telles que la mise en cache L2 [ et la signature de contenu statique [](static-content-signing.md) L2](level-two-cache.md) améliorent encore les performances pour les déploiements à trafic élevé et à plusieurs nœuds.

Ce guide explique le fonctionnement de chaque couche de mise en cache et vous explique comment configurer les options frontales, principales et avancées en fonction de vos exigences de déploiement.

## Mise en cache des fronts

Un cache frontal est une interface entre Commerce et le serveur principal de stockage du cache. Vous pouvez définir plusieurs fronts, chacun avec des paramètres de serveur principal différents, puis attribuer des [types de cache](../cli/manage-cache.md#clean-and-flush-cache-types) spécifiques à chaque front-end.  Pour plus d’informations sur la configuration, voir [Configuration des fronts de cache](cache-types.md).

## Mise en cache des serveurs principaux

Un serveur principal de cache est le mécanisme de stockage sous-jacent pour les données mises en cache. Commerce fournit un serveur principal de système de fichiers par défaut, mais vous pouvez configurer d’autres serveurs principaux tels que Redis ou Valkey pour améliorer les performances et l’évolutivité. Pour plus d’informations sur les options disponibles, voir [Mettre en cache les options du serveur principal](cache-options.md).

## Mise en cache de toutes les pages avec vernis

[Varnish Cache](config-varnish.md) est un accélérateur HTTP qui met en cache des pages complètes en mémoire. Pour les environnements de production sur site, Adobe recommande vivement Varnish, car il est beaucoup plus rapide que le cache de pleine page intégré. Commerce dans les environnements cloud utilise [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) pour la mise en cache de toutes les pages au lieu de Varnish.

>[!NOTE]
>
>Varnish fonctionne comme un proxy inverse devant votre serveur web et ne nécessite pas de modifications de la configuration du serveur principal de cache de Commerce.

## Mise en cache L2 (à deux niveaux)

[Cache L2](level-two-cache.md) stocke les données de cache localement sur chaque nœud web tout en utilisant un cache distant (Redis ou Valkey) comme source de vérité. Cela réduit le trafic réseau entre vos nœuds web et le cache distant, ce qui améliore les performances des sites à trafic élevé.

## Mise en cache de contenu statique

La [signature de contenu statique](static-content-signing.md) invalide le cache du navigateur pour les ressources statiques (CSS, JavaScript, images) en incorporant une version de déploiement dans les URL des fichiers.

## Terminologie de mise en cache

[!DNL Commerce] utilise la terminologie de mise en cache suivante :

- **Frontend** — Interface ou passerelle de stockage en cache, implémentée par [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Types de cache** — L&#39;un des types intégrés fournis avec [!DNL Commerce] (comme `config`, `layout`, `block_html`, `full_page`) ou un [type personnalisé](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Serveur principal** — Spécifie les détails du [stockage en cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), implémenté par [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend).
- **Serveur principal à deux niveaux** — Stocke les enregistrements de cache sur deux serveurs principaux : un cache local (rapide) et un cache distant (partagé). Voir la section Configuration du cache L2 ](level-two-cache.md).[

## Options de configuration

Pour le mappage front-end-à-type et la syntaxe de configuration du cache :

**On-premise** : la configuration du cache est stockée dans deux fichiers :

- `<magento_root>/app/etc/di.xml` — Configuration de l&#39;injection de dépendance globale. Modifiez ce fichier pour modifier le paramètre frontal de cache `default` fourni.
- `<magento_root>/app/etc/env.php` : configuration spécifique à un environnement. Modifiez ce fichier pour configurer les fronts de cache personnalisés. Ce fichier remplace la configuration équivalente dans `di.xml`.

Pour plus d’informations, voir :

- [Configurer les fronts du cache](cache-types.md) : associez un front-end du cache à des types de cache spécifiques.
- [Options du serveur principal de mise en cache](cache-options.md)—Référence des options du serveur principal

**Adobe Commerce sur le cloud** : configurez la mise en cache avec les `CACHE_CONFIGURATION` dans le `.magento.env.yaml`. Voir [Bonnes pratiques pour la configuration du service Redis et Valkey](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md).
