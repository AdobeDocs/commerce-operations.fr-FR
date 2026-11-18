---
title: 'Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.86'
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.86.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 95a2c8dc890366c96b6a8129e8ee25dd1b319190
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%
---
# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.86

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.86.

QPT v1.1.86 comprend les correctifs suivants :

1. **ACP2E-3094** : correction d’un problème en raison duquel l’affichage ou la modification de **[!UICONTROL Category Permissions]** pour une catégorie dotée de nombreuses autorisations peut empêcher le navigateur de répondre.
1. **ACP2E-5046** : correction d’un problème en raison duquel l’actualisation de la page lors de la création d’une commande dans l’administrateur ajoute le même SKU plusieurs fois.
1. **ACP2E-5050** : correction du problème en raison duquel l’affichage ou l’enregistrement d’une autorisation de retour client dans l’administration n’affichait pas le numéro d’autorisation de retour client dans le rapport **[!UICONTROL Action Logs]**.
1. **ACP2E-5057** : correction du problème en raison duquel les requêtes [!DNL GraphQL] pour les produits groupés renvoient des prix globaux d’option de bundle au lieu de prix spécifiques au site web lorsque **[!UICONTROL Catalog Price Scope]** est défini sur **[!UICONTROL Website]**.
1. **ACP2E-5061** : correction d’un problème en raison duquel une règle de marchandisage de catégorie ne peut pas combiner les conditions `AND` avec une condition correspondant à l’une des valeurs.
1. **ACP2E-5071** : correction d’un problème en raison duquel le message d’indisponibilité du stock n’était pas toujours affiché sur la page du produit lorsque le panier de l’acheteur contenait déjà la quantité disponible complète.
1. **ACP2E-5094** : correction d’un problème en raison duquel le chargement des pages est considérablement plus lent lorsqu’une variable d’environnement `MAGENTO_DC_*` est définie.
1. **ACP2E-5118** : correction du problème en raison duquel l’aperçu [!DNL Page Builder] ne s’affiche pas lorsque le cache **[!UICONTROL Translations]** est désactivé.
1. **ACP2E-5134** : correction d’un problème en raison duquel la suppression du produit composant d’une offre groupée du [!UICONTROL Shared Catalog] d’une entreprise laisse le produit de l’offre groupée dans le panier, provoquant une erreur dans le panier et lors du passage en caisse.
1. **ACP2E-5146** : correction du problème en raison duquel un utilisateur administrateur limité à des sites web spécifiques ne peut pas supprimer des clients lorsqu’un client d’un autre site web possède le même ID que l’utilisateur administrateur.
1. **ACP2E-5176** : correction d’un problème en raison duquel les événements e-commerce envoyés à [!DNL Google Analytics 4] via [!DNL Google Tag Manager] utilisent le format [!DNL Universal Analytics] et omettent plusieurs événements de passage en caisse.
1. **ACP2E-5185** : correction du problème en raison duquel le déplacement d’une catégorie dans l’arborescence des catégories affiche l’erreur `There was a category move error` ou prend plusieurs minutes lorsque le magasin comporte de nombreuses réécritures d’URL.
1. **ACP2E-4191** : correction du problème en raison duquel certaines requêtes de l’API REST entrent en boucle infinie lorsque le cache **[!UICONTROL EAV types and attributes]** est désactivé.
1. **ACP2E-4973** : corrige le problème en raison duquel le passage de **[!UICONTROL In-Store Delivery]** à une autre méthode de diffusion n’efface pas l’adresse de magasin associée du panier.
1. **ACP2E-5221** : correction d’un problème en raison duquel l’indexeur **[!UICONTROL Catalog Product Permissions]** prend beaucoup plus de temps lorsque **[!UICONTROL Quick Order]** est activé dans des installations comportant de nombreux magasins et groupes de clients.
1. **ACP2E-5245** : correction du problème en raison duquel un client nouvellement enregistré qui utilise la même adresse pour l’expédition et la facturation lors de sa première commande voit cette adresse répertoriée deux fois lors de sa prochaine commande.
1. **ACP2E-5248** : correction du problème en raison duquel les utilisateurs administrateurs sans l’autorisation **[!UICONTROL Edit Product Status]** voient l’erreur d’obsolescence `null as array offset` lors de l’ouverture de la page **[!UICONTROL Add Product]** sur [!DNL PHP] 8.5.
1. **ACP2E-5254** : correction du problème en raison duquel les produits ajoutés à une liste de demandes d&#39;approvisionnement n&#39;apparaissent pas lorsqu&#39;un client ouvre la liste tant que le cache n&#39;est pas effacé.
1. **ACP2E-5268** : corrige le problème en raison duquel la création d’un produit configurable échoue lorsque **[!UICONTROL Enable Frontend Resize]** est défini sur **[!UICONTROL No]**.
1. **ACP2E-3752** : correction du problème en raison duquel le traitement de l’importation de produit renvoie l’erreur `Undefined array key "apply_to"` lorsque de nombreuses opérations d’importation de produit sont créées.
1. **ACP2E-5280** : correction d’un problème en raison duquel les clients rencontraient une erreur lors de la connexion lorsque **[!UICONTROL Category Permissions]** était activé.
1. **ACP2E-5295** : correction d’un problème en raison duquel la réindexation parallèle des prix des produits échouait avec l’erreur `Fail in child process` lors de l’exécution après l’indexeur **[!UICONTROL Inventory]** dans le même processus.
1. **ACP2E-5298** : correction du problème en raison duquel les utilisateurs administrateurs ayant un accès en lecture seule aux règles de prix des paniers peuvent générer ou supprimer des codes de coupon.
1. **ACP2E-5333** : correction d’un problème en raison duquel l’actualisation d’un segment client avec une condition **[!UICONTROL Total Number of Orders]** qui utilise l’opérateur **[!UICONTROL is not]** et une valeur d’un ou de plusieurs échoue avec l’erreur `Unknown operator specified`.
1. **ACP2E-5425** : correction du problème en raison duquel les clients reçoivent des e-mails de confirmation de commande en double pour la même commande.

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
