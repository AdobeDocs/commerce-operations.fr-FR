---
title: Options d’intégration Adobe Commerce
description: Explorez vos options d’intégration d’autres systèmes à votre mise en oeuvre Adobe Commerce.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Points d’intégration standard et flux de données

Il existe deux approches principales aux intégrations et aux flux de données, qui sont très similaires, mais qui ont une différence clé.

## Monolithique

Le diagramme suivant décrit une approche monolithique qui utilise Adobe Commerce comme système principal et application storefront :

![Diagramme de monolithe Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Headless

Le diagramme suivant décrit une approche sans tête qui utilise Adobe Commerce comme système principal intégré à une application DXP/CMS/personnalisée en tant qu’application storefront :

![Diagramme Adobe Commerce sans interface](../../assets/playbooks/integration-headless.svg)

La seule différence entre l’approche monolithique et l’approche sans tête est l’intégration du storefront, qui a un impact sur l’expérience utilisateur pour les clients. Monolithic utilise le storefront d’Adobe Commerce directement pour s’intégrer à des services tiers, tandis que le headless dépend de son propre storefront pour personnaliser et intégrer les mêmes services. Certains services tels que le paiement et l’authentification unique (SSO) nécessitent une personnalisation de storefront et Adobe Commerce pour finaliser le flux d’intégration.

## Systèmes tiers

Certains services populaires disposent déjà de super extensions pour prendre en charge Adobe Commerce ou les solutions de storefront populaires, telles que PWA Studio, Adobe Experience Manager et Vue Storefront, qui peuvent être trouvées sur leur marketplace d’extension ou à partir de sites web tiers associés. Même s’il n’existe aucune extension, les efforts pour mettre en oeuvre l’intégration entre Adobe Commerce et d’autres storefronts sans interface sont similaires. Tous les services tiers ont généralement des documents expliquant comment s’intégrer avec eux. Ces services ne sont que quelques exemples ; différents pays et marchés peuvent avoir des choix différents.

## Intégrations d’entreprise

Pour les intégrations de systèmes d’entreprise, généralement appelées intégrations d’arrière-plan, il y a un impact sur le flux de données d’entreprise. En fonction de différents types d’entreprise et besoins, il peut utiliser trois options d’intégration différentes, que nous avons déjà introduites.

Les données obligatoires sur les produits, telles que les SKU, les stocks et les prix de base, proviennent généralement des ERP, tandis que les prix de vente sont généralement gérés par chaque canal de vente (par exemple, Adobe Commerce) ou CPQ (B2B ou ventes privées). Comme les données obligatoires du produit (sauf le stock) ne changent pas très souvent, la bonne pratique consiste à utiliser des mises à jour par lots planifiées via l’API REST ou l’importation de fichiers en vrac. Pour l’inventaire, la bonne pratique consiste à disposer d’une mise à jour complète quotidienne de l’inventaire des produits qui est partagée avec différents canaux de vente afin d’éviter les ventes excessives. En outre, apportez des modifications incrémentielles par rapport à votre ERP planifié dans les 24 heures.

Le catalogue de produits, les métadonnées et le contenu marketing peuvent être gérés séparément par chaque canal de vente (par exemple, Adobe Commerce) ou par un PIM central. Comme les métadonnées ne sont pas modifiées fréquemment, il est recommandé d’utiliser les mises à jour par lots planifiées via l’API REST ou l’importation de fichiers en vrac.

Les données de commande comprennent les données de commande, de devis (B2B), d’expédition, de retour et d’échange qui sont généralement gérées à partir d’un système OMS et WMS centralisé. Les données de commande doivent être synchronisées dès que possible. L’API REST est donc généralement la meilleure option. Pour de meilleures performances, envisagez de réduire le nombre d’appels API. Pour connaître l’état de la commande, les envois, le retour et les données d’échange, pensez à planifier les API de mise à jour de lots REST en heures ou en minutes.

Les données B2B sont généralement gérées à partir d’un CRM centralisé. Une API en temps réel est utilisée pour vérifier les clients existants et créer de nouveaux clients. Pour B2B, il peut s’avérer nécessaire d’introduire plus d’API pour synchroniser différents employés, groupes et listes de prix de l’entreprise entre Adobe Commerce et votre CRM ou CPQ.

Il existe d’autres intégrations système, telles que eDM pour le marketing par e-mail et Business Intelligence pour l’analyse des données d’entreprise, qui sont généralement effectuées par le biais de l’API REST ou de l’exportation/importation de fichiers, généralement prises en charge par les extensions existantes.
