---
title: Principes de développement des plateformes
description: Découvrez les principes fondamentaux du développement de plateformes lorsque vous utilisez Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Principes de développement de plates-formes

Dans ce manuel de lecture, nous approfondirons certaines des principales normes de développement d’Adobe Commerce, notamment :

- Portée fonctionnelle et technique conforme au processus de développement
- Bonnes pratiques de développement alignées sur l’architecture MVC
- Considérations architecturales, y compris la GRA
- Normes de sécurité contre les scripts et les exploits
- Bonnes pratiques relatives au développement d’extensions
- Intégrations des API web avec REST, SOAP et GraphQL
- Améliorations des performances du codage et de l’infrastructure
- Outils, stratégies et méthodologies de test

Bien que certains implémentateurs de solutions puissent avoir leurs propres préférences en ce qui concerne les méthodologies, les processus et les outils utilisés tout au long d’un projet de mise en oeuvre, ce manuel se concentre sur les bonnes pratiques et les méthodologies généralement acceptées, qui peuvent être partagées dans la majorité des implémentations.

Comme tout projet informatique volumineux, Adobe Commerce repose sur des normes de codage qui tirent parti des bonnes pratiques et des normes des technologies sous-jacentes (par exemple, PHP/Zend, Symfony, JavaScript, jQuery et HTML), ainsi que des normes établies dans Adobe Commerce Coding Standard. Le respect de ces normes est un impératif absolu pour éliminer les bogues et améliorer la qualité et la maintenabilité du code personnalisé.

## Adobe Commerce sur l’infrastructure cloud

Adobe Commerce sur l’infrastructure cloud est une plateforme d’hébergement automatisée et gérée pour le logiciel Adobe Commerce. Adobe Commerce sur l’infrastructure cloud s’accompagne d’une variété de fonctionnalités supplémentaires qui la distinguent des implémentations Adobe Commerce sur site et des implémentations de Magento Open Source :

![Infographie des composants Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce sur l’infrastructure cloud fournit une infrastructure préconfigurée qui inclut PHP, MySQL, Redis, [!DNL RabbitMQ]et les technologies Elasticsearch; un workflow basé sur Git avec des opérations de création et de déploiement automatiques pour un développement rapide et un déploiement continu efficaces chaque fois que des modifications de code sont transmises dans un environnement Platform as a Service (PaaS) ; des fichiers et des outils de configuration d’environnement hautement personnalisables ; et l’hébergement AWS qui offre un environnement évolutif et sécurisé pour les ventes en ligne et la vente au détail.

![Infographie des composants Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
