---
title: Exemple avec une configuration partagée
description: Consultez un exemple de modification des paramètres dans un système de développement avec un fichier de configuration partagé.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Exemple avec une configuration partagée

Cet exemple montre comment modifier les paramètres suivants dans votre système de développement, mettre à jour le fichier de configuration partagé, `config.php`, dans votre système de génération et implémenter les mêmes paramètres dans votre système de production :

- Fuseau horaire
- Unité de poids

Ces paramètres sont disponibles dans Admin dans **Magasins** > Paramètres > **Configuration** > Général > **Général**.

Vous pouvez utiliser la même procédure pour configurer des paramètres non sensibles et non spécifiques au système dans les références suivantes :

- [Référence des autres chemins de configuration](../reference/config-reference-general.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence des chemins de configuration de l’extension B2B d’entreprise Commerce](../reference/config-reference-b2b.md)

## Avant de commencer

Avant de commencer, configurez les autorisations et la propriété du système de fichiers comme décrit dans la section [Conditions préalables pour les systèmes de développement, de création et de production](../deployment/prerequisites.md).

## Hypothèses

Cette rubrique fournit un exemple de modification de la configuration du système d’exploitation. Vous pouvez choisir différentes options de configuration si vous le souhaitez.

Pour les besoins de cet exemple, nous supposons que :

- Vous utilisez le contrôle de code source Git.
- Le système de développement est disponible dans un référentiel distant Git nommé `mconfig`
- Votre branche de travail Git est nommée `m2.2_deploy`

## Étape 1 : définir la configuration dans le système de développement

Pour définir le fuseau horaire et les unités de poids dans votre système de développement :

1. Connectez-vous à l’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Dans le volet de droite, développez **Options locales**.

   La figure suivante en est un exemple.

   ![Définir des options de paramètres régionaux dans le système de développement](../../assets/configuration/split-deploy-set-locale.png)

1. Dans la liste **Fuseau horaire**, cliquez sur **GMT+00:00 (UTC)**.
1. Désélectionnez la case **Utiliser la valeur système** située en regard du champ **Unité de poids**.
1. Dans la liste **Unité de poids**, cliquez sur **kg**.
1. Cliquez sur **Enregistrer la configuration**.
1. Si vous y êtes invité, videz le cache.

## Étape 2 : mettre à jour la configuration partagée

Générez le fichier de configuration partagé, `app/etc/config.php`, dans votre système de développement et transférez-le à l’aide du contrôle de code source vers votre système de génération, comme indiqué dans cette section.

{{$include /help/_includes/config-save-config.md}}

## Étape 3 : mettre à jour votre système de génération et générer des fichiers

Maintenant que vous avez validé vos modifications de la configuration partagée dans le contrôle de code source, vous pouvez extraire ces modifications dans votre système de génération, compiler le code et générer des fichiers statiques. La dernière étape consiste à apporter ces modifications à votre système de production. Par conséquent, la configuration de votre système de production correspond à votre système de développement.

{{$include /help/_includes/config-update-build-system.md}}

## Etape 4 : Mise à jour du système d&#39;exploitation

La dernière étape du processus consiste à mettre à jour votre système de production à partir du contrôle de code source. Cela extrait toutes les modifications que vous avez apportées à vos systèmes de développement et de création, ce qui signifie que votre système de production est complètement à jour.

{{$include /help/_includes/config-update-prod-system.md}}

### Vérifier les modifications dans l’administrateur

**Pour vérifier que ces paramètres ne sont pas modifiables dans l’administration** :

1. Connectez-vous à l’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Dans le volet de droite, développez **Options locales**.

   Les options que vous venez de définir s’affichent comme suit :

   ![Les options de configuration ne peuvent pas être modifiées dans l’administration](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Pour modifier un paramètre verrouillé dans Admin, utilisez la commande [`magento config:set --lock`](../cli/set-configuration-values.md).
