---
title: Outils Platform
description: Choisissez les outils de plateforme recommandés pour votre mise en oeuvre Adobe Commerce.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Outils Platform

Il ne manque pas d’aspects qui doivent être soigneusement étudiés et rigoureusement testés pour qu’un site de commerce électronique fonctionne sans interférence. Vous devez non seulement identifier les solutions appropriées pour aborder tous les aspects du site, depuis le stockage des données et la programmation jusqu’à la mise en cache et la sécurité, mais vous avez également besoin d’un processus approprié pour assurer la diffusion d’une plateforme qui s’exécute correctement et qui peut être créée et optimisée efficacement.

Cette section présente non seulement les outils, les solutions, les processus et les méthodologies qui ont été testés et perfectionnés sur un certain nombre d’implémentations d’Adobe Commerce, mais également nos recommandations pour les solutions qui répondent le mieux aux besoins et aux objectifs spécifiques de l’entreprise.

Le tableau suivant comprend des solutions que nous recommandons et que vous pouvez utiliser dans Adobe Commerce pour améliorer les performances de la plateforme :

| Objectif | Outil |
|------------------------------------------|-------------------------|
| Base | MySQL, MariaDB, Percona |
| Langage de programmation | PHP, JS, HTML, LESS CSS |
| Environnement de développement intégré (IDE) | Eclipse, PHPStorm |
| Serveur web | Nginx, Apache |
| Mise en cache des services | Redis, Varnish |
| Services de recherche | Elasticsearch |
| Services de la file d’attente des messages | [!DNL RabbitMQ] |
| Outil d&#39;analyse de sécurité | SonarQube, ZAP |

## Base

Nous utilisons trois outils différents en fonction des besoins de la marque. MySQL est une excellente solution de base de données comme la base de données Adobe Commerce si vous ne vous attendez pas à ce que votre boutique traite des charges extrêmes.

MariaDB est davantage centrée sur la communauté et fonctionne mieux pour les utilisateurs qui se soucient plus des fonctionnalités que des performances pures. MariaDB prend en charge un large éventail de moteurs de base de données, de cryptage de disque, d’interconnectivité horizontale complexe et de fonctionnalités de mise à l’échelle, ce qui peut être intéressant pour les grands magasins Adobe Commerce.

Percona est un branchement de MySQL centré sur les performances et la gestion de charge maximale. Choisissez MariaDB si vous avez besoin de plus de qualité de vie et de fonctionnalités DevOps. Allez sur Percona si votre objectif est d’obtenir des performances de charge élevée dans les jeux de données à grande échelle.

## Langage de programmation

Adobe Commerce est une application basée sur PHP et les nouvelles versions sont toujours compatibles avec la dernière version stable de PHP (par exemple, Adobe Commerce version 2.4 recommande d’utiliser PHP 7.4). Pour accroître la sécurité et les performances, vous devez tenir compte de plusieurs facteurs lors de la configuration de PHP afin d’obtenir une vitesse et une efficacité optimales lors du traitement des demandes. Le storefront web Adobe Commerce est créé avec HTML, JavaScript et le préprocesseur CSS LESS.

## Serveurs web

Adobe Commerce prend entièrement en charge les serveurs web Nginx et Apache. Adobe Commerce fournit des exemples de fichiers de configuration recommandés pour les deux :

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

L’exemple Nginx contient des paramètres pour de meilleures performances et est conçu de sorte qu’une petite reconfiguration soit requise.

## Mise en cache des services

Adobe Commerce propose de nombreuses options pour stocker vos données de cache et de session, notamment Redis, Memcache, filessystem et database. Pour une configuration avec plusieurs noeuds web, Redis est la meilleure option.

Nous vous recommandons vivement d’utiliser Varnish comme serveur de cache de page entière pour votre magasin. Adobe Commerce distribue un exemple de fichier de configuration pour le vernis qui contient tous les paramètres recommandés pour les performances.

## Services de recherche

Pour Adobe Commerce version 2.4 et ultérieure, toutes les installations doivent être configurées pour utiliser Elasticsearch ou OpenSearch en tant que solution de recherche de catalogue. Elasticsearch fournit des recherches rapides et avancées sur les produits du catalogue. Elasticsearch est facultatif pour les versions antérieures à la version 2.4, mais il est recommandé.

## Services de la file d’attente des messages

Les files d’attente de message fournissent un mécanisme de communication asynchrone dans lequel l’expéditeur et le destinataire d’un message ne se contactent pas. [!DNL RabbitMQ] est un courtier de messages open source qui offre un système de messagerie fiable, hautement disponible, évolutif et portable.

## Outils de sécurité

L’ [ outil d’analyse de sécurité Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html) vous permet de surveiller régulièrement vos sites web de magasin et de recevoir des mises à jour concernant les risques de sécurité connus, les logiciels malveillants et les logiciels obsolètes. En règle générale, vous commencez à utiliser cet outil lorsque vous commencez les tests d’acceptation par l’utilisateur (UAT). Outre l’outil d’analyse de sécurité d’Adobe Commerce, qui est gratuit et disponible pour toutes les mises en oeuvre et versions d’Adobe Commerce, d’autres options peuvent être utilisées pendant le processus CI/CD et avant chaque mise à jour.

SonarQube est une plateforme de gestion de la qualité Open Source, conçue pour analyser et mesurer la qualité technique de votre code. SonarQube fournit non seulement un rapport complet des bogues de code, des erreurs de syntaxe et des vulnérabilités, mais il fournit également des suggestions et des exemples pour résoudre votre code. SonarQube est idéal à utiliser dans un environnement CI/CD en tant qu’outil capable d’analyser le code avant son déploiement.

Zed Attack Proxy (ZAP) est un outil de test de sécurité gratuit utilisé par des milliers de testeurs de stylo dans le monde entier. ZAP est développé par OWASP et est l’un des outils les plus utilisés pour les tests de sécurité manuels.
