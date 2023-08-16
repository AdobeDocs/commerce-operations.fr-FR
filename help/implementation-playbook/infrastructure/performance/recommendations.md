---
title: Recommendations d’optimisation des performances
description: Optimisez les performances de votre implémentation Adobe Commerce en suivant ces recommandations.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Examen de l’optimisation des performances

Même si l’optimisation des performances peut provenir de nombreux aspects, certaines recommandations générales doivent être prises en compte pour la plupart des scénarios. Cela inclut l’optimisation de la configuration pour les éléments d’infrastructure, la configuration du serveur principal Adobe Commerce et la planification de l’évolutivité de l’architecture.

## Infrastructure

Les sections suivantes décrivent les recommandations d’optimisation de l’infrastructure.

### Recherches DNS

La recherche DNS est le processus de recherche de l’adresse IP à laquelle appartient le nom de domaine. Le navigateur doit attendre que la recherche DNS soit terminée pour pouvoir télécharger n’importe quoi pour chaque requête. La réduction des recherches DNS est importante pour améliorer les temps de chargement généraux des pages.

### Réseau de diffusion de contenu (CDN)

Utilisez un CDN pour optimiser les performances de téléchargement des ressources. Adobe Commerce utilise Fastly. Si vous disposez d’une mise en oeuvre sur site d’Adobe Commerce, vous devez également envisager d’ajouter un calque CDN.

### Latence web

L’emplacement du centre de données affecte la latence web des utilisateurs frontaux.

### Bande passante réseau

Une bande passante réseau suffisante est l’une des principales exigences pour l’échange de données entre les noeuds web, les bases de données, les serveurs de mise en cache/session et d’autres services.

Comme Adobe Commerce exploite efficacement la mise en cache pour des performances élevées, votre système peut échanger activement des données avec des serveurs de mise en cache tels que Redis. Si Redis se trouve sur un serveur distant, vous devez fournir un canal réseau suffisant entre les noeuds web et le serveur de mise en cache pour éviter les goulets d’étranglement lors des opérations de lecture/écriture.

### Système d’exploitation

Les configurations et optimisations des systèmes d’exploitation sont similaires pour Adobe Commerce par rapport aux autres applications web à charge élevée. À mesure que le nombre de connexions simultanées gérées par le serveur augmente, le nombre de sockets disponibles peut être entièrement alloué.

### Unité centrale des noeuds web

Un noyau de processeur peut traiter entre 2 et 4 demandes Adobe Commerce sans mise en cache efficace. Pour déterminer le nombre de noeuds/coeurs web nécessaires au traitement de toutes les requêtes entrantes sans les mettre en file d’attente, utilisez l’équation :

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Paramètres PHP-FPM

L’optimisation de ces paramètres dépend des résultats des tests de performance pour différents projets.

- **ByteCode**: pour tirer le meilleur parti d’Adobe Commerce avec PHP 7, vous devez activer la fonction `opcache` et configurez-le correctement.

- **APCU**: nous vous recommandons d’activer l’extension APCu PHP et de configurer le compositeur afin d’optimiser les performances. Cette extension met en cache les emplacements de fichiers pour les fichiers ouverts, ce qui augmente les performances des appels au serveur Adobe Commerce, y compris les pages, les appels Ajax et les points de fin.

- **Realpath_cacheconfiguration**: optimisation `realpath_cache` permet aux processus PHP de mettre en cache les chemins d’accès aux fichiers au lieu de les rechercher chaque fois qu’une page est chargée.

### Serveur web

Seule une légère reconfiguration est nécessaire pour utiliser nginx en tant que serveur web. Le serveur web nginx offre de meilleures performances et est facile à configurer à l’aide de l’exemple de fichier de configuration d’Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configuration de PHP-FPM avec TCP correctement

- Activation de HTTP/2 et de Gzip

- Optimisation des connexions de travail

### Base

Ce document ne fournit pas d’instructions d’optimisation MySQL détaillées, car chaque magasin et environnement est différents, mais nous pouvons faire des recommandations générales.

La base de données Adobe Commerce (ainsi que toute autre base de données) est sensible à la quantité de mémoire disponible pour le stockage des données et des index. Pour utiliser efficacement l’indexation des données MySQL, la quantité de mémoire disponible doit être, au minimum, proche de la moitié de la taille des données stockées dans la base de données.

