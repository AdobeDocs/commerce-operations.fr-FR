---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.83.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 758cab5d4002ddba607dadb3c4b44553adf8d8ba
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.83

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.83.

QPT v1.1.83 comprend les correctifs suivants :

1. **AC-17975** : corrige plusieurs problèmes de compatibilité PHP 8.5 affectant les workflows d’administration, l’authentification de passage en caisse, le traitement CAPTCHA, la gestion des catégories, les pages de configuration et les opérations de ligne de commande dans certains environnements PHP.
1. **AC-18128** : correction du problème en raison duquel les dates de commande et les horodatages des commentaires de commande renvoyés par GraphQL affichent des dates de calendrier incorrectes dans des paramètres régionaux non anglais.
1. **AC-18096** : correction du problème en raison duquel les champs de date de Sales GraphQL renvoient des dates dans un format différent des versions précédentes en rétablissant le format de date de slash-separée (`/`) à dash-separée (`-`).
1. **ACP2E-4639** : corrige le problème en raison duquel le type d&#39;éléments de la liste de demandes était mal orthographié dans le schéma GraphQL, tandis que le champ d&#39;éléments plus anciens et le type d&#39;`RequistionListItems` restent disponibles, mais sont obsolètes.
1. **ACP2E-4838** : correction du problème en raison duquel un utilisateur administrateur disposant d’autorisations limitées ne peut pas supprimer les clients de la grille Clients .
1. **ACP2E-4877** : correction du problème en raison duquel les commandes passées à l’aide de **[!UICONTROL Payment on Account]** ne pouvaient pas être modifiées dans l’administration lorsqu’elles avaient le statut *En attente*.
1. **ACP2E-4908** : correction du problème en raison duquel les catalogues volumineux entraînent une utilisation excessive de la mémoire dans Redis ou Valkey, car des entrées de cache de mise en page distinctes ont été créées pour chaque produit dans chaque vue de magasin.
1. **[AC-12854](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-12854.md)** : correction du problème en raison duquel la réorganisation d’une commande dans l’administration crée un nouveau numéro de commande avec un suffixe `-1` au lieu d’attribuer le numéro de commande séquentiel suivant.
1. **ACP2E-4977** : correction du problème en raison duquel les totaux généraux des factures et des avoirs pour les produits configurables n&#39;incluent pas les **[!UICONTROL Fixed Product Tax]** (FPT), ce qui entraîne des totaux inférieurs au total de la commande.
1. **AC-16530** : correction d’un problème en raison duquel le panier ne reflétait pas de manière cohérente les mises à jour planifiées des règles de prix de catalogue.
1. **AC-11389** : correction d’un problème en raison duquel les remises, les taxes et les totaux des commandes ne sont pas calculés correctement dans certains scénarios d’arrondi.
1. **ACP2E-4998** : correction d’un problème en raison duquel la requête `POST /V1/products/tier-prices` de l’API REST échouait pour l’ensemble de la requête alors qu’il n’existait pas de SKU dans la payload, empêchant la mise à jour des SKU valides.
1. **ACP2E-5015** : correction d’un problème en raison duquel l’enregistrement d’un catalogue partagé dans l’administration peut involontairement supprimer les produits affectés et le prix lorsque les données de catalogue requises ne sont pas disponibles.
1. **AC-14940** : correction d’un problème en raison duquel un clic sur **[!UICONTROL Reset Password]** pour un compte client dans l’administrateur n’envoyait pas l’e-mail de réinitialisation de mot de passe dans certains cas liés au magasin .
1. **[ACP2E-5101](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5101.md)** : correction d’un problème en raison duquel l’installation du module B2B échouait lorsque les indexeurs étaient définis sur **[!UICONTROL Update by Schedule]**.
1. **ACP2E-5205** : corrige le problème lorsque le chargement d’une catégorie prend beaucoup de temps ou entraîne un délai d’expiration lorsqu’un grand nombre de catégories et de produits est impliqué. En outre, le nombre de produits est désormais correctement affiché pour chaque feuille de catégorie.
1. **ACP2E-3211** : correction d’un problème en raison duquel l’ajout d’un même produit au panier en même temps sur la vitrine crée des articles distincts dans le panier pour le même SKU au lieu de les combiner en un seul article.
1. **[ACP2E-5223](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5223.md)** : correction du problème en raison duquel l’index **[!UICONTROL Catalog Permissions]** inclut les sites web exclus d’un groupe de clients.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
