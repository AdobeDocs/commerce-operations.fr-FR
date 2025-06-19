---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.42
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.42

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 comprend les correctifs suivants :

1. **ACSD-53658** : corrige le problème en raison duquel les données de produit *[!UICONTROL Recently Viewed]* ne sont pas correctement mises à jour dans la vue du magasin.
1. **ACSD-54626** : corrige le problème en raison duquel vous ne pouvez pas créer de règle de bon de commande (`createPurchaseOrderApprovalRule`) avec l’attribut `NUMBER_OF_SKUS` via GraphQL.
1. **ACSD-53845** : corrige le problème de délai d’expiration de la connexion MySQL lorsque `consumer max_messages` = 0.
1. **ACSD-54890** : corrige le problème d’`aggregate_sales_report_bestsellers_data` des erreurs MySQL dues au manque d’espace `/tmp` disque.
1. **ACSD-55112** : corrige le problème en raison duquel il est possible de cliquer plusieurs fois sur le bouton *[!UICONTROL Submit review]* sans validation [!DNL Google reCAPTCHA v3].
1. **ACSD-54264** : corrige le problème en raison duquel le message d’erreur *Vous ne pouvez pas mettre à jour l’attribut demandé. ID de ligne : store_id* s’affiche lorsqu’un client tente de passer en caisse avec un devis négociable provenant d’une autre vue de magasin.
1. **ACSD-54418** : correction d’un problème en raison duquel un montant fixe de remise est incorrectement appliqué à chaque produit enfant du lot à prix dynamiques.
1. **ACSD-55238** : corrige le problème d’enregistrement de la méta-description vide du produit.
1. **ACSD-54966** : correction d’un problème en raison duquel un code de coupon à utilisation limitée par client ne peut pas être réutilisé en cas d’échec de la commande précédente.
1. **ACSD-54060** : corrige le problème en raison duquel un administrateur restreint ne peut pas enregistrer un produit s’il est l’enfant d’un autre produit affecté à une portée différente.
1. **ACSD-48910** : permet de résoudre le problème de rupture de stock d’un produit groupé affecté à plusieurs sources après la facturation et l’expédition d’une commande, même si la quantité n’est pas nulle.
1. **ACSD-55381** : corrige une erreur de serveur interne lors de l’interrogation de champs `configurable_product_option_uid` et `configurable_product_option_value_uid` à partir d’un *[!UICONTROL Requisition list]* B2B via GraphQL.
1. **ACSD-55628** : correctif pour le téléchargement d’un fichier sur le formulaire d’enregistrement de l’entreprise et le remplacement d’un fichier pour un attribut du client sur le storefront.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
