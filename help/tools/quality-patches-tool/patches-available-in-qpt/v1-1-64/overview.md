---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.64
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.64.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f6013ec84c1b3c65e2fe2ca062616976326d2fef
workflow-type: tm+mt
source-wordcount: '261'
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
