---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.77
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.77.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.77

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.77.

QPT v1.1.77 comprend les correctifs suivants :

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)** : correction d’un problème en raison duquel des prix incorrects s’affichent parce qu’il n’est pas possible de nettoyer [!DNL Redis] cache.
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)** : corrige un problème en raison duquel `X-Magento-Vary` cookie est défini plusieurs fois pendant le chargement du PDP, lorsque plusieurs segments de clients sont créés au niveau du magasin.
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)** : correction d’un problème en raison duquel les performances de passage en caisse se dégradaient à mesure que le nombre de segments de clients augmentait.
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)** : correction d’un problème en raison duquel l’aperçu de la mise à jour planifiée s’interrompt lors de la tentative de prévisualisation du contenu des magasins avec des domaines personnalisés.
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)** : corrige un problème en raison duquel la création d’un compte client échoue lors de l’utilisation du paramètre régional Arabe et l’attribut Date de naissance (DOB) est défini pour s’afficher sur le storefront.
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)** : corrige un problème en raison duquel les pages pouvant être mises en cache ne sont pas correctement stockées ou diffusées à partir du cache [!DNL Fastly], ce qui entraîne un comportement de mise en cache incohérent et une réduction des performances.
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)** : correction d’un problème en raison duquel le prix spécial n’est pas pris en compte pour les sites web créés dans différents fuseaux horaires.
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)** : corrige un problème en raison duquel un produit configurable est automatiquement inclus dans les listes de carrousel de produits [!DNL Page Builder] si l’un de ses produits enfants répond aux conditions de filtrage.
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)** : corrige un problème en raison duquel le nombre d’entrées pouvant être traitées et insérées par le biais des tâches cron `sales_*_async_insert` est limité à *100* par exécution.
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)** : Correction d&#39;un problème lié au calcul incorrect de la taxe dans les avoirs lors de la création d&#39;un remboursement partiel à partir d&#39;une facture, si un avoir précédent a été créé à partir de la page d&#39;affichage de la commande.
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)** : correction d’un problème en raison duquel les soldes des cartes-cadeaux et les dates d’expiration ne s’affichent pas conformément à la portée du site web qui leur est attribuée.
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)** : corrige un problème lié aux opérations de remboursement asynchrones en raison duquel les demandes de remboursement avec le paramètre `is_online` ne sont pas traitées correctement.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
