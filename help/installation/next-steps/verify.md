---
title: Vérification de l’installation
description: Suivez ces étapes pour confirmer que votre installation Adobe Commerce ou Magento Open Source sur site a réussi.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '259'
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

Si la page n’affiche pas de styles, reportez-vous à la section [dépannage](https://support.magento.com/hc/en-us/articles/360032994352).

Si vous obtenez une erreur 404 (Introuvable) similaire à ce qui suit, reportez-vous à la section [Erreur de version PHP ou 404 lors de l’accès à Adobe Commerce dans le navigateur](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
