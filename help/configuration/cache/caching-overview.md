---
title: Présentation de la mise en cache et options de configuration
description: Découvrez la mise en cache dans Adobe Commerce, notamment le stockage principal, la configuration frontale et la mise en cache de pages complètes avec les caches Varnish, Redis, Valkey et L2.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
autotag-review: '2026-06-22T20:28:12.484Z'
TQID: 'https://experienceleague.adobe.com/oDoZ1o2IWXsDTo84XQygWZYVmfVHWbk-CuqaU47laU4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# Présentation de la mise en cache et options de configuration

Adobe Commerce utilise plusieurs couches de mise en cache pour réduire les traitements répétés, réduire la charge de la base de données et améliorer les temps de réponse. Ces couches fonctionnent à différents points de la requête et de la diffusion des ressources :

- **Mise en cache de l’application** stocke les données générées ou traitées à l’aide des types de cache Commerce.
- **mise en cache complète de pages HTTP** stocke les réponses HTTP complètes avant qu’elles n’atteignent l’application Commerce.
- **Mise en cache L2** peut ajouter un cache local sur chaque nœud web devant le stockage du cache distant partagé.
- **La mise en cache de contenu statique** permet aux navigateurs de réutiliser des ressources statiques telles que CSS, JavaScript et des images.

Cette page présente un aperçu conceptuel de ces couches et des liens vers leurs conseils de configuration. Pour connaître les choix du serveur principal, les détails d’implémentation et les paramètres spécifiques aux versions, consultez [Options du serveur principal de mise en cache et référence de stockage](cache-options.md).

## Mise en cache des calques

### Mise en cache de l’application

La mise en cache de l’application Commerce est organisée comme suit :

>[!BEGINSHADEBOX]

type de cache → cache frontal → principal du cache

>[!ENDSHADEBOX]

Un **type de cache** identifie le type de données mises en cache, comme la configuration, la mise en page, le bloc HTML ou le contenu pleine page. Un **cache frontal** connecte un ou plusieurs types de cache au stockage. Un **serveur principal du cache** fournit l’implémentation du stockage.

Vous pouvez affecter différents types de cache à différents fronts lorsque des paramètres de cache ou un stockage distincts sont requis. Pour plus d’informations sur la configuration, voir [Configuration des types et fronts de cache](cache-types.md).

### Mise en cache HTTP de toutes les pages

La mise en cache pleine page HTTP stocke les réponses complètes sur la couche HTTP ou CDN. Pour les déploiements en production :

- **Adobe Commerce On-premise**—Adobe recommande [Varnish](config-varnish.md) pour la mise en cache de toutes les pages. Varnish fonctionne comme un proxy inverse devant le serveur web.
- **Adobe Commerce sur l’infrastructure cloud** utilise [Fastly](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/cdn/fastly){target="_blank"} pour la couche de mise en cache Edge et full-page. L’infrastructure cloud n’utilise pas de service Varnish géré séparément.

>[!NOTE]
>
>La modification du serveur principal du cache de l’application Commerce ne configure pas Varnish ni Fastly. La mise en cache HTTP de toutes les pages est configurée et gérée séparément du cache d’application de bas niveau.

### Mise en cache L2

La mise en cache L2, ou à deux niveaux, ajoute un cache local sur chaque nœud web de Commerce tout en conservant le stockage de cache distant partagé. Les données fréquemment consultées peuvent être diffusées localement, ce qui réduit la communication avec le cache distant dans les déploiements multi-nœuds.

La configuration et les implémentations prises en charge de L2 varient selon la version et le type de déploiement de Commerce. Pour plus d’informations, consultez la configuration du cache L2 [&#128279;](level-two-cache.md).

### Mise en cache de contenu statique

Commerce peut améliorer la mise en cache des navigateurs pour les ressources statiques telles que les CSS, les JavaScript et les images en ajoutant une version de déploiement à leurs URL. Lorsque le contenu change, l’URL change, ce qui fait que le navigateur demande la nouvelle ressource au lieu d’utiliser une ancienne copie mise en cache.

## Configuration spécifique au déploiement

Les tâches de configuration suivantes varient selon le type de déploiement.

| Tâche | On-premise | Infrastructure cloud |
| --- | --- | --- |
| Serveurs principaux du cache d’applications | [Options de cache du serveur principal et référence de stockage](cache-options.md) | [Bonnes pratiques relatives à la configuration des services Valkey et Redis](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md) |
| Mise en cache pleine page HTTP | [Configurer le vernis](config-varnish.md) | [Présentation des services Fastly](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/cdn/fastly) |

Les tâches suivantes s’appliquent à tous les types de déploiement :

- **Configurez les types de cache et les fronts** [Configurez les fronts et les types de cache](cache-types.md) pour associer les types de cache aux fronts de cache.
- **Configurer la mise en cache L2** - [Configuration du cache L2](level-two-cache.md).
- **Configurer l’invalidation du cache du navigateur pour le contenu statique**—[Signature de contenu statique et invalidation du cache du navigateur](static-content-signing.md).
