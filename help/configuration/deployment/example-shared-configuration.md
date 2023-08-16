---
title: Exemple d'utilisation d'une configuration partagée
description: Consultez un exemple de modification des paramètres dans un système de développement avec un fichier de configuration partagé.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Exemple d&#39;utilisation d&#39;une configuration partagée

Cet exemple montre comment modifier les paramètres suivants de votre système de développement, mettre à jour le fichier de configuration partagé, `config.php`, dans votre système de génération, et implémentez les mêmes paramètres dans votre système de production :

- Fuseau horaire
- Unité de poids

Ces paramètres sont disponibles dans la section Admin de **Magasins** > Paramètres > **Configuration** > Général > **Général**.

Vous pouvez suivre la même procédure pour configurer des paramètres qui ne sont pas sensibles et qui ne sont pas spécifiques au système dans les références suivantes :

- [Autres références de chemins de configuration](../reference/config-reference-general.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence sur les chemins de configuration de l’extension B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

## Avant de commencer

Avant de commencer, configurez les autorisations et la propriété du système de fichiers, comme décrit dans la section [Conditions préalables pour les systèmes de développement, de génération et de production](../deployment/prerequisites.md).

## Hypothèses

Cette rubrique fournit un exemple de modification de la configuration du système de production. Si vous le souhaitez, vous pouvez choisir différentes options de configuration.

Pour les besoins de cet exemple, nous supposons que :

- Vous utilisez le contrôle source Git
- Le système de développement est disponible dans un référentiel distant Git nommé `mconfig`
- Votre branche de travail Git est nommée `m2.2_deploy`

## Étape 1 : définir la configuration dans le système de développement

Pour définir le fuseau horaire et les unités de poids dans votre système de développement :

1. Connectez-vous à l’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Dans le volet de droite, développez **Options de paramètres régionaux**.

   La figure suivante illustre un exemple.

   ![Définition des options de paramètres régionaux dans le système de développement](../../assets/configuration/split-deploy-set-locale.png)

1. Dans la **Fuseau horaire** liste, cliquez sur **GMT+00:00 (UTC)**.
1. Effacez la variable **Utiliser la valeur système** en regard de la case **Unité de poids** champ .
1. Dans la **Unité de poids** liste, cliquez sur **kgs**.
1. Cliquez sur **Enregistrer la configuration**.
1. Si vous y êtes invité, videz le cache.

## Étape 2 : mise à jour de la configuration partagée

Générer le fichier de configuration partagé, `app/etc/config.php`, dans votre système de développement et transférez-le à l’aide du contrôle de code source vers votre système de génération, comme indiqué dans cette section.

{{$include /help/_includes/config-save-config.md}}

## Étape 3 : Mettre à jour votre système de génération et générer des fichiers

Maintenant que vous avez validé vos modifications dans la configuration partagée pour le contrôle de code source, vous pouvez extraire ces modifications dans votre système de création, compiler du code et générer des fichiers statiques. La dernière étape consiste à extraire ces modifications dans votre système de production. Par conséquent, la configuration de votre système de production correspond à votre système de développement.

{{$include /help/_includes/config-update-build-system.md}}

## Étape 4 : mise à jour du système de production

La dernière étape du processus consiste à mettre à jour votre système de production à partir du contrôle source. Cela récupère toutes les modifications que vous avez apportées à vos systèmes de développement et de création, ce qui signifie que votre système de production est entièrement à jour.

{{$include /help/_includes/config-update-prod-system.md}}

### Vérification des modifications dans l’administrateur

**Pour vérifier que ces paramètres ne sont pas modifiables dans l’Admin**:

1. Connectez-vous à l’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Dans le volet de droite, développez **Options de paramètres régionaux**.

   Les options que vous venez de définir s’affichent comme suit :

   ![Options de configuration non modifiables dans l’administrateur](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Pour modifier un paramètre verrouillé dans l’administrateur, utilisez la variable [`magento config:set --lock` command](../cli/set-configuration-values.md).
