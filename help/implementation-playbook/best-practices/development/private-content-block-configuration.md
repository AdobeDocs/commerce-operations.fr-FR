---
title: Bonnes pratiques relatives aux blocs de contenu privé
description: Découvrez les bonnes pratiques pour configurer des blocs de contenu privés afin d’optimiser les performances du storefront.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Bonnes pratiques relatives aux blocs de contenu privé

Lorsqu’un bloc de contenu privé contient la variable `_isScopePrivate` , le bloc ne peut pas être mis en cache. Comme le bloc privé n’est pas mis en cache, Adobe Commerce doit récupérer les mêmes données pour chaque demande client, ce qui augmente la charge serveur.

Au lieu d’utiliser la variable `_isScopePrivate` pour le contenu privé, créez un bloc et un modèle afin d’afficher les données indépendantes de l’utilisateur. Ces données sont remplacées par des données spécifiques à l’utilisateur par Adobe Commerce. [Composant d’interface utilisateur](https://glossary.magento.com/ui-component/), qui gère plus efficacement les données de prérendu. Pour obtenir des instructions, voir [Contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) dans le _[!DNL Commerce PHP Extensions Guide]_.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Impact potentiel sur les performances

Sites qui disposent de blocs de contenu privé contenant les `_isScopePrivate` déclenchent des requêtes AJAX pour récupérer les mêmes données pour chaque requête client. Cela augmente le temps de réponse et utilise des ressources supplémentaires qui peuvent être utilisées pour gérer davantage d’opérations de vitrine critiques telles que l’enregistrement des clients, les mises à jour du panier, l’envoi de commandes et les transactions de paiement.

## Informations supplémentaires

- [Contenu privé](../../../performance/configuration.md#client-side-optimization-settings)
- [Les demandes d’AJAX à débit élevé provoquent des performances médiocres](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


