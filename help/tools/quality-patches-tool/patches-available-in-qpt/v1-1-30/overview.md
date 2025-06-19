---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.30
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.30.
feature: Tools and External Services
role: Admin
exl-id: 36c6e0cc-fd8c-4583-b147-fe4897b101d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.30

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.30.

QPT v1.1.30 comprend les correctifs suivants :

1. **ACSD-50336** : corrige le problème en raison duquel les e-mails d’alerte de produit ne sont pas envoyés lorsqu’un produit est de nouveau en stock ou que le prix est modifié.
1. **ACSD-50367** : corrige le problème en raison duquel l’exportation de l’adresse du client ne fonctionne pas lorsqu’un attribut d’adresse du client à sélection multiple sans valeurs est créé.
1. **ACSD-49877** : corrige le problème en raison duquel la lecture automatique de la vidéo ne fonctionne pas sur les [!DNL Safari] mobiles lorsque la vidéo est directement liée à un fichier vidéo distant et non à un service de streaming.
1. **ACSD-50165** : corrige l’erreur *Le fichier ne peut pas être supprimé. Avertissement!unlink: aucun fichier ou répertoire de ce type lors du vidage du cache JS/CSS de l&#39;administrateur*.
1. **ACSD-49737** : correction d’un problème en raison duquel un coupon est incorrectement marqué comme utilisé après un échec de paiement par carte.
1. **ACSD-50814** : corrige le problème en raison duquel un utilisateur administrateur n’est pas en mesure de créer un avoir.
1. **ACSD-50116** : corrige le problème en raison duquel un utilisateur administrateur ne peut pas créer de réécriture d’URL pour les sous-catégories de niveau 3 ou inférieur.
1. **ACSD-49513** : corrige le problème d’échec de la synchronisation du stockage distant en raison de fichiers de 0 octet.
1. **ACSD-46683** : corrige le problème en raison duquel le prix d’expédition indique *Pas encore calculé*.
1. **ACSD-49129** : corrige le problème en raison duquel l’attribut de contenu ([!UICONTROL base64 image code]) n’est pas renvoyé dans les réponses de l’API des médias du produit `rest/V1/products/sku/media`.
1. **ACSD-50276** : corrige le problème en raison duquel le formulaire d’enregistrement du client ne fonctionne pas sur le storefront si un attribut du client à sélection multiple est créé.
1. **ACSD-50527** : corrige l’erreur qui se produit lors de l’enregistrement d’une page avec un bloc dynamique vide.
1. **ACSD-49973** : améliore les performances de récupération des produits groupés via GraphQL.
1. **ACSD-51114** : corrige le problème où un produit aléatoire disparaît des catalogues volumineux lorsque l’indexation asynchrone est activée. Amélioration des performances de la réindexation asynchrone pour les catalogues volumineux.
1. **B2B-2598** : ajoute une fonctionnalité de mise en cache aux requêtes `availableStores`, `countries`, `country`, `currency` et `storeConfig` GraphQL.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
