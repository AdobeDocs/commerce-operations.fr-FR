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
source-git-commit: 3d95ebd821afb07c08b65e5e8b911ada2d9e58ae
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.84

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.84.

QPT v1.1.84 comprend les correctifs suivants :

1. **[ACP2E-5005](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5005.md)** : corrige le problème où la quantité d&#39;une option de produit groupé dans un devis négociable revient à sa valeur précédente lorsque le produit groupé est reconfiguré dans l&#39;administrateur et que la quantité est modifiée.
1. **[ACP2E-4913](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4913.md)** : correction d’un problème en raison duquel les opérations d’expédition et de facturation échouent en raison d’un blocage.
1. **[ACP2E-5009](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5009.md)** : correction d’un problème en raison duquel la migration des données de Magento Open Source vers Adobe Commerce ne migre pas correctement les modifications de conception planifiées des catégories et les mises à jour planifiées des produits **[!UICONTROL Special Price]**, ce qui entraîne l’absence ou l’omission de certaines mises à jour planifiées lors de la migration et améliore les performances de la migration.
1. **[ACP2E-5017](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5017.md)** : correction du problème en raison duquel l’interrogation du client `role` via GraphQL renvoie *une erreur de serveur interne* lorsque le client n’est pas affecté à une société.
1. **[ACP2E-5027](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5027.md)** : correction d’un problème en raison duquel les indexeurs restent bloqués dans une boucle et la réindexation ne se termine pas lorsque le verrouillage des fichiers est activé.
1. **ACP2E-5029** : correction du problème en raison duquel les modifications apportées aux règles de prix de catalogue n’apparaissent pas dans **[!DNL Live Search]** tant qu’une resynchronisation manuelle n’a pas été effectuée.
1. **[ACP2E-5041](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5041.md)** : correction d’un problème en raison duquel l’enregistrement d’un produit lors d’une mise à jour planifiée entraînait l’affichage par le storefront du prix normal au lieu du **[!UICONTROL Special Price]** une fois la mise à jour terminée.
1. **[ACP2E-5183](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5183.md)** : corrige le problème en raison duquel le déploiement du contenu statique échoue sur PHP 8.5 lors de la compilation d’un fichier `LESS` qui utilise la directive `@magento_import`.
1. **[ACP2E-5059](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5059.md)** : correction du problème en raison duquel les clients reçoivent des e-mails de confirmation de commande en double pour la même commande.
1. **[ACP2E-5122](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5122.md)** : correction d’un problème en raison duquel les erreurs gérées à partir des requêtes GraphQL pour le panier étaient incorrectement enregistrées dans les journaux d’exceptions en tant qu’erreurs d’application.
1. **[ACP2E-5143](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5143.md)** : correction du problème en raison duquel la requête GraphQL `route` effectue le rendu de l’intégralité du contenu des pages CMS lorsque seules les métadonnées de routage sont demandées, ce qui augmente les requêtes de base de données pour les pages CMS contenant des widgets Page Builder.
1. **[ACP2E-5242](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5242.md)** : correction d’un problème en raison duquel la vérification de la disponibilité du produit lors de l’ajout d’articles au panier affichait une erreur indiquant que le site web est introuvable.
1. **[ACP2E-5263](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5263.md)** : correction d’un problème en raison duquel l’exportation de produits dans un fichier CSV peut s’arrêter avant que tous les produits ne soient inclus, ce qui entraîne la création d’un fichier incomplet.
1. **[ACP2E-5034](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5034.md)** : correction du problème en raison duquel la gestion des devis négociables réinitialise incorrectement les totaux à *zéro* lors du recalcul d&#39;un devis après la sélection d&#39;une méthode d&#39;expédition, ignore les mises à jour des quantités d&#39;option de produit groupé effectuées via l&#39;action **[!UICONTROL Configure]** dans l&#39;Administration et ne reflète pas correctement les remises au niveau article appliquées aux produits groupés à prix dynamique dans les sous-totaux de devis.
1. **[AC-15494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/ac-15494.md)** : correction du problème en raison duquel la requête products renvoie des noms de produit avec des caractères spéciaux d’échappement HTML au lieu de leurs caractères d’origine.
1. **[ACP2E-4741](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4741.md)** : correction d’un problème en raison duquel un produit disparaît du storefront après l’enregistrement d’un produit qui lui est lié en tant que [!UICONTROL Related Product], [!UICONTROL Up-Sell] ou vente croisée pendant l’utilisation d’un stock et d’une source autres que ceux par défaut.
1. **[ACP2E-5127](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5127.md)** : correction du problème en raison duquel la modification d’un compte d’entreprise dans l’administration avec des paramètres régionaux autres que ceux par défaut réinitialise son **[!UICONTROL Credit Limit]** sur *0*.
1. **[ACP2E-5079](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5079.md)** : correction d’un problème en raison duquel l’évaluation d’un segment client affecté à plusieurs sites web renvoie des clients correspondants uniquement à partir du premier site web lorsque les comptes client sont partagés dans le monde entier.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
