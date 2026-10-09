---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.72.
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.72

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 comprend les correctifs suivants :

1. **ACSD-66807** : `report_viewed_product_index` tableau indique un nombre incorrect de pages vues de produits.
1. **ACSD-67187** : les utilisateurs administrateurs limités à des sites web autres que ceux par défaut voient l’erreur *«* Veuillez créer au moins un catalogue public partagé pour continuer* et ne peuvent pas accéder au bouton **[!UICONTROL Add New Company]** sur la grille de l’entreprise.
1. **ACSD-67383** : erreur lors de la connexion en tant que client avec deux comptes d’administrateur de société dans la même session.
1. **ACSD-67424** : `updated_at` valeur de la réponse de l&#39;API `GET /carts/search` [!DNL REST] ne correspond pas à la valeur affichée dans le **[!UICONTROL Admin panel]** lors de l&#39;utilisation de devis négociables.
1. **ACSD-67518** : la création de rapports avancée génère des lignes d’en-tête dupliquées lorsque le nombre de lignes dépasse la taille du lot.
1. **ACSD-67639** : la création d&#39;un avoir échoue pour les produits groupés dont le **[!UICONTROL Dynamic Price]** est défini sur *Non*.
1. **ACSD-67696** : les entrées `media_gallery` ne sont pas renvoyées dans le nœud de produit GraphQL du panier après un vidage du cache.
1. **ACSD-67941** : les requêtes GraphQL avec des noms de filtres inconnus entraînent des logs d&#39;exceptions PHP.
1. **ACSD-67946** : la mise à jour du panier affiche les bannières d’erreur en double.
1. **ACSD-68011** : SKU inexistantes affectées au catalogue partagé via l’API /V1/sharedCatalog/:id/assignProducts.
1. **ACSD-68040** : la page de recherche front-end ralentit sur [!DNL MariaDB] 10.6 avec un historique volumineux.
1. **ACSD-68064** : entrées en double créées lors des mises à jour planifiées dans les environnements comportant des catégories profondément imbriquées.
1. **ACSD-68092** : les options de produits groupés sont perdues après plusieurs enregistrements en raison d’une synchronisation incorrecte entre les mises à jour planifiées et les données de produits de base.
1. **ACSD-68118** : `customerCart` requête [!DNL GraphQL] renvoie des valeurs d’attribut de produit incorrectes pour la vue de magasin.


Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
