---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.78
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.78.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0494717c06fcabcb093a2b168ae714f773ed6f7b
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.78

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 comprend les correctifs suivants :
1. **ACP2E-4416** : correction d’un problème en raison duquel les points de récompense client ne sont pas initialisés lors de leur création dans l’administration.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)** : correction d’un problème en raison duquel les cartes-cadeaux ne sont pas appliquées correctement lors du passage en caisse après la validation réussie de reCAPTCHA v2 (« Je ne suis pas un robot ») sur le storefront.
1. **ACP2E-4431** : correction d’un problème en raison duquel les produits associés correspondant aux règles cible étaient supprimés lors du processus de réindexation.
1. **ACP2E-4448** : correction d’un problème en raison duquel les modifications de configuration effectuées lors des pannes de Redis ne sont pas prises en compte après la récupération de Redis, ce qui entraîne la persistance de valeurs obsolètes.
1. **ACP2E-4452** : correction du problème en raison duquel les prix des produits sur la page Commande rapide incluent la taxe, quelle que soit la configuration de l’affichage de la taxe.
1. **ACP2E-4456** : correction d’un problème en raison duquel l’annulation d’une commande à l’aide d’une mutation GraphQL ne fait pas passer une commande payée entièrement avec des cartes-cadeaux au statut Fermé.
1. **ACP2E-4507** : correction d’un problème en raison duquel la configuration des options de mot de passe n’était pas appliquée aux demandes de réinitialisation de mot de passe client effectuées par des mutations de GraphQL.
1. **ACP2E-4513** : corrige le problème en raison duquel les images CAPTCHA expirées ne sont pas supprimées du système.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)** : correction d’une erreur de clé en double intermittente qui se produit dans la table quote_coupons lorsque plusieurs demandes de fusion de panier ou d’enregistrement de devis s’exécutent simultanément.
1. **ACP2E-4528** : corrige le problème de validation de la ville dans les adresses des clients, qui autorise désormais une barre oblique (/) et rejette les caractères non valides tels que !,  », # et ?.
1. **ACP2E-4535** : correction d’un problème en raison duquel l’envoi du formulaire de mot de passe oublié entraîne la destruction ou la régénération de la session (modifications de PHPSESSID) et l’effacement du panier d’invités.
1. **ACP2E-4540** : correction d’un problème en raison duquel la bibliothèque Fotorama ne se chargeait pas correctement, ce qui rendait visible uniquement la première image jointe.
1. **ACP2E-4555** : corrige le problème des numéros de téléphone modernes contenant « . » ou « / » ne sont pas validés correctement.
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)** : corrige le problème en raison duquel la requête GraphQL d’entreprise renvoie « Le client actuel n’est pas autorisé » lorsque l’en-tête X-Adobe-Company est utilisé.
1. **ACP2E-4591** : correction d’un problème en raison duquel les segments de clients basés sur le nombre de commandes, tels que « Nouveaux acheteurs », n’étaient pas mis à jour lorsque des commandes étaient passées via l’API REST.
1. **ACP2E-4609** : correction du problème en raison duquel la page Mes devis n&#39;affiche aucun devis lorsque certains devis contiennent des produits supprimés.
1. **ACP2E-4613** : correction d’un problème en raison duquel les structures de répertoires multimédia volumineuses provoquaient des réponses gettree lentes, ce qui entraînait des temps de chargement d’arborescence de répertoires Media Gallery étendus.
1. **ACP2E-4628** : correction d’un problème en raison duquel l’importation de clients avec des adresses e-mail en majuscules entraînait l’erreur de clé de tableau indéfinie, lorsque le Partage de compte était défini sur Global.
1. **ACP2E-4665** : corrige le problème où les produits enfants de produits configurables contenant des vidéos dans les galeries de produits ne sont pas répertoriés lorsqu’ils sont demandés via l’API REST.
1. **ACP2E-4732** : correction d&#39;un problème en raison duquel l&#39;indexation partielle s&#39;arrêtait pour les clients avec un grand nombre de mises à jour lorsque la colonne version_id de la table changelog atteignait sa valeur maximale.
1. **ACP2E-4763** : correction du problème en raison duquel la requête customerOrders de GraphQL renvoie des valeurs original_price_include_tax et original_row_total_include_tax gonflées lorsque les prix du catalogue sont définis sur Taxe incluse, en raison d’une application double de la taxe.
1. **ACSD-60989** : correction d’un problème en raison duquel la modification d’une colonne avec une clé étrangère par le biais d’un schéma déclaratif entraînait des erreurs sur MariaDB.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
