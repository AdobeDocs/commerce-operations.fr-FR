---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.82
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.82.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 9ea2dec8843119280f9ee291a89590024ddd2973
workflow-type: tm+mt
source-wordcount: 484
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.82

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.82.

QPT v1.1.82 comprend les correctifs suivants :

1. **ACP2E-4815** : correction de plusieurs problèmes GraphQL qui provoquaient des exceptions PHP dans les journaux, une association correcte des commandes avec les comptes clients créés après la commande via GraphQL et l’alignement des réponses avec les spécifications GraphQL sur HTTP.
1. **ACP2E-4194** : correction d’un problème en raison duquel les réponses de GraphQL renvoyaient des codes d’état HTTP incorrects pour les requêtes non valides, non autorisées ou malformées.
1. **[ACP2E-4547](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547.md)** : correction d’un problème en raison duquel un utilisateur administrateur ne peut pas utiliser les **[!UICONTROL Add Products By SKU]** de l’administrateur pour ajouter des produits du catalogue par défaut à une commande pour une société affectée à un groupe de clients qui n’est pas lié à un catalogue partagé.
1. **ACP2E-4593** : correction d’un problème en raison duquel la page CMS affichée pour les restrictions de site web était incorrecte sur les sites web secondaires dans les déploiements multi-sites web.
1. **ACP2E-4682** : correction d’un problème en raison duquel la visite d’une page de Storefront qui vérifie le statut du devis `isActive` crée des enregistrements de devis vides chaque fois que la page est chargée.
1. **ACP2E-4695** : correction d’un problème en raison duquel l’indexeur de règles de catalogue consomme trop de mémoire et ne parvient pas à se terminer, provoquant une instabilité et des erreurs de mémoire insuffisante.
1. **ACP2E-4698** : correction d’un problème en raison duquel la modification d’une image dans le contenu texte de Page Builder enregistre une URL de média absolue au lieu de conserver une directive de média portable.
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)** : corrige le problème où l’expiration des points de récompense s’exécute lentement sur les magasins ayant un historique de points de récompense important, ce qui entraîne des retards dans l’expiration des points de récompense.
1. **ACP2E-4797** : correction d’un problème en raison duquel la saisie de caractères Unicode à 4 octets dans l’éditeur WYSIWYG ou le contenu du Créateur de page dans l’administrateur était incorrectement bloquée, même si la base de données était configurée pour prendre en charge `utf8mb4`.
1. **ACP2E-4799** : correction du problème en raison duquel la requête `requisition_lists` GraphQL renvoie une valeur `total_count` qui reflète uniquement le nombre d’éléments sur la page active au lieu du nombre total de listes de demandes d’approvisionnement qui correspondent aux critères de requête.
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)** : correction d’un problème en raison duquel les requêtes d’API de passage en caisse étaient considérablement plus lentes pour les produits configurables comportant de nombreux produits enfants lorsque le premier produit enfant vendable apparaissait en fin de liste.
1. **ACP2E-4840** : corrige le problème en raison duquel la valeur de quantité demandée dans la requête `products` GraphQL renvoie *null*.
1. **ACP2E-4870** : correction du problème en raison duquel les notifications par e-mail **[!UICONTROL Product Alerts]** ignorent les paramètres d’affichage des e-mails du magasin.
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)** : correction d’un problème en raison duquel l’affichage de comptes clients avec des carnets d’adresses volumineux dans l’administration déconnectait de manière inattendue les utilisateurs administrateurs.
1. **ACP2E-4894** : correction du problème en raison duquel les nouvelles commandes apparaissent tardivement dans les grilles de gestion des commandes d’administration lorsque la **[!UICONTROL Asynchronous Indexing]** est activée sur les magasins à volume élevé.
1. **ACP2E-4981** : correction d’un problème en raison duquel les carrousels de produits Page Builder affichent les produits dans un ordre qui ne reflète pas la position définie dans l’administration et incluent des produits configurables lorsque les produits enfants correspondants sont individuellement visibles.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
