---
title: AWS OpenSearch
description: Pour configurer le service Web OpenSearch AWS pour les installations sur site d’Adobe Commerce, procédez comme suit.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 prend en charge l’utilisation des grappes de services OpenSearch d’Amazon. Ce service succède à Amazon Elasticsearch Service. Cette rubrique décrit comment configurer Commerce pour utiliser AWS OpenSearch et comment migrer les données d’un Elasticsearch local ou d’une instance OpenSearch vers une grappe AWS OpenSearch.

## Création d’un domaine de service OpenSearch AWS

Vous devez d’abord établir une instance OpenSearch dans AWS.
Lecture [Création et gestion des domaines de service OpenSearch Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) pour obtenir des instructions détaillées.

## Obtention de données pour AWS OpenSearch

Une fois que tout est préparé sur AWS, il est temps de le remplir avec des données.

Pour les installations plus petites, nous vous recommandons de créer des index directement sur l’instance AWS pour les raisons suivantes :

* Recréer les indices est une opération rapide.
* Il peut y avoir des incompatibilités de versions entre l’ancienne instance et l’instance AWS, et celles-ci peuvent être évitées en se basant directement sur l’instance AWS.

Les installations plus volumineuses peuvent envisager de migrer leurs index de données de l’instance existante vers AWS. Bien que cela puisse réduire les temps d’arrêt, il existe encore un faible risque de problèmes d’incompatibilité en raison de versions différentes entre l’ancien serveur Elasticsearch et AWS.

Il n’est pas nécessaire de migrer les index, car ils peuvent être facilement recréés sur l’instance AWS.
Cependant, lors de la migration des index de données, assurez-vous que les versions d’Elasticsearch/OpenSearch sont compatibles.

Voir Amazon [Migration vers le service Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) instructions pour plus d’informations.

### Configuration de Commerce pour OpenSearch

Les étapes de configuration d’OpenSearch sont décrites dans la section [Installation avancée](../../advanced.md) rubrique.

Pour vérifier que la nouvelle configuration fonctionne, testez directement le point de terminaison OpenSearch :

1. Créez un produit dans l’Admin (par exemple : sku=&quot;testproduct1&quot;).
1. Réindexez par l’intermédiaire de l’administrateur.
1. Interrogez le point de terminaison OpenSearch (disponible dans l’interface utilisateur d’AWS) :

   Pour obtenir des index, ajoutez : `/_cat/indices/*?v=true` à l’URL :
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Pour obtenir des produits à partir de l’index, ajoutez : `/magento2docker_product_1/_search?q=*` à l’URL :
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Ressources supplémentaires

Pour plus d’informations, voir [Documentation OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).
