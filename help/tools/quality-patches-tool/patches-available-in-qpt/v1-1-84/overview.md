---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.84'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.84.
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
source-wordcount: '549'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.84

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.84.

QPT v1.1.84 comprend les correctifs suivants :

1. **ACP2E-4913** : correction d’un problème en raison duquel les opérations d’expédition et de facturation échouent en raison d’un blocage.
1. **ACP2E-5005** : corrige le problème où la quantité d&#39;une option de produit groupé dans un devis négociable revient à sa valeur précédente lorsque le produit groupé est reconfiguré dans l&#39;administrateur et que la quantité est modifiée.
1. **ACP2E-5009** : correction d’un problème en raison duquel la migration des données de Magento Open Source vers Adobe Commerce ne migre pas correctement les modifications de conception planifiées des catégories et les mises à jour planifiées des **[!UICONTROL Special Price]** de produits, ce qui entraîne l’absence ou l’omission de certaines mises à jour planifiées lors de la migration et améliore les performances de la migration.
1. **ACP2E-5017** : correction d’un problème en raison duquel l’interrogation du rôle du client via GraphQL renvoie une *erreur de serveur interne* lorsque le client n’est pas affecté à une société.
1. **ACP2E-5027** : correction du problème où les indexeurs restent bloqués dans une boucle et où la réindexation ne se termine pas lorsque le verrouillage des fichiers est activé.
1. **ACP2E-5029** : correction d’un problème en raison duquel les modifications apportées aux règles de prix de catalogue n’apparaissent dans **[!DNL Live Search]** qu’après une resynchronisation manuelle.
1. **ACP2E-5041** : correction d’un problème en raison duquel l’enregistrement d’un produit lors d’une mise à jour planifiée entraînait l’affichage par le storefront du prix normal au lieu du **[!UICONTROL Special Price]** une fois la mise à jour terminée.
1. **ACP2E-5059** : correction du problème en raison duquel les clients reçoivent des e-mails de confirmation de commande en double pour la même commande.
1. **ACP2E-5122** : correction d’un problème en raison duquel les erreurs gérées à partir des requêtes GraphQL pour le panier étaient incorrectement enregistrées dans les journaux d’exceptions en tant qu’erreurs d’application.
1. **ACP2E-5143** : correction du problème en raison duquel la requête d’itinéraire GraphQL effectue le rendu de l’intégralité du contenu des pages CMS lorsque seules les métadonnées de routage sont demandées, ce qui augmente les requêtes de base de données pour les pages CMS contenant des widgets Page Builder.
1. **ACP2E-5183** : corrige le problème en raison duquel le déploiement du contenu statique échoue sur PHP 8.5 lors de la compilation d&#39;un fichier `LESS` qui utilise la directive `@magento_import`.
1. **ACP2E-5242** : correction d’un problème en raison duquel la vérification de la disponibilité du produit lors de l’ajout d’articles au panier affichait une erreur indiquant que le site web est introuvable.
1. **ACP2E-5263** : correction d’un problème en raison duquel l’exportation de produits dans un fichier CSV peut s’arrêter avant que tous les produits ne soient inclus, ce qui entraîne la création d’un fichier incomplet.
1. **ACP2E-5034** : Correction du problème en raison duquel la gestion des devis négociables réinitialise incorrectement les totaux sur *zéro* lors du recalcul d&#39;un devis après la sélection d&#39;un mode d&#39;expédition, ignore les mises à jour des quantités d&#39;option de produit groupé effectuées via l&#39;action **[!UICONTROL Configure]** dans l&#39;administrateur et ne reflète pas correctement les remises au niveau article appliquées aux produits groupés à prix dynamique dans les sous-totaux de devis.
1. **ACP2E-4741** : correction d’un problème en raison duquel un produit disparaît du storefront après qu’un produit qui lui est associé en tant que [!UICONTROL Related Product], [!UICONTROL Up-Sell] ou vente croisée a été enregistré alors qu’un stock et une source autres que ceux par défaut sont en cours d’utilisation.
1. **ACP2E-5079** : correction d’un problème en raison duquel l’évaluation d’un segment client affecté à plusieurs sites web renvoie les clients correspondants uniquement à partir du premier site web lorsque les comptes clients sont partagés globalement.
1. **ACP2E-5127** : correction d’un problème en raison duquel la modification d’un compte d’entreprise dans le panneau d’administration avec des paramètres régionaux autres que ceux par défaut réinitialise son **[!UICONTROL Credit Limit]** sur *zéro*.
1. **AC-15494** : correction du problème en raison duquel la requête products renvoie des noms de produit avec des caractères spéciaux d’échappement HTML au lieu de leurs caractères d’origine.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
