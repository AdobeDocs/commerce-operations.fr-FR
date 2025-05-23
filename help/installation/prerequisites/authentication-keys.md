---
title: Obtention des clés d’authentification
description: Suivez ces étapes pour récupérer les informations d’identification afin d’accéder aux modules du compositeur d’Adobe Commerce sur repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Obtention des clés d’authentification

Le référentiel `repo.magento.com` est l’emplacement où les modules Adobe Commerce et le compositeur tiers sont stockés et nécessitent une authentification. Utilisez votre compte de Commerce Marketplace pour générer une paire de *clés d&#39;authentification* de 32 caractères afin d&#39;accéder au référentiel.

Pour pouvoir accéder aux packages Adobe Commerce, vous devez utiliser les clés associées à un MAGEID auquel l’accès à ces packages a été accordé. Le MAGEID est généralement le contact par Principal sur le compte Adobe Commerce et peut ne pas toujours être le propriétaire du projet Adobe Commerce sur le projet d’infrastructure cloud.

>[!TIP]
>
>Si vous rencontrez des [erreurs](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=fr), vous ne disposez peut-être pas d’une autorisation d’accès au package ou le droit d’accès a expiré en raison d’une facture en attente sur votre compte.
>
>* Si vous êtes la personne Contact Principal sur le compte, vérifiez qu&#39;il n&#39;y a aucune facture en suspens répertoriée sur le compte.
>* Si les clés fournies par le contact de Principal ne fonctionnent pas et qu’il n’y a aucune facture en suspens sur le compte, le contact de Principal doit contacter l’[assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=fr#submit-ticket) pour obtenir de l’aide.

Pour créer des clés d’authentification :

1. Connectez-vous au [Commerce Marketplace](https://commercemarketplace.adobe.com/). Si vous n&#39;avez pas de compte, cliquez sur **Enregistrer**.

1. Cliquez sur le nom de votre compte en haut à droite de la page et sélectionnez **Mon profil**.

1. Cliquez sur **Accéder aux clés** dans l’onglet Marketplace.

   ![Obtenir vos clés d’accès sécurisées sur le Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Cliquez sur **Créer une clé d’accès**. Saisissez un nom spécifique pour les clés (par exemple, le nom du développeur recevant les clés) et cliquez sur **OK**.

1. De nouvelles clés publiques et privées sont désormais associées à votre compte, sur lesquelles vous pouvez cliquer pour les copier. Enregistrez ces informations ou gardez la page ouverte lorsque vous utilisez votre projet. Utilisez la **clé publique** comme nom d’utilisateur et la **clé privée** comme mot de passe.

## Gestion des clés d’authentification

Vous pouvez également désactiver ou supprimer des clés d’authentification. Par exemple, vous pouvez désactiver ou supprimer des clés pour des raisons de sécurité une fois qu’une personne a quitté votre entreprise.

* Pour désactiver les clés : cliquez sur **Désactiver**. Vous pouvez le faire si vous souhaitez suspendre l’utilisation de vos clés.
* Pour activer une clé précédemment désactivée : cliquez sur **Activer**.
* Pour supprimer des clés : cliquez sur **Supprimer**.

### Gestion du jeton d’accès SSH

Pour télécharger des versions Adobe Commerce à l’aide de SSH, vous devez générer un jeton d’accès aux téléchargements. Pour générer un jeton :

1. Connectez-vous à votre [compte magento.com](https://account.magento.com/customer/account/login).
1. Cliquez sur **Mon compte** en haut de la page.
1. Cliquez sur **Paramètres du compte** > **Télécharge le jeton d’accès**.

   ![Accéder à vos clés](../../assets/installation/connect_keys1.png)

1. Cliquez sur **Générer un nouveau jeton** pour remplacer et désactiver un jeton existant.

Vous devez utiliser votre MAGEID ainsi que votre jeton pour télécharger une version. Votre MAGEID s’affiche en haut à gauche de la page de votre compte.

Par exemple :

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilisez vos clés d’authentification pour :

* [Obtention du métappackage (intégrateurs, Packagers)](../composer.md)
* [Cloner le référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (développeurs contribuant uniquement)
* [Mettre à niveau et gérer les modules](../../upgrade/modules/upgrade.md)
