---
title: Diffuser Des Expériences À L’Échelle
description: Découvrez comment diffuser des expériences à grande échelle avec Adobe Commerce et Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Diffuser des expériences à grande échelle avec Adobe Commerce, Commerce Integration Framework et Adobe Experience Manager

Un modèle d’intégration recommandé entre AEM et Adobe Commerce en utilisant CIF comme connecteur est que AEM possède la couche de présentation (la &quot;vitre&quot;) et Adobe Commerce pour alimenter le serveur principal Commerce en tant que serveur principal &quot;sans tête&quot;. Cette approche de l’intégration tire parti des avantages de chaque application : les capacités de création, de personnalisation et d’omnicanal des AEM et des opérations de commerce électronique d’Adobe Commerce.

Dans un environnement AEM/CIF/Adobe Commerce, les visiteurs du site de commerce électronique arriveront initialement à AEM. AEM vérifie si la page demandée est disponible dans son cache de Dispatcher. Si la page existe, cette page mise en cache est diffusée au visiteur et aucun autre traitement n’est requis. Si le Dispatcher ne contient pas la page demandée, ou si elle a expiré, il demande à l’éditeur AEM de créer la page, l’éditeur appelant Adobe Commerce pour les données de commerce électronique afin de créer la page, si nécessaire. La page créée est ensuite transmise au Dispatcher pour être diffusée au visiteur, puis mise en cache afin d’éviter que d’autres chargements ne soient placés sur les serveurs lors des demandes ultérieures à la même page de la part d’autres visiteurs.

![Diagramme de présentation de l’architecture d’Adobe Experience Manager et Adobe Commerce](../assets/commerce-at-scale/overview.png)

Une combinaison de rendu côté serveur et de rendu côté client peut être utilisée dans le modèle AEM/CIF/Adobe Commerce : rendu côté serveur pour diffuser du contenu statique et du rendu côté client afin de diffuser du contenu dynamique personnel ou changeant fréquemment, en appelant directement Adobe Commerce pour des composants spécifiques depuis le navigateur de l’utilisateur.

Vous trouverez un exemple des différents composants dans une page Détails du produit sur un exemple AEM storefront eCommerce dans l’exemple ci-dessous :

![Diagramme de présentation de l’architecture d’Adobe Experience Manager et Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Rendu côté serveur

Il est peu probable que les pages d’e-commerce telles que les pages de détails des produits (PDP) et les pages de liste de produits (PLP) changent fréquemment et conviennent pour être entièrement mises en cache après le rendu côté serveur à l’aide des composants principaux CIF AEM. Les pages doivent être rendues sur l’éditeur AEM à l’aide de modèles génériques créés dans AEM. Ces composants obtiennent des données d’Adobe Commerce via les API GraphQL. Ces pages sont créées dynamiquement, rendues sur le serveur, mises en cache dans le Dispatcher d’AEM, puis diffusées au navigateur. Les exemples de ce type sont présentés dans les zones violettes de l’exemple ci-dessus.

## Rendu côté client

Lorsque des attributs plus dynamiques tels que les niveaux/disponibilité ou le prix sont affichés, par exemple sur les pages Détails du produit (PDP), des composants côté client peuvent être utilisés. Bien que la page de modèle puisse être créée et mise en cache sur le Dispatcher à l’aide de l’approche de rendu côté serveur ci-dessus, il peut exister, dans la page statique elle-même, des composants web côté client dynamiques. Ces composants dynamiques peuvent récupérer des données directement dans le navigateur du client à partir d’Adobe Commerce via les API GraphQL pour vérifier, par exemple, le prix actuel ou le niveau de stock en temps réel sur le PDP. Cela garantit que le contenu généralement essentiel à afficher en temps réel est toujours récupéré au chargement de la page. Des exemples de ce type de comportement sont présentés dans les zones rouges de l’exemple ci-dessus.

Une combinaison de modèles d’AEM et de rendu côté client peut également être utilisée pendant le processus de passage en caisse : les composants du panier côté client rendent le panier, le formulaire de passage en caisse et l’intégration au fournisseur de services de paiement. Cette approche hybride peut également être utilisée pour les fonctionnalités de gestion de compte d’Adobe Commerce, telles que la création d’un compte, la connexion à un compte et l’oubli du mot de passe.
