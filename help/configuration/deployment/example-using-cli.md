---
title: Exemple d’utilisation de commandes d’interface de ligne de commande
description: Consultez un exemple de définition de valeurs partagées, spécifiques au système et sensibles dans votre système de développement à l’aide de la ligne de commande.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Exemple d’utilisation de commandes d’interface de ligne de commande

Cet exemple montre comment définir des valeurs partagées, spécifiques au système et sensibles dans votre système de développement, puis déployer ces valeurs sur votre système de production.
Pour ce faire, utilisez une combinaison de configurations partagées, du fichier `config.php` et de la commande de l’interface de ligne de commande Commerce.

Cet exemple utilise les paramètres de configuration suivants :

- **Numéro de TVA** et **Nom de la boutique** pour les paramètres de configuration partagés.

  Vous les trouverez sous **Magasins** > Paramètres > **Configuration** > Général > **Général**.

- **Envoyer des e-mails à** pour la valeur de configuration sensible.

  Elle se trouve sous **Magasins** > Paramètres > **Configuration** > Général > **Contacts**.

- **Domaine d’e-mail par défaut** pour la valeur de configuration spécifique au système.

  Elle se trouve sous **Magasins** > Paramètres > **Configuration** > Clients > **Configuration du client** > **Options de création de compte**.

Vous pouvez utiliser la même procédure que celle illustrée dans cet exemple pour configurer des paramètres dans les références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence des autres chemins de configuration](../reference/config-reference-general.md)
- [Référence des chemins de configuration de l’extension B2B d’entreprise Commerce](../reference/config-reference-b2b.md)

## Avant de commencer

Avant de commencer, configurez les autorisations et la propriété du système de fichiers, comme indiqué dans la section [Conditions préalables au développement, à la création et aux systèmes de production](../deployment/prerequisites.md).

## Hypothèses

Cette rubrique fournit un exemple de modification de la configuration du système d’exploitation. Vous pouvez choisir différentes options de configuration si vous le souhaitez.

Pour les besoins de cet exemple, nous supposons que :

- Vous utilisez le contrôle de code source Git.
- Le système de développement est disponible dans un référentiel distant Git nommé `mconfig`
- Votre branche de travail Git est nommée `m2.2_deploy`

## Étape 1 : définir la configuration dans le système de développement

Pour définir les paramètres régionaux et les unités de poids par défaut dans votre système de développement :

1. Connectez-vous à l’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Si plusieurs sites web sont disponibles, utilisez la liste **Affichage de la boutique** située dans le coin supérieur gauche pour passer à un autre site web, comme le montre l’illustration suivante.

   ![Changer de site web](../../assets/configuration/split-deploy-switch-website.png)

1. Dans le volet de droite, développez **Informations du magasin**.
1. Si nécessaire, décochez la case **Utiliser la valeur par défaut** en regard des champs **Numéro de TVA** et **Nom de la boutique**.
1. Saisissez un nombre dans le champ (par exemple, `12345`).
1. Dans le champ **Nom de la boutique**, saisissez une valeur (comme `My Store`).
1. Cliquez sur **Enregistrer la configuration**.
1. Dans le volet de navigation de gauche, sous Général, cliquez sur **Contacts**.
1. Dans le volet de droite, développez **Options de messagerie**.
1. Si nécessaire, décochez la case **Utiliser la valeur par défaut** en regard du champ **Envoyer des e-mails à**.
1. Saisissez une adresse e-mail dans le champ.
1. Cliquez sur **Enregistrer la configuration**.
1. Utilisez la liste **Affichage de la boutique** pour sélectionner la configuration **par défaut** comme le montre la figure suivante.

   ![Passer à la configuration par défaut](../../assets/configuration/split-deploy-default-config.png)

1. Dans le volet de gauche, cliquez sur Clients > **Configuration du client**.
1. Dans le volet de droite, développez **Options de création de compte**.
1. Si nécessaire, décochez la case **Utiliser la valeur système** en regard du champ **Domaine d’e-mail par défaut**.
1. Saisissez un nom de domaine dans le champ .
1. Cliquez sur **Enregistrer la configuration**.
1. Si vous y êtes invité, videz le cache.

## Étape 2 : mettre à jour la configuration

Maintenant que vous avez modifié la configuration dans l’administration, écrivez la configuration partagée dans un fichier en procédant comme suit :

{{$include /help/_includes/config-save-config.md}}