Optimisez les `innodb_buffer_pool_instances` pour éviter des problèmes liés à plusieurs threads tentant d’accéder à la même instance. La valeur de la variable `max_connections` doit correspondre au nombre total de threads PHP configurés dans le serveur d’applications. Utilisez la formule suivante pour calculer la meilleure valeur pour `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Mise en cache de session

La mise en cache de session est un bon candidat à configurer pour une instance distincte de Redis. La configuration de la mémoire pour ce type de cache doit tenir compte de la stratégie d’abandon de panier du site et de la durée pendant laquelle une session doit rester dans le cache.

La mémoire des redis doit être suffisante pour contenir tous les autres caches en mémoire pour des performances optimales. Le cache des blocs sera le facteur clé pour déterminer la quantité de mémoire à configurer. Le cache des blocs augmente par rapport au nombre de pages sur un site (nombre de SKU x nombre de vues de magasin).

### Mise en cache des pages

Il est vivement recommandé d’utiliser le vernis pour le cache de page complet sur votre boutique Adobe Commerce. La variable `PageCache` est toujours présent dans le code base, mais il doit être utilisé à des fins de développement uniquement.

Installez Varnish sur un serveur distinct devant le niveau web. Il doit accepter toutes les requêtes entrantes et fournir des copies de page mises en cache. Pour permettre à Varnish de fonctionner efficacement avec les pages sécurisées, un proxy de terminaison SSL peut être placé devant Varnish. Nginx peut être utilisé à cet effet.

Bien que l’invalidation de la mémoire cache de la page entière de vernis soit efficace, nous vous recommandons d’allouer suffisamment de mémoire à Varnish pour contenir vos pages les plus populaires en mémoire.

### Files d&#39;attente des messages

Le Message Queue Framework (MQF) est un système qui permet à un module de publier des messages dans les files d’attente. Il définit également les consommateurs qui reçoivent les messages de manière asynchrone. Adobe Commerce prend en charge [!DNL RabbitMQ] en tant que courtier de messagerie, qui fournit une plateforme évolutive pour l’envoi et la réception de messages.

### Test et surveillance des performances

Il est toujours recommandé d’effectuer des tests de performance avant chaque version de production afin d’obtenir une estimation des fonctionnalités de votre plateforme de commerce électronique. Effectuez une surveillance après le lancement et disposez d’un plan d’évolutivité et de sauvegarde pour gérer les heures de pointe.

>[!NOTE]
>
> Adobe Commerce sur l’infrastructure cloud applique déjà toutes les optimisations d’infrastructure et d’architecture ci-dessus, à l’exception de la recherche DNS, car elle n’est pas étendue.

### Rechercher {#search-heading}

Elasticsearch (ou OpenSearch) est requis à compter de la version 2.4 d’Adobe Commerce, mais il est également recommandé de l’activer pour les versions antérieures à la version 2.4.

## Modèles d’exploitation

Outre les recommandations d’optimisation de l’infrastructure commune mentionnées précédemment, il existe également des approches pour améliorer les performances pour des modes et des échelles d’entreprise spécifiques. Ce document ne fournit pas d’instructions de réglage approfondies pour tous les scénarios, car ceux-ci sont différents, mais nous pouvons vous fournir quelques options de haut niveau pour votre référence.

### Architecture sans affichage

Nous avons une section distincte dédiée à détailler ce qui [headless](../../architecture/headless/adobe-commerce.md) est et différentes options. En résumé, il sépare la couche de storefront de la plate-forme elle-même. Il s’agit toujours du même serveur principal, mais Adobe Commerce ne traite plus directement les requêtes et ne prend en charge que les storefronts personnalisés via l’API GraphQL.

### Conserver Adobe Commerce mise à jour

Adobe Commerce offre toujours de meilleures performances lors de l’exécution de la dernière version. Même s’il n’est pas possible de maintenir Adobe Commerce à jour après chaque nouvelle version, il est toujours recommandé de [upgrade](../../../upgrade/overview.md) lorsqu’Adobe Commerce introduit des optimisations de performances significatives.

Par exemple, en 2020, Adobe a publié une optimisation de la couche Redis, corrigeant de nombreuses inefficacités, problèmes de connexion et transferts inutiles de données entre Redis et Adobe Commerce. Les performances globales entre la version 2.3 et la version 2.4 sont nuit et jour et nous avons constaté des améliorations significatives dans le panier, le passage en caisse et les utilisateurs simultanés, simplement en raison de l’optimisation de Redis.

### Optimiser le modèle de données

De nombreux problèmes proviennent des données, notamment des modèles de données incorrects, des données qui ne sont pas correctement structurées et des données qui manquent d’un index.

Il semble correct que vous testiez quelques connexions, mais que vous voyiez en production lorsque le trafic réel atteint et c&#39;est là que la lenteur entre en jeu. Il est très important que les intégrateurs de systèmes sachent comment concevoir un modèle de données (en particulier pour les attributs de produit), éviter d’ajouter des attributs inutiles et conserver les attributs obligatoires qui affectent la logique commerciale (comme la tarification, la disponibilité des stocks et la recherche).

Pour les attributs qui n’affectent pas la logique commerciale mais qui doivent toujours être présents sur le storefront, combinez-les en quelques attributs (par exemple, le format JSON).

Pour optimiser les performances de la plateforme, si aucune logique commerciale n’est requise sur le storefront à partir de données ou d’attributs provenant d’un PIM ou d’un ERP, il n’est pas nécessaire d’ajouter cet attribut dans Adobe Commerce.

### Conception pour l’évolutivité

Ceci est important pour les entreprises qui exécutent des campagnes et qui font souvent face à des heures de pointe. Pour que la conception de l’architecture et de l’application soit facile à mettre à l’échelle, cela peut augmenter les ressources en période de pointe et les réduire ensuite.
