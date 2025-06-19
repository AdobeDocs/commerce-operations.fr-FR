---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.2
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.2.
feature: Tools and External Services
role: Admin
exl-id: 14aaee46-2113-4ed6-8a54-9eb89e801fcd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.2

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.2.

QPT v1.1.2 comprend les correctifs suivants :

1. **MDVA-37115** : corrige le problème d’affichage d’un avis inutile *Il ne reste que 0* sur la page des produits configurables.
1. **MDVA-37364** : correction du problème en raison duquel l’attribut du client personnalisé de type date rompt l’interface utilisateur de la grille du client.
1. **MDVA-38447** : corrige deux problèmes : où les produits enfants configurables *Non visibles individuellement* sont renvoyés dans la réponse GraphQL et optimisent la requête MySQL pour la requête de produits GraphQL avec un filtre de catégorie.
1. **MDVA-38852** : correction du problème en raison duquel l’inventaire du catalogue verrouille par conception les tables pour les mises à jour qui diminuent considérablement les performances dans les cas où plusieurs commandes sont parallèles.
1. **MDVA-38929** : correction du problème en raison duquel la facture avec FPT affiche un total général incorrect lorsque la commande est payée à partir du crédit du magasin.
1. **MDVA-39043** : correction d’un problème en raison duquel l’utilisateur administrateur à accès limité recevait une erreur lors de la tentative d’ajout du widget *Products* à la page CMS.
1. **MDVA-39195** : correction du problème en raison duquel **[!UICONTROL Add to Cart]** bouton était inactif sur la page de catégorie lorsque la redirection vers le panier était activée.
1. **MDVA-39384** : correction du problème en raison duquel l’attribut du client personnalisé d’un utilisateur d’entreprise n’est pas enregistré.
1. **MDVA-39521** : corrige le problème en raison duquel l’utilisateur ne peut pas définir d’adresses de livraison dans le panier avec un numéro de téléphone vide via GraphQL.
1. **MDVA-39923** : corrige le problème où les clients et clientes obtiennent une erreur lorsqu’ils ou elles recherchent la fonctionnalité de commande rapide par SKU dans B2B avec une casse différente de celle avec laquelle le nom est enregistré.
1. **MDVA-39935** : correction du problème en raison duquel le GraphQL renvoie des produits enfants configurables désactivés au niveau du site web.
1. **MDVA-39966** : correction d’un problème lié au déploiement de paramètres régionaux incorrects.
1. **MDVA-39986** : corrige le problème en raison duquel l’utilisateur ne peut pas passer de commande dans l’interface d’administration de MacOS à l’aide du navigateur Safari.
1. **MDVA-40134** : correction du problème en raison duquel GraphQL ne renvoie pas de produits associés lorsque le catalogue partagé est activé.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
