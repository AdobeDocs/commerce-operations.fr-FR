---
title: 'Présentation : [!DNL Quality Patches Tool]  (QPT) v1.1.56'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.56.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 88cc3a9b2582998812af196f9e59b93015098c52
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.56

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.56.

QPT v1.1.56 comprend les correctifs suivants :

1. **ACSD-63244** : corrige les problèmes en raison desquels une erreur JavaScript empêche [!DNL Google Maps] d’effectuer correctement le rendu et où il existe de nombreuses *erreurs de type non interceptées : cette erreur._each n&#39;est pas une erreur de fonction* dans la console du panneau [!UICONTROL Admin].
1. **ACSD-63242** : résolution du problème de lenteur de l’importation lors de l’ajout de produits de catalogue avec plus de 10 000 entrées.
1. **ACSD-63062** : corrige le problème en raison duquel des calculs d’escompte de panier incorrects se produisaient lorsque plusieurs règles se chevauchaient.
1. **ACSD-62979** : correction d’un problème en raison duquel l’utilisation de [!UICONTROL Store ID] incorrect dans l’en-tête de GraphQL provoquait une erreur de mémoire fatale.
1. **ACSD-62971** : résolution du problème en raison duquel l’importation de sources de stock avec des valeurs non numériques dans la colonne *[!UICONTROL Quantity]* entraînait la définition de *quantity* sur *0*.
1. **ACSD-62872** : résolution du problème de validation d’attribut unique en raison duquel les mises à jour de planification sont incorrectement validées.
1. **ACSD-62755** : correction d’un problème en raison duquel [!DNL TinyMCE] 7 nécessitait l’ajout spécifique de la taille et de la police dans les paramètres d’initialisation de l’éditeur.
1. **ACSD-62670** : correction d’un problème en raison duquel l’exportation du rapport [!UICONTROL Products Ordered] au format CSV et XML renvoyait une erreur.
1. **ACSD-62577** : corrige le problème de lenteur des performances des requêtes de recherche storefront en optimisant les index de requête et de table.
1. **ACSD-62475** : résolution du problème de fusion incorrecte des produits [!UICONTROL Gift Card] dans le panier.
1. **ACSD-62428** : résolution du problème en raison duquel `is_out_of_stock` est défini sur une valeur incorrecte dans l’index de recherche de catalogue lorsque [!DNL SKU] n’est pas défini comme attribut pouvant faire l’objet d’une recherche.
1. **ACSD-62355** : améliore le temps de chargement de la page de modification du produit configurable lorsque le produit configurable est basé sur de nombreux attributs avec de nombreuses valeurs.
1. **ACSD-61805** : résolution du problème en raison duquel les produits restent en rupture de stock sur le storefront après la mise à jour de l’état de la commande en arrière-plan via [!DNL REST API].
1. **ACSD-60811** : résolution du problème de mise à jour de l’état de la commande avec une valeur ou un commentaire personnalisé uniquement si l’état actuel est *[!UICONTROL Processing]* ou *[!UICONTROL Fraud]*.
1. **ACSD-62952** : correction d’un problème en raison duquel la date [!UICONTROL Gift Registry] s’affichait incorrectement sur le storefront.
1. **ACSD-55339** : correction d’un problème en raison duquel un produit [!DNL SKU] commençant par *0* (zéro) supprimait l’élément *0*, empêchant la mise à jour de la citation.

Utilisez le menu de gauche pour accéder à une page de correctif spécifique.
