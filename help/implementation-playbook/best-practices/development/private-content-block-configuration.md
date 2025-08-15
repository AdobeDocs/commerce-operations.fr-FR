---
title: Bonnes pratiques relatives aux blocs de contenu privés
description: Découvrez les bonnes pratiques de configuration des blocs de contenu privés pour optimiser les performances du storefront.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Bonnes pratiques relatives aux blocs de contenu privés

Lorsqu’un bloc de contenu privé contient la variable `_isScopePrivate`, il n’est pas possible de le mettre en cache. Comme le bloc privé n’est pas mis en cache, Adobe Commerce doit récupérer les mêmes données pour chaque demande du client, ce qui augmente la charge du serveur.

Au lieu d’utiliser la variable `_isScopePrivate` pour le contenu privé, créez un bloc et un modèle pour afficher les données agnostiques de l’utilisateur. Ces données sont remplacées par des données spécifiques à l’utilisateur par le composant de l’interface utilisateur d’Adobe Commerce, qui gère plus efficacement les données de pré-rendu. Pour obtenir des instructions, consultez [Contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) dans la _[!DNL Commerce PHP Extensions Guide]_.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce On-Premise

## Impact potentiel sur les performances

Les sites dont les blocs de contenu privés contiennent les variables `_isScopePrivate` déclenchent des requêtes AJAX afin de récupérer les mêmes données pour chaque requête client. Cela augmente le temps de réponse et utilise des ressources supplémentaires qui peuvent être utilisées pour gérer davantage d’opérations de storefront critiques, telles que l’enregistrement des clients, les mises à jour de panier, la soumission de commandes et les transactions de paiement.

## Informations supplémentaires

- [Contenu privé](../../../performance/configuration.md#client-side-optimization-settings)
- [Les requêtes AJAX à débit élevé entraînent de faibles performances](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
