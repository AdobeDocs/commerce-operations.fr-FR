---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.57
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.57.
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
source-git-commit: fc5c790108a3c62d4591631128743259824c4c6b
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.57

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.57.

QPT v1.1.57 comprend les correctifs suivants :

1. **ACSD-57570** : corrige le problème en raison duquel un utilisateur administrateur restreint ayant accès à un magasin particulier ne peut pas toujours voir tous les catalogues partagés auxquels les produits sont affectés ou peut voir les clients qui ne peuvent pas les enregistrer, ce qui entraîne des incohérences dans le système.
1. **ACSD-58325** : corrige le problème en raison duquel le bouton [!UICONTROL Import] est disponible même après une erreur de validation.
1. **ACSD-59083** : correction du problème en raison duquel certaines opérations de mise à jour de la base de données entraînent l’erreur _Table ou vue de base introuvable_ si la mise à jour de la [!DNL mview] est exécutée en même temps.
1. **ACSD-61622** : corrige le problème en raison duquel des taux spécifiques au compte [!DNL FedEx] sont manquants dans la réponse. ACSD-61622 remplace le correctif documenté dans [[!DNL FedEx] migration de l’intégration de la méthode d’expédition de [!DNL SOAP] vers [!DNL RESTful API]](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api).
1. **ACSD-61895** : corrige le problème où les catégories [!DNL GraphQL] la requête renvoient des catégories avec l’autorisation *allow* même si la catégorie racine ne dispose pas de l’autorisation *allow*.
1. **ACSD-62212** : corrige le problème en raison duquel le contenu de l’e-mail [!UICONTROL Forgot Password] n’est pas traduit dans la langue de la vue du magasin.
1. **ACSD-62481** : corrige le problème en raison duquel le panier du client est vide même si [!UICONTROL Persistence] est activé.
1. **ACSD-62629** : correction d’un problème en raison duquel une liste de produits utilisée dans [!UICONTROL Widgets] ne respecte pas la condition de catégorie.
1. **ACSD-62635** : corrige le problème d’affichage incorrect des produits associés à plusieurs magasins dans la requête de produit [!DNL GraphQL].
1. **ACSD-62671** : corrige le problème en raison duquel la requête [!DNL GraphQL] ne renvoie pas d’informations d’adresse à jour lors de la première tentative.
1. **ACSD-62689** : corrige le problème en raison duquel le client ne peut pas ajouter de catégories dans [!UICONTROL Related Product Rules] et [!UICONTROL Widgets] après la profondeur 4.
1. **ACSD-62708** : corrige le problème en raison duquel [!DNL TinyMCE] taille de police de l’éditeur 7 dans l’administration affiche [!UICONTROL pt] et non [!UICONTROL px] après l’application du correctif depuis [!UICONTROL ACP2E-3430]. Vous pouvez désormais également définir la taille de police dans [!UICONTROL px] au lieu de [!UICONTROL pt].
1. **ACSD-62758** : corrige le problème en raison duquel les vidéos de produit ne s’affichent pas correctement sur la page des détails du [!UICONTROL Configurable Product] si l’URL contient les options sélectionnées.
1. **ACSD-62951** : corrige le problème d’envoi de l’e-mail [!UICONTROL Credit Memo] sans inclure d’éléments ni de totaux.
1. **ACSD-62965** : corrige le problème en raison duquel un message *LocalizedException* n’est pas inclus dans le [!DNL GraphQL response] d’emplacement de commande.
1. **ACSD-63286** : corrige le problème où les produits affectés à un catalogue partagé via l’API n’apparaissent pas sur le storefront tant qu’une réindexation manuelle n’est pas exécutée.
1. **ACSD-63326** : corrige le problème en raison duquel l’administrateur est redirigé vers une page endommagée après avoir passé une commande sur le serveur principal.


Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
