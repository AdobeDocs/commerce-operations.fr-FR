---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.50
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.50.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e136531-6bd4-4294-9a5a-66d19eb136db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.50

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.50.

QPT v1.1.50 comprend les correctifs suivants :

1. **ACSD-59280** : corrige le problème en raison duquel l’erreur *Appel à une méthode non définie ReflectionUnionType::getName()* se produit lors de l’installation des versions 2.4.4-pX.
1. **ACSD-45049** : corrige le problème en raison duquel le paramètre d’attribut de *[!UICONTROL Is required]* du client ne fonctionne pas correctement selon la portée du site web dans Admin.
1. **ACSD-46938** : corrige le problème de performances de la recréation des déclencheurs de base de données lors de l’`setup:upgrade`.
1. **ACSD-48210** : correction du problème en raison duquel la mise à jour de l’attribut *[!UICONTROL website scope]* dans une vue de magasin spécifique remplace les valeurs d’attribut dans la portée globale.
1. **ACSD-54887** : corrige le problème d’effacement du panier client après l’expiration de la session client avec *[!UICONTROL Persistent Shopping Cart]* activé.
1. **ACSD-58141** : corrige le problème en raison duquel `PHPSESSID` se régénère sur les requêtes POST sur la zone de storefront pour un client connecté si le [!UICONTROL L2 Redis cache] est activé et que le client est mis à jour à partir de l’administration.
1. **ACSD-58352** : corrige le problème où les libellés d’attribut de retour pour la vue de magasin par défaut sont renvoyés via l’API GraphQL lorsqu’une vue de magasin autre que la vue par défaut est spécifiée dans l’en-tête de la requête.
1. **ACSD-58442** : corrige le problème où les appareils d’une largeur de *768 px* sont traités comme des appareils mobiles, ce qui entraîne le chargement du menu et de l’en-tête dans une vue mobile au lieu du bureau.
1. **ACSD-58790** : corrige la fonctionnalité *pincer pour zoomer* sur les images de la page des détails du produit en vue mobile sur [!DNL Chrome].
1. **ACSD-59036** : corrige une exception qui se produit lors du chargement des prix des produits avec des limites inférieure et supérieure égales à *$0*.
1. **ACSD-59229** : corrige le problème d’enregistrement des informations relatives au groupe de clients dans un segment incorrect en raison de l’ancienne valeur du [!UICONTROL X-Magento-Vary] dans la requête.
1. **ACSD-59378** : correction d’un problème en raison duquel les réécritures d’URL au niveau du magasin ne sont pas correctement mises à jour lors de l’importation.
1. **ACSD-59514** : corrige le problème de rendu des formulaires dans la zone d’administration avec [!DNL Page Builder] lancez le *[!DNL Page Builder]pendant 5 secondes sans libérer les verrous.* erreur dans la console du navigateur après l’envoi du formulaire et les modifications ne peuvent pas être enregistrées.
1. **ACSD-60303** : corrige le problème en raison duquel une commande de l’administrateur ne peut pas être passée si la minimisation d’HTML est activée.
1. **ACSD-60441** : corrige le problème de mise à jour des clients via `V1/customers REST API` point d’entrée lors de l’utilisation du jeton d’accès à l’intégration généré à partir du serveur principal.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
