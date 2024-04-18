---
title: Vérification de l’installation
description: Suivez ces étapes pour confirmer que votre installation Adobe Commerce sur site a réussi.
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Vérification de l’installation

Accédez au storefront dans un navigateur web. Par exemple, si l’URL de base de l’installation est `http://www.example.com`, saisissez-le dans la barre d’adresse ou d’emplacement de votre navigateur.

La figure suivante présente un exemple de page de storefront. S’il s’affiche comme suit, votre installation a réussi !

![Storefront avec le thème Luma](../../assets/installation/install-success_store-luma.png)

## Vérification du storefront (pas de données d’exemple)

Accédez au storefront dans un navigateur web. Par exemple, si l’URL de base de l’installation est `http://www.example.com`, saisissez-le dans la barre d’adresse ou d’emplacement de votre navigateur.

La figure suivante présente un exemple de page de storefront. S’il s’affiche comme suit, votre installation a réussi !

![Storefront qui vérifie une installation réussie](../../assets/installation/install-success_store.png)

Si la page affiche une `404 (Not Found)` ou n’affiche pas de styles, voir [dépannage](https://support.magento.com/hc/en-us/articles/360032994352).

## Vérification de l’administrateur

Accédez à l’ administrateur dans un navigateur web. Par exemple, si l’URL de base de l’installation est `http://www.example.com`, et l’URI d’administration est `admin_au1nT`, saisissez `http://www.example.com/admin_au1nT` dans la barre d’adresse ou d’emplacement de votre navigateur.

(L’URI d’administration est spécifié par la valeur de la variable `backend-frontname` paramètre d’installation.)

Lorsque vous y êtes invité, connectez-vous en tant qu’administrateur.

La figure suivante illustre un exemple de page d’administration. S’il s’affiche comme suit, votre installation a réussi !

![Administrateur qui vérifie une installation réussie](../../assets/installation/install_success_admin.png)

Si la page n’affiche pas de styles, voir [dépannage](https://support.magento.com/hc/en-us/articles/360032994352).

Si vous obtenez une erreur 404 (Introuvable) similaire à ce qui suit, voir [Erreur de version PHP ou 404 lors de l’accès à Adobe Commerce dans le navigateur](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
