---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
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
source-wordcount: '296'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.48

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 comprend les correctifs suivants :

1. **ACSD-55566** : corrige le problème d’échec de l’*[!UICONTROL mergeCart mutation]* avec une *Erreur de serveur interne* dans la réponse de GraphQL lorsque la fusion des paniers source et de destination comporte les mêmes éléments groupés.
1. **ACSD-56546** : corrige le problème d’affichage des produits configurables et groupés comme *[!UICONTROL Out of Stock]* sur le storefront lorsque la configuration *[!UICONTROL Display Out of Stock Product]* est désactivée.
1. **ACSD-56635** : corrige le problème de duplication du client importé avec la même adresse e-mail lorsque l’importation est utilisée avec [!UICONTROL Account Sharing] définie sur *[!UICONTROL Global]*.
1. **ACSD-56741** : corrige le message d’erreur *Tentative d’accès au décalage du tableau sur une valeur de type null* qui s’affiche lors de l’`setup:upgrade` lorsque la base de données contient un déclencheur MySQL personnalisé non lié au mécanisme d’indexation et aux [!DNL MView].
1. **ACSD-57315** : permet de résoudre le problème de création d’une transaction dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton **[!UICONTROL Fetch]** de l’écran Afficher la transaction de l’[!UICONTROL Admin].
1. **ACSD-57337** : corrige le problème en raison duquel un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques peut voir les sociétés de tous les sites web dans la grille de *[!UICONTROL Companies]*.
1. **ACSD-57394** : correction d’un tri incorrect des produits en fonction de plusieurs champs de tri dans GraphQL.
1. **ACSD-57565** : corrige le problème en raison duquel le tableau de bord *[!UICONTROL Order]* affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Le tableau de bord affiche désormais des statistiques d’ordre correctes au premier chargement.
1. **ACSD-57854** : correction du problème en raison duquel les requêtes GraphQL de produit renvoient des catégories désactivées dans les agrégations de catégories.
1. **ACSD-58008** : corrige le problème en raison duquel la mise à jour d’une mise à jour planifiée supprime la version précédente de l’élément intermédiaire si aucune date de fin n’est spécifiée.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
