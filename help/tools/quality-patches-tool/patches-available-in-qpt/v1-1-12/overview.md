---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.12'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.12.
feature: Tools and External Services
role: Admin
exl-id: 75c0848c-b815-47af-86e8-221daf53776c
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%
---
# Présentation d’[!DNL Quality Patches Tool] (QPT) v1.1.12

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.12.

QPT v1.1.12 comprend les correctifs suivants :

1. **MDVA-39546** : corrige le problème en raison duquel la date de début de la mise à jour de l’évaluation pouvait être définie à une date antérieure à la date actuelle lors de la modification.
1. **MDVA-39713** : corrige le problème en raison duquel l’utilisateur ou l’utilisatrice peut modifier l’heure de début d’une mise à jour planifiée active.
1. **MDVA-39993** : corrige le problème en raison duquel les modifications d’inventaire effectuées par le biais de l’API ne sont pas reflétées sur la page produit sur le serveur frontal.
1. **MDVA-41136** : correction d’un problème en raison duquel la date d’expiration du `mage-cache-sessid` n’est pas prolongée, ce qui entraîne un nettoyage des données client.
1. **MDVA-41229** : correction du problème en raison duquel les images disponibles sur le serveur principal ne s’affichent pas sur le serveur frontal après l’importation de produits configurables.
1. **MDVA-41628** : correction du problème en raison duquel les utilisateurs administrateurs restreints existants accèdent aux nouvelles ressources lorsque de nouveaux modules sont ajoutés.
1. **MDVA-42410** : correction du problème en raison duquel les rapports de coupon n’affichent que la devise de base par défaut.
1. **MDVA-42645** : corrige le problème en raison duquel l’administrateur ne peut pas rembourser les points de récompense si la fonctionnalité de crédit de magasin est désactivée.
1. **MDVA-42689** : correction du problème en raison duquel Adobe Commerce renvoie une erreur *violation de contrainte d’intégrité* lors de la mise à jour des catégories de produits lors de l’importation.
1. **MDVA-42855** : corrige le problème en raison duquel une nouvelle adresse de client n’est pas enregistrée dans le carnet d’adresses lors du passage en caisse.
1. **MDVA-42950** : correction d’un problème en raison duquel les vidéos ne sont pas lues sur la page produit.
1. **MDVA-43232** : correction du problème en raison duquel le tri des produits dans [!DNL Visual Merchandiser] par Prix spécial en bas/en haut provoque une erreur lors de l’enregistrement de la catégorie.
1. **MDVA-43348** : corrige le problème en raison duquel la requête GraphQL de carte cadeau affiche une erreur si `gift_card_options` contient *uid*.
1. **MDVA-43414** : corrige l’erreur fatale PHP qui se produit lors de l’exécution du client de la file d’attente `inventory.reservations.updateSalabilityStatus` sur des SKU numériques.
1. **MDVA-43726** : correction du problème en raison duquel la règle de prix de catalogue basée sur la correspondance d’attributs au niveau du magasin ne s’applique pas après une réindexation partielle.
1. **MDVA-43731** : correction du problème en raison duquel *les synonymes de recherche* ne fonctionnent plus lorsque de la valeur est ajoutée dans *Termes minimaux à correspondre*.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
