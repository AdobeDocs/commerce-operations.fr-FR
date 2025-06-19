---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.34
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.34.
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.34

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.34.

QPT v1.1.34 comprend les correctifs suivants :

1. **ACSD-52277** : corrige le problème de redirection incorrecte d’un utilisateur administrateur après avoir sélectionné la vue du magasin lors de la création d’une nouvelle commande dans l’administrateur.
1. **ACSD-50813** : corrige le problème en raison duquel un administrateur ne peut pas ajouter de produits groupés contenant une barre oblique dans le SKU avec la fonctionnalité [!UICONTROL Add Products by SKU] à la commande d’administration.
1. **ACSD-51630** : corrige le problème en raison duquel une grande quantité de messages système ralentit le téléchargement des pages d’administration.
1. **ACSD-51853** : correction du problème en raison duquel les styles de texte copiés ne sont pas appliqués lors de l’utilisation de [!DNL Page Builder].
1. **ACSD-52160** : corrige le problème où un résultat de validation de produit par rapport à la règle de prix de panier n’a pas été correctement évalué, en fonction de la condition de règle *Si un article est TROUVÉ/NON TROUVÉ dans le panier avec Toutes/L’une de ces conditions est vraie*.
1. **ACSD-51636** : corrige le problème en raison duquel un administrateur ne peut pas ajouter de nouveaux utilisateurs à partir de la section du compte client bien qu’il dispose de tous les rôles et autorisations nécessaires.
1. **ACSD-51739** : corrige le problème où une erreur est renvoyée lorsque l’`structure_id` est demandée dans une demande GraphQL `CompanyTeam`.
1. **ACSD-51857** : correction du problème en raison duquel la lenteur des performances `aggregate_sales_report_bestsellers_data` rapport cron affecte les tables de base de données `sales_order` et `sales_order_item` volumineuses.
1. **ACSD-48448** : corrige le problème d’un problème de condition de concurrence se produisant lors des annulations de commande, ce qui entraîne une entrée dupliquée dans la table *inventory_reservation*.
1. **ACSD-52689** : corrige le problème en raison duquel les images ne peuvent pas être chargées dans le stockage [!DNL Amazon S3] à l’aide de l’API REST.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
