---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.64.
feature: Tools and External Services
role: Admin, Developer
exl-id: e86b8557-a14a-40e2-a181-56efa4383a1c
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
source-wordcount: '263'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.64

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.64.

QPT v1.1.64 comprend les correctifs suivants :

1. **ACP2E-3838** : correction du problème en raison duquel les erreurs CORS [!DNL Page Builder] empêchent l’enregistrement des modifications dans le panneau d’administration en mode production.
1. **ACP2E-3841** : correction d’un problème en raison duquel les règles de prix de panier pour les produits à expédition multiple ne s’appliquent pas correctement lorsque des conditions `subselect` sont utilisées et que **[!UICONTROL Free Shipping]** est activé.
1. **ACSD-63139** : corrige le problème d’échec de l’exportation du produit lorsque les attributs du produit contiennent des milliers de valeurs d’option.
1. **ACSD-65100** : correction d’un problème en raison duquel la suppression des valeurs de **[!UICONTROL Maximum Width]** et **[!UICONTROL Maximum Height]** dans la configuration **[!UICONTROL Media Gallery Image Optimization]** entraînait une erreur lors du processus d’optimisation de l’image.
1. **ACSD-65127** : correction d’un problème en raison duquel l’activation de la minimisation JavaScript en mode de production entraîne la génération d’erreurs par [!DNL TinyMCE] 6 dans la console du navigateur, ce qui affecte les fonctionnalités et l’expérience utilisateur.
1. **ACSD-65787** : corrige le problème de blocage de la classe `SchemaBuilder` lors de la création ou des mises à jour de schémas en raison d’une clé de tableau non définie *colonne* lors du traitement des données de table.
1. **ACSD-65223** : permet de résoudre le problème d&#39;erreur lié aux conditions générales sélectionnées manuellement pour les commandes fournisseur [!DNL B2B].
1. **ACSD-65540** : corrige le problème d’erreur de syntaxe SQL due à l’absence de la fonction `REGEXP_LIKE` lors de la mise à jour de la table `company_structure`.
1. **ACSD-65684** : corrige le problème de performances en raison duquel la mise à niveau du module `Magento_Company` après la mise à jour vers la [!DNL B2B] 1.5.2 prenait trop de temps lors du traitement d’un grand nombre d’enregistrements (~100 000+) dans la table `company_structure`.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
