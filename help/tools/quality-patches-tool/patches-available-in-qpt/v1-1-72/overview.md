---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.72
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a6a18a4cbab9d2e5a0c4824fc5ad9463f9e61c1c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.72

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 comprend les correctifs suivants :
1. **ACSD-68040** : la page de recherche front-end présente une dégradation des performances sur les [!DNL MariaDB] 10.6 et 11.4 avec de nombreuses requêtes de recherche historiques.
1. **ACSD-67941** : les requêtes GraphQL avec des noms de filtres inconnus entraînent des logs d&#39;exceptions PHP.
1. **ACSD-68064** : la création de mises à jour planifiées entraîne des entrées en double dans les environnements comportant un grand nombre de catégories imbriquées.
1. **ACSD-66807** : `report_viewed_product_index` tableau indique un nombre incorrect de pages vues de produits.
1. **ACSD-67383** : la connexion en tant que client avec deux comptes d’administration de société dans la même session entraîne une erreur *Aucune entité de ce type avec cartId*.
1. **ACSD-67518** : la création de rapports avancée génère des lignes d’en-tête dupliquées lorsque le nombre de lignes dépasse la taille du lot.
1. **ACSD-67639** : la création d&#39;un avoir échoue pour les produits groupés dont le **[!UICONTROL Dynamic Price]** est défini sur *Non*.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)** : les entrées `media_gallery` ne sont pas renvoyées dans le nœud de produit GraphQL du panier après un vidage du cache.
1. **ACSD-67946** : les mises à jour du panier affichent les bannières d’erreur en double.
1. **ACSD-68011** : les SKU inexistantes peuvent être affectées à un catalogue partagé via l’API `/V1/sharedCatalog/:id/assignProducts` [!DNL REST].
1. **ACSD-68118** : `customerCart` requête GraphQL renvoie des valeurs d’attribut de produit qui ne reflètent pas l’en-tête du magasin, ce qui entraîne une localisation incohérente.
1. **ACSD-68092** : les options de produits groupés sont perdues après plusieurs enregistrements en raison d’une synchronisation incorrecte entre les mises à jour planifiées et les données de produits de base.
1. **ACSD-67424** : `updated_at` valeur de la réponse de l&#39;API `GET /carts/search` [!DNL REST] ne correspond pas à la valeur affichée dans le **[!UICONTROL Admin panel]** lors de l&#39;utilisation de devis négociables.
1. **ACSD-67187** : les utilisateurs administrateurs limités à des sites web autres que ceux par défaut voient l’erreur * »*Veuillez créer au moins un catalogue public partagé pour continuer* et ne peuvent pas accéder au bouton **[!UICONTROL Add New Company]** sur la grille de l’entreprise.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
