---
title: Stratégie d’intégration Adobe Commerce
description: Consultez les stratégies et options d’intégration pour votre mise en oeuvre Adobe Commerce.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Stratégie d’intégration Adobe Commerce

La possibilité d’intégrer votre plateforme est &quot;non négociable&quot;. Les entreprises veulent que leurs plateformes de commerce électronique soient accessibles à partir de divers points de contact et intégrées de manière transparente à leurs systèmes technologiques, en particulier à leurs PGI. La personnalisation, l’évolutivité globale et l’abordabilité jouent également un rôle dans l’achat final de la plateforme.

Une approche d’intégration globale pour les systèmes front-end et back-end est prise en charge par les API GraphQL performantes, les API REST complètes et l’importation de fichiers par lots entre Adobe Commerce et d’autres systèmes ou services.

L’API GraphQL d’Adobe Commerce offre une couverture de storefront complète que vous pouvez utiliser pour intégrer à d’autres storefronts, notamment :

- Plateformes d’expérience numérique (DXP) comme Adobe Experience Manager et Bloomreach
- Systèmes de gestion de contenu (CMS) tels que Drupal et WordPress
- Application storefront personnalisée moderne telle qu’Adobe Commerce, PWA Studio et Vue Storefront

GraphQL fournit une réponse efficace et spécifique au canal, sans récupération excessive des données et un déploiement agile des nouvelles fonctionnalités de point de contact. Il est également souvent choisi pour s’intégrer aux canaux de vente tels que les applications mobiles natives, POS, IoT, les canaux sociaux et les canaux de commerce en direct tels que Facebook, Google, Instagram, WeChat et TikTok.

L’API REST Adobe Commerce fournit une couverture de configuration système complète et des fonctionnalités de gestion des données, y compris les produits et le catalogue. panier, guillemet et passage en caisse ; les clients, les comptes et les entreprises; et commandes et retours. Les API REST prennent en charge les opérations en bloc, les modes d’authentification multiples et l’autorisation granulaire. Les API REST sont donc souvent choisies pour s’intégrer aux systèmes d’entreprise, notamment :

- Systèmes de planification des ressources de l’entreprise (ERP) tels que SAP
- Systèmes de gestion de l’information sur les produits (PIM) tels qu’Akeneo
- Systèmes de gestion de la relation client (CRM) tels que Salesforce
- Systèmes de gestion des commandes (OMS) tels que MOM, Manhattan et SAP
- Warehouse Management System (WMS) ou une logistique tierce (3PL) telle qu’Oracle, NetSuite et SAP WM
- Configurer, prix, devis (CPQ) comme SalesforceCPQ
- Gestion des actifs numériques (DAM) comme la gestion des actifs numériques d’Adobe.

Les importations de fichiers par lots sont également considérées comme une bonne option pour intégrer des systèmes d’entreprise tels que les ERP et les PIM, car ces données ne changent pas très souvent et vous obtenez souvent de meilleures performances avec les importations de fichiers planifiées. Par conséquent, les importations de fichiers par lot sont généralement sélectionnées pour la synchronisation de données en bloc, quotidienne/hebdomadaire et les synchronisations de données complètes mensuelles, tandis que les API REST sont sélectionnées pour la synchronisation incrémentale des changements de données, afin de meilleures performances. Cette opération est également considérée comme une tâche planifiée, mais peut être effectuée fréquemment (potentiellement toutes les 15 minutes à 1 heure), selon les besoins de l’entreprise.

## Options d’intégration

Adobe Commerce propose trois options d’intégration flexibles :

- Intégration directe système à système avec des connecteurs préconfigurés. Certains systèmes peuvent déjà avoir des extensions Adobe Commerce sur Adobe Commerce Marketplace ou sur leur propre site web.

- Intégration système à système par le biais d’un middleware personnalisé. La solution middleware personnalisée déployée sera utilisée pour le mappage, la traduction et la gestion des données de processus.

- Intégration système à système via iPaaS (Integration Platform-as-a-Service), également appelée EAI (Enterprise Application Integration Platform), comme Mulesoft, Boomi et Software AG.

![Options d’intégration Adobe Commerce](../../assets/playbooks/integration-options.svg)

Bien que les intégrations en temps réel soient généralement souhaitées, elles ne sont pas nécessaires pour certains scénarios. Adobe Commerce prend en charge de manière native [!DNL RabbitMQ] comme le bus de messages pour activer les processus asynchrones, ce qui est recommandé pour certaines données qui ne sont pas nécessaires à l’échange en temps réel, mais plutôt pour une mise à jour avec l’échange de fichiers par lots ou l’API de traitement de données par lots REST pour un traitement asynchrone.
