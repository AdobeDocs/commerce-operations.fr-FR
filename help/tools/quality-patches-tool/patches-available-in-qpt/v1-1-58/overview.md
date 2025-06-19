---
title: Présentation de  [!DNL Quality Patches Tool] (QPT) v1.1.58
description: Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans  [!DNL Quality Patches Tool] (QPT) v1.1.58.
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Présentation : [!DNL Quality Patches Tool] (QPT) v1.1.58

Cette sous-section fournit une description détaillée des problèmes résolus par les correctifs disponibles dans [!DNL Quality Patches Tool] (QPT) v1.1.58.

QPT v1.1.58 comprend les correctifs suivants :

1. **ACSD-48570** : corrige le problème en raison duquel la page de réinitialisation du mot de passe n’était pas accessible en cliquant sur le lien [!UICONTROL Admin] réinitialiser le mot de passe lorsque **Ajouter le code de magasin aux URL** était *activé*, ce qui entraînait auparavant l’affichage de la page de connexion ou d’une page 404.
1. **ACSD-62118** : correction du problème en raison duquel la table `sales_order_tax_item` n&#39;est pas entièrement mise à jour lorsque des commandes [!DNL B2B] sont passées à l&#39;aide de la méthode Bon de commande.
1. **ACSD-63067** : corrige le problème en raison duquel toutes les quantités de produits sont incorrectement mises en surbrillance et le message *[!DNL Please specify the quantity of product(s).]* s’affiche pour tous les produits d’un produit regroupé lorsqu’une seule quantité est incorrecte.
1. **ACSD-63090** : permet de résoudre le problème de suppression des articles du panier lors de la suppression d’un produit après son ajout au panier.
1. **ACSD-63182** : corrige le problème où une erreur se produit lors de l’enregistrement d’un produit groupé dupliqué avec **[!DNL MSI]** *activé*.
1. **ACSD-63283** : corrige le problème en raison duquel la commande d’articles dans le registre des cadeaux provoque une exception et en raison duquel les mises à jour du registre des cadeaux incluent des articles qui n’appartiennent pas au registre.
1. **ACSD-63299** : corrige le problème en raison duquel le prix spécial d&#39;un produit configurable ne s&#39;affiche pas sur le storefront.
1. **ACSD-63325** : corrige le problème d’erreur `Syntax Error: Unexpected <EOF>` lors de l’envoi d’une demande de [!DNL GraphQL] vide.
1. **ACSD-63329** : corrige le problème en raison duquel les valeurs par défaut des attributs dotés de types d’entrée **[!UICONTROL Date]** ou **[!UICONTROL Date and Time]** ne sont pas définies lors de la création de produits via l’[!DNL REST API].
1. **ACSD-63572** : corrige le problème en raison duquel les tables temporaires de l’indexeur `CatalogRule` ne sont pas nettoyées si le processus de l’indexeur est arrêté.
1. **ACSD-63578** : corrige le problème en raison duquel le fait de cliquer sur le bouton **[!UICONTROL Delete]** en **[!UICONTROL Add to Order by SKU]** dans le [!UICONTROL Admin] ne supprime pas le [!DNL SKU].

Utilisez le menu à gauche pour accéder à une page de correctif spécifique.
