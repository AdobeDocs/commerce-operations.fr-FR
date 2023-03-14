---
title: Technologies de l’infrastructure cloud
description: Observez de plus près la collection de technologies que nous utilisons pour Adobe Commerce sur l’infrastructure cloud.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Technologies

Comme nous l’avons mentionné, Adobe Commerce utilise plusieurs solutions logicielles pour prendre en charge la plateforme. Plus précisément, en ce qui concerne la production, nous avons ventilé certaines des solutions et fonctionnalités techniques incluses dans Adobe Commerce sur l’infrastructure cloud qui permettent de tirer le meilleur parti de votre environnement de production.

![Diagramme présentant Adobe Commerce sur la technologie de l’infrastructure cloud](../../../assets/playbooks/infrastructure-technology.svg)

## Solutions logicielles

- **Nginx**—Serveur web utilisant PHP-FPM. Il existe une instance avec plusieurs programmes de travail.

- **GlusterFS**—Serveur de fichiers pour la gestion de tous les déploiements de fichiers statiques et la synchronisation avec quatre montages de répertoires :
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**— Un serveur par VM avec une seule principale et les deux autres comme répliques.

- **Elasticsearch**: recherchez Adobe Commerce version 2.2.x et ultérieure.

- **OpenSearch**: recherchez Adobe Commerce version 2.4.6 et ultérieure.

- **Galera**: grappe de base de données avec une base de données MariaDB MySQL par noeud avec un paramètre d’incrémentation automatique de trois pour les identifiants uniques de chaque base de données.

## Fonctionnalités et avantages

- Avec trois instances dédiées dans un VPC, il existe un équilibreur de charge élastique dans trois zones de disponibilité ou centres de données distincts.

- Une résilience plus élevée est fournie par rapport aux événements qui peuvent entraîner l’échec d’une instance unique. Par exemple, une panne d’une zone de disponibilité AWS entière ou d’un centre de données.

- La mise à l’échelle zéro temps d’arrêt sur l’ensemble de la pile, y compris le web, la mise en cache, la recherche et la base de données, en moins de 15 minutes.
