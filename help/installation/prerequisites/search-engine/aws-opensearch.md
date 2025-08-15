---
title: AWS OpenSearch
description: Pour configurer le service web AWS OpenSearch pour les installations sur site d’Adobe Commerce, procédez comme suit.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 prend en charge l’utilisation de clusters de services Amazon OpenSearch. Ce service succède au service Amazon Elasticsearch. Cette rubrique décrit comment configurer Commerce pour utiliser AWS OpenSearch et comment migrer les données d’une instance Elasticsearch ou OpenSearch locale vers un cluster AWS OpenSearch.

## Création d’un domaine de service AWS OpenSearch

Vous devez d’abord établir une instance OpenSearch dans AWS.
Lisez [Création et gestion des domaines de service Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) pour obtenir des instructions détaillées.

## Transfert de données vers AWS OpenSearch

Une fois que tout est préparé sur AWS, il est temps de le renseigner avec des données.

Pour les installations plus petites, il est recommandé de créer des index directement sur l’instance AWS, et ce pour les raisons suivantes :

* Recréer les index est une opération rapide.
* Il peut y avoir des incompatibilités de version entre l’ancienne instance et l’instance AWS, et elles peuvent être évitées en créant directement sur l’instance AWS.

Les installations plus grandes peuvent envisager de migrer leurs index de données de l’instance existante vers AWS. Bien que cela puisse réduire les temps d’arrêt, il existe toujours un faible risque de problèmes d’incompatibilité en raison de versions différentes entre l’ancien serveur Elasticsearch et AWS.

Il n’est pas nécessaire de migrer les index, car ils peuvent être facilement recréés sur l’instance AWS.
Toutefois, lors de la migration des index de données, assurez-vous que les versions d’Elasticsearch/OpenSearch sont compatibles.

Pour plus d’informations, consultez les instructions d’Amazon [Migration vers le service Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html).

### Configuration de Commerce pour OpenSearch

Les étapes de configuration d’OpenSearch sont décrites dans la rubrique [Installation avancée](../../advanced.md).

Pour tester le bon fonctionnement de la nouvelle configuration, testez directement le point d’entrée OpenSearch :

1. Créez un produit dans l’administration (par exemple : sku=« testproduct1 »).
1. Réindexez-le via l’administrateur.
1. Exécutez une requête sur le point d’entrée OpenSearch (disponible dans l’interface utilisateur d’AWS) :

   Pour obtenir des index, ajoutez : `/_cat/indices/*?v=true` à l’URL :
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Pour obtenir des produits à partir de l’index, ajoutez : `/magento2docker_product_1/_search?q=*` à l’URL :
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Ressources supplémentaires

Pour plus d’informations, consultez la [documentation d’OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).
