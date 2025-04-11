---
title: Versions de Beta
description: Découvrez les versions bêta d’Adobe Commerce et comment y participer.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: ea4f340540e57b282657a44502d80f1d5c409c6a
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# Versions bêta d’Adobe Commerce

Les programmes bêta d’Adobe Commerce permettent aux commerçants d’accéder aux fonctionnalités et au code de version préliminaire, de faire part de leurs commentaires et de guider l’avenir d’Adobe Commerce. Il existe deux types de programmes bêta :

- Beta publique : un programme bêta public est disponible pour tous les clients et partenaires d’Adobe Commerce
- Private Beta : pour participer à un programme Private Beta, une approbation basée sur des critères de qualification peut être nécessaire

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’aura aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par l’intermédiaire des services d’assistance Adobe ou d’une autre manière) les versions bêta. Il est conseillé aux clients d’être prudents et de ne pas se fier, de quelque manière que ce soit, au bon fonctionnement ou aux performances des versions bêta et/ou de la documentation ou du matériel les accompagnant. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

## Avantages de la participation

L’accès anticipé aux fonctionnalités développées par Adobe permet aux clients et aux partenaires de faire part de leurs commentaires, de façonner le développement des produits et de se préparer à adopter de nouvelles fonctionnalités avant leur disponibilité générale.

## Programmes Beta actuels

Consultez les sections suivantes pour obtenir la liste des programmes bêta actifs.

### Adobe Commerce Optimizer

Adobe Commerce Optimizer améliore votre expérience d’e-commerce grâce à une vitrine haute performance qui stimule le trafic organique, l’engagement des clients et le chiffre d’affaires.

Avec Adobe Commerce Optimizer, vous pouvez :

- Développez et mettez à l’échelle votre catalogue sans reconfigurer l’ensemble de votre pile commerciale.
- Ingérez des données de catalogue à partir de n’importe quelle source.
- Définissez des canaux et des politiques métier.
- Créez des recherches et des recommandations personnalisées à l’aide de l’IA et du ML.
- Affichez la disponibilité des données essentielles du produit, y compris l’état de synchronisation et les données d’événement du storefront pour une implémentation et un dépannage précis.

[En savoir plus](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html) sur Adobe Commerce Optimizer. Si vous souhaitez en savoir plus sur le programme d’accès anticipé [!DNL Adobe Commerce Optimizer], remplissez le [formulaire de demande d’accès anticipé](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4WOxhjY2doZPikS2hIbfmL5UMlhTMTYzVDhPQVFNTUFYUjJHNlRKTE5TWS4u).

### Amélioration des fonctionnalités de recherche pour la recherche en direct (Beta public)

Cette version Beta prend en charge trois nouvelles fonctionnalités dans la requête [`productSearch` ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) :

- **Recherche superposée** - Effectuez une recherche dans un autre contexte de recherche - Grâce à cette fonctionnalité, vous pouvez effectuer jusqu’à deux couches de recherche pour vos requêtes de recherche. Par exemple :

   - **Recherche de la couche 1** - Recherchez « Motor » sur « product_attribute_1 ».
   - **Recherche de la couche 2** - Recherchez « référence 123 » sur « product_attribute_2 ». Dans cet exemple, le « moteur » est recherché dans les résultats par « numéro de pièce 123 ».

  La recherche en couches est disponible pour l’indexation de recherche `startsWith` et l’indexation de recherche `contains`, comme décrit ci-dessous :

- **startsWith search indexation** - Effectuez une recherche à l’aide de l’indexation `startsWith`. Cette nouvelle fonctionnalité permet :

   - Recherche de produits dont la valeur d’attribut commence par une chaîne particulière.
   - La configuration d’une recherche « se termine par » afin que les acheteurs puissent rechercher des produits pour lesquels la valeur d’attribut se termine par une chaîne particulière. Pour activer une recherche « se termine par », l’attribut de produit doit être ingéré en inverse et l’appel API doit également être une chaîne inversée.

