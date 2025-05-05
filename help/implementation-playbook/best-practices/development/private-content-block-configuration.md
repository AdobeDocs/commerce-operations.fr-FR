---
title: Bonnes pratiques relatives aux blocs de contenu privé
description: Découvrez les bonnes pratiques pour configurer des blocs de contenu privés afin d’optimiser les performances du storefront.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Bonnes pratiques relatives aux blocs de contenu privé

Lorsqu’un bloc de contenu privé contient la variable `_isScopePrivate`, le bloc ne peut pas être mis en cache. Comme le bloc privé n’est pas mis en cache, Adobe Commerce doit récupérer les mêmes données pour chaque demande client, ce qui augmente la charge serveur.

Au lieu d’utiliser la variable `_isScopePrivate` pour le contenu privé, créez un bloc et un modèle pour afficher les données indépendantes des utilisateurs. Ces données sont remplacées par des données spécifiques à l’utilisateur par le composant d’interface utilisateur d’Adobe Commerce, qui gère plus efficacement les données de prérendu. Pour obtenir des instructions, voir [Contenu privé](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) dans _[!DNL Commerce PHP Extensions Guide]_.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Impact potentiel sur les performances

Les sites qui comportent des blocs de contenu privés contenant les variables `_isScopePrivate` déclenchent AJAX demandes de récupération des mêmes données pour chaque demande du client. Cela augmente le temps de réponse et utilise des ressources supplémentaires qui peuvent être utilisées pour gérer davantage d’opérations de vitrine critiques telles que l’enregistrement des clients, les mises à jour du panier, l’envoi de commandes et les transactions de paiement.

## Informations supplémentaires

- [Contenu privé](../../../performance/configuration.md#client-side-optimization-settings)
- [Les demandes d&#39;AJAX à débit élevé provoquent des performances médiocres](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html?lang=fr)