Même si `app/etc/env.php` (la configuration spécifique au système) a été mise à jour, ne l’archivez pas dans le contrôle de code source.
Vous allez créer les mêmes paramètres de configuration sur votre système d’exploitation plus loin dans cette procédure.

## Étape 3 : mettre à jour votre système de génération et générer des fichiers

Maintenant que vous avez validé vos modifications de la configuration partagée dans le contrôle de code source, vous pouvez extraire ces modifications dans votre système de build, compiler le code et générer des fichiers statiques.

{{$include /help/_includes/config-update-build-system.md}}

## Etape 4 : Mise à jour du système d&#39;exploitation

La dernière étape du processus consiste à mettre à jour votre système de production. Vous devez le faire en deux parties :

- Mettre à jour les paramètres sensibles et spécifiques au système
- Mettre à jour les paramètres partagés

### Mettre à jour les paramètres sensibles et spécifiques au système

Pour définir les paramètres sensibles et spécifiques au système à l’aide de variables d’environnement, vous devez connaître les éléments suivants :

- Portée de chaque paramètre

  Si vous avez suivi les instructions de l’étape 1, la portée de l’option **Envoyer des e-mails à** est celle du site web et celle de l’option **Domaine d’e-mail par défaut** est globale (c’est-à-dire la portée de la configuration par défaut).

  Vous avez besoin du code du site web pour définir la valeur de configuration **Envoyer des e-mails à**.

  Pour plus d’informations sur la recherche de cette valeur, voir : [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables).

- Chemins de configuration des paramètres utilisés dans cet exemple :

  | Nom du paramètre | Chemin de configuration |
  | -------------------- | -------------------------------------- |
  | Envoyer Des E-Mails À | `contact/email/recipient_email` |
  | Domaine d’e-mail par défaut | `customer/create_account/email_domain` |

  Pour tous les chemins de configuration sensibles et spécifiques au système, voir : [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md).

### Définition des variables à l’aide de commandes d’interface de ligne de commande

Utilisez les commandes d’interface de ligne de commande suivantes pour définir des paramètres de configuration sensibles et spécifiques au système :

- `magento config:set` pour les paramètres spécifiques au système
- `magento config:sensitive:set` pour les paramètres sensibles

Pour définir le paramètre spécifique au système **Domaine d’e-mail par défaut**, qui se trouve dans la portée par défaut, utilisez la commande suivante :

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Il n’est pas nécessaire d’utiliser la portée dans la commande, car il s’agit de la portée par défaut.

Toutefois, pour définir des valeurs pour **Envoyer des e-mails à**, vous devez connaître le type de portée (`website`) et le code de portée, qui est probablement différent sur chaque site.

Exemple :

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Mettre à jour les paramètres partagés

Cette section explique comment extraire toutes les modifications que vous avez apportées à vos systèmes de développement et de création dans un environnement de production, ce qui met à jour les paramètres de configuration partagés (nom de magasin et numéro de TVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Vérification des paramètres de configuration dans l’Administration

Pour vérifier les paramètres de configuration :

1. Connectez-vous à l’administrateur de votre système d’exploitation.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Utilisez la liste **Affichage de la boutique** dans le coin supérieur gauche pour passer à un autre site web.

   Les options de configuration partagées que vous définissez dans le système de développement s’affichent de la manière suivante.

   ![Vérification des paramètres dans le système d’exploitation](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Le champ **Nom de la boutique** est modifiable dans la portée du site web, mais si vous passez à la portée Configuration par défaut, il n’est pas modifiable. C’est le résultat de la manière dont vous définissez les options dans le système de développement. La valeur de **numéro de TVA** n’est pas modifiable dans la portée du site web.

1. Si vous ne l’avez pas déjà fait, passez à la portée Configuration par défaut .
1. Dans le volet de navigation de gauche, sous Général, cliquez sur **Contacts**.

   Le champ **Envoyer des e-mails à** n’est pas modifiable, comme le montre la figure suivante. Il s’agit d’un contexte sensible.

   ![Vérification des paramètres dans le système d’exploitation](../../assets/configuration/split-deploy-verify-contacts.png)

1. Dans le volet de gauche, cliquez sur Clients > **Configuration du client**.
1. Dans le volet de droite, développez **Options de création de compte**.

   La valeur du champ **Domaine d’e-mail par défaut** s’affiche comme suit. Il s’agit d’un paramètre spécifique au système.

   ![Vérification des paramètres dans le système d’exploitation](../../assets/configuration/split-default-domain.png)

<!-- Last updated from includes: 2024-07-18 15:50:54 -->
