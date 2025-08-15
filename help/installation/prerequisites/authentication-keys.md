---
title: Obtention de vos clés d’authentification
description: Pour récupérer les informations d’identification et accéder aux packages du compositeur Adobe Commerce sur repo.magento.com, procédez comme suit.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Obtention de vos clés d’authentification

Le référentiel `repo.magento.com` est l’emplacement de stockage des packages de compositeurs Adobe Commerce et tiers, qui nécessitent une authentification. Utilisez votre compte Commerce Marketplace pour générer une paire de *clés d’authentification* de 32 caractères afin d’accéder au référentiel.

Pour obtenir le droit d’accès aux packages Adobe Commerce, vous devez utiliser les clés associées à un MAGEID ayant obtenu l’accès à ces packages. Le MAGEID est généralement le contact par Principal sur le compte Adobe Commerce et peut ne pas toujours être le propriétaire du projet d’infrastructure Adobe Commerce sur le cloud.

>[!TIP]
>
>Si vous rencontrez des [erreurs](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), il se peut que vous n’ayez pas l’autorisation d’accéder au package ou que le droit d’accès ait expiré en raison d’une facture en suspens sur votre compte.
>
>* Si vous êtes la personne de contact de Principal sur le compte, assurez-vous qu&#39;aucune facture en souffrance n&#39;est répertoriée sur le compte.
>* Si les clés fournies par le contact de Principal ne fonctionnent pas et qu&#39;il n&#39;y a aucune facture en suspens sur le compte, le contact de Principal doit contacter [l&#39;assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour obtenir de l&#39;aide.

Pour créer des clés d’authentification :

1. Connectez-vous à [Commerce Marketplace](https://commercemarketplace.adobe.com/). Si vous n’avez pas de compte, cliquez sur **S’inscrire**.

1. Cliquez sur le nom de votre compte en haut à droite de la page et sélectionnez **Mon profil**.

1. Cliquez sur **Clés d’accès** dans l’onglet Marketplace.

   ![Obtention de vos clés d’accès sécurisées sur Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Cliquez sur **Créer une clé d’accès**. Saisissez un nom spécifique pour les clés (par exemple, le nom du développeur qui reçoit les clés) et cliquez sur **OK**.

1. De nouvelles clés publiques et privées sont désormais associées à votre compte, sur lequel vous pouvez cliquer pour les copier. Enregistrez ces informations ou gardez la page ouverte lorsque vous travaillez avec votre projet. Utilisez la **clé publique** comme nom d’utilisateur et la **clé privée** comme mot de passe.

## Gestion des clés d’authentification

Vous pouvez également désactiver ou supprimer des clés d’authentification. Par exemple, vous pouvez désactiver ou supprimer des clés pour des raisons de sécurité après le départ d’une personne de votre organisation.

* Pour désactiver les clés : cliquez sur **Désactiver**. Vous pouvez le faire si vous souhaitez suspendre l’utilisation de vos clés.
* Pour activer une clé désactivée précédemment : cliquez sur **Activer**.
* Pour supprimer des clés : cliquez sur **Supprimer**.

### Gérer le jeton d’accès SSH

Pour télécharger les versions d’Adobe Commerce à l’aide de SSH, vous devez générer un jeton d’accès aux téléchargements. Pour générer un jeton :

1. Connectez-vous à votre compte [magento.com](https://account.magento.com/customer/account/login).
1. Cliquez sur **Mon compte** en haut de la page.
1. Cliquez sur **Paramètres du compte** > **Télécharge le jeton d’accès**.

   ![Accéder à vos clés](../../assets/installation/connect_keys1.png)

1. Cliquez sur **Générer un nouveau jeton** pour remplacer et désactiver un jeton existant.

Vous devez utiliser votre MAGEID ainsi que votre jeton pour télécharger une version. Votre MAGEID est affiché en haut à gauche de la page de votre compte.

Par exemple :

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilisez vos clés d’authentification pour :

* [Obtenir le métapaquet (intégrateurs, packages)](../composer.md)
* [Cloner le référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (développeurs et développeuses contributeurs uniquement)
* [Mise à niveau et gestion des modules](../../upgrade/modules/upgrade.md)
