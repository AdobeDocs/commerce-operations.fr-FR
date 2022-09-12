---
title: Obtention des clés d’authentification
description: Suivez ces étapes pour récupérer les informations d’identification afin d’accéder aux packages Adobe Commerce et Magento Open Source Composer sur repo.magento.com.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Obtention des clés d’authentification

Le `repo.magento.com` est l’emplacement où les modules Adobe Commerce, Magento Open Source et tiers Composer sont stockés et nécessitent une authentification. Utilisez votre compte de Commerce Marketplace pour générer une paire de 32 caractères. *clés d’authentification* pour accéder au référentiel.

>[!NOTE]
>
>Pour pouvoir accéder aux packages Adobe Commerce et Magento Open Source, vous devez utiliser les clés associées à un MAGEID auquel l’accès à ces packages a été accordé. Le MAGEID correspond généralement à la variable **Contact de facturation** sur le compte Adobe Commerce et ne peut pas toujours être le **Propriétaire du projet** du projet d’infrastructure cloud Adobe Commerce. Si vous rencontrez [errors](https://support.magento.com/hc/en-us/articles/360040296392), vous ne disposez peut-être pas d’une autorisation d’accès au kit ou le droit d’accès a expiré en raison d’une facture en souffrance sur le compte. Contact [Prise en charge d’Adobe Commerce](https://support.magento.com/hc/en-us) pour obtenir de l’aide sur votre MAGEID.

Pour créer des clés d’authentification :

1. Connectez-vous au [Commerce Marketplace](https://marketplace.magento.com). Si vous ne disposez pas d’un compte, cliquez sur **Enregistrer**.
1. Cliquez sur le nom de votre compte en haut à droite de la page, puis sélectionnez **Mon profil**.

1. Cliquez sur **Accéder aux clés** dans l’onglet Marketplace .

   ![Obtention de vos clés d’accès sécurisées sur Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Cliquez sur **Création d’une clé d’accès**. Saisissez un nom spécifique pour les clés (par exemple, le nom du développeur recevant les clés) et cliquez sur **OK**.

1. De nouvelles clés publiques et privées sont désormais associées à votre compte, sur lesquelles vous pouvez cliquer pour les copier. Enregistrez ces informations ou gardez la page ouverte lorsque vous utilisez votre projet. Utilisez la variable **Clé publique** comme votre nom d’utilisateur et le **Clé privée** comme votre mot de passe.

## Gestion des clés d’authentification

Vous pouvez également désactiver ou supprimer des clés d’authentification. Par exemple, vous pouvez désactiver ou supprimer des clés pour des raisons de sécurité une fois qu’une personne a quitté votre entreprise.

* Pour désactiver les clés : Cliquez sur **Désactiver**. Vous pouvez le faire si vous souhaitez suspendre l’utilisation de vos clés.
* Pour activer une clé précédemment désactivée : Cliquez sur **Activer**.
* Pour supprimer des clés : Cliquez sur **Supprimer**.

### Gestion du jeton d’accès SSH

Pour télécharger des versions Adobe Commerce à l’aide de SSH, vous devez générer un jeton d’accès aux téléchargements. Pour générer un jeton :

1. Connectez-vous à [compte magento.com](https://account.magento.com/customer/account/login).
1. Cliquez sur **Mon compte** en haut de la page.
1. Cliquez sur **Paramètres du compte** > **Téléchargements du jeton d’accès**.

   ![Accès à vos clés](../../assets/installation/connect_keys1.png)

1. Cliquez sur **Générer un nouveau jeton** pour remplacer et désactiver un jeton existant.

Vous devez utiliser votre MAGEID ainsi que votre jeton pour télécharger une version. Votre MAGEID s’affiche en haut à gauche de la page de votre compte.

Par exemple :

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilisez vos clés d’authentification pour :

* [Obtention du métappackage (intégrateurs, Packagers)](../composer.md)
* [Clonage du référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (développeurs contributeurs uniquement)
* [Mettre à niveau et gérer les modules](../../upgrade/modules/upgrade.md)