- **contient l’indexation de la recherche** : recherchez un attribut à l’aide de l’indexation contient. Cette nouvelle fonctionnalité permet :

   - Recherche d’une requête dans une chaîne plus grande. Par exemple, si un acheteur recherche le numéro de produit « PE-123 » dans la chaîne « HAPE-123 ».

      - Remarque : ce type de recherche est différent de la recherche existante [expression](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase), qui effectue une recherche de saisie automatique. Par exemple, si la valeur de l’attribut de votre produit est « pantalon extérieur », une expression de recherche renvoie une réponse pour « out pan », mais ne renvoie pas de réponse pour « oor ants ». Une recherche Contient , cependant, renvoie une réponse pour « fourmis ».

Ces nouvelles conditions améliorent le mécanisme de filtrage des requêtes de recherche pour affiner les résultats de recherche. Ces nouvelles conditions n’affectent pas la requête de recherche principale. Pour participer à la version bêta, envoyez une demande par e-mail à [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Pour installer la version Beta de Live Search, consultez le [Guide de Live Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta).

### Intégration du système IBM Sterling Order Management (Private Beta)

Cet accélérateur d’intégration pour IBM Sterling Order Management permet aux clients Adobe Commerce de commencer à utiliser des fonctionnalités avancées de gestion des commandes optimisées par IBM Sterling OMS. Grâce à cette intégration, les commerçants obtiennent :

- Visibilité en temps réel des niveaux de stock et dates de livraison précises pour vos clients.
- L&#39;approvisionnement automatisé pour les commandes basé sur des règles configurables, afin que vous puissiez optimiser votre réseau d&#39;exécution et vos stocks.
- Une vue universelle des commandes sur l’ensemble des canaux à partir d’un seul tableau de bord afin que vos équipes d’assistance puissent fournir un service exceptionnel et identifier et gérer rapidement les exceptions.
- Un flux de gestion des retours modélisé pour simplifier la gestion des retours.

Pour participer à cette version bêta, envoyez une demande par e-mail à [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Beta public)

Chaque version bêta d’Adobe Commerce Foundation comprend toutes les modifications apportées au code principal d’Adobe Commerce à la date de publication prévue, y compris, mais sans s’y limiter, les domaines fonctionnels suivants :

- Derniers correctifs de sécurité
- Améliorations des performances
- Améliorations de GraphQL
- Correctifs de qualité générale
- Contributions de la Communauté
- Modifications requises pour prendre en charge la compatibilité avec les [services Adobe Commerce](https://experienceleague.adobe.com/docs/commerce/user-guides/home.html)

#### Convention et planning d’affectation des noms

Adobe publie généralement les correctifs bêta deux fois par an.

Les packages de version Beta comportent un suffixe `-betaX`. Par exemple, les packages de version bêta d’Adobe Commerce 2.4.7 utilisent la convention de nommage suivante :

- `2.4.7-beta1`
- `2.4.7-beta2`

Consultez le [calendrier des versions](schedule.md) pour obtenir la liste des dates de publication des prochaines versions bêta publiques.

#### Accès à la version de Beta

Les versions bêta d’Adobe Commerce sont distribuées de la même manière que toute autre version de correctif Adobe Commerce : en tant que métapaquets du compositeur sur `https://repo.magento.com`. Le code source est disponible sur [GitHub](https://github.com/magento/magento2).

Voir [ Démarrage rapide de l’installation du compositeur](../installation/composer.md) pour plus d’informations.

#### Rapports sur les événements

Adobe ne fournit pas le service d’assistance Adobe standard pour les versions bêta.

Pour soumettre vos commentaires concernant les versions bêta, suivez notre [flux régulier de création de rapports sur les problèmes](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) sur [GitHub](https://github.com/magento/magento2).

Nos équipes internes surveilleront tous les problèmes critiques signalés par rapport à la dernière version bêta et leur donneront la priorité pour qu’ils soient résolus avant la date de publication de la version mise à disposition générale.
