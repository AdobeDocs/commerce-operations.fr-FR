---
title: Exemple avec des variables d’environnement
description: Consultez un exemple de définition de valeurs partagées, spécifiques au système et sensibles dans votre système de développement à l’aide de variables d’environnement.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Exemple avec des variables d’environnement

Cet exemple montre comment définir des valeurs partagées, spécifiques au système et sensibles dans votre système de développement, puis définir toutes les valeurs dans votre système de production à l’aide d’une combinaison des variables d’environnement de configuration partagée, `config.php` et PHP.

Ces paramètres de configuration peuvent être partagés entre les systèmes de développement et de production :

Numéro de TVA et nom du magasin dans **Magasins** > Paramètres > **Configuration** > Général > **Général**

Ces paramètres de configuration sont spécifiques au système ou sensibles, comme indiqué :

- Envoyer des e-mails à (sensible) depuis **Magasins** > Paramètres > **Configuration** > Général > **Contacts**
- Domaine d’e-mail par défaut (spécifique au système) à partir de **Magasins** > Paramètres > **Configuration** > Clients > **Configuration client** > **Options de création de compte**

Vous pouvez utiliser la même procédure pour configurer des paramètres dans les références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence des chemins de configuration généraux](../reference/config-reference-general.md)
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
1. Si nécessaire, décochez la case **Utiliser par défaut** en regard du champ **Numéro de TVA**.
1. Saisissez un nombre dans le champ (par exemple, `12345`).
1. Dans le champ **Nom de la boutique**, saisissez une valeur (comme `My Store`).
1. Cliquez sur **Enregistrer la configuration**.
1. Utilisez la liste **Affichage de la boutique** pour sélectionner la configuration **par défaut** comme le montre la figure suivante.

   ![Passer à la configuration par défaut](../../assets/configuration/split-deploy-default-config.png)

1. Dans le volet de navigation de gauche, sous Général, cliquez sur **Contacts**.
1. Désélectionnez la case **Utiliser la valeur par défaut** en regard du champ **Envoyer des e-mails à**.
1. Saisissez une adresse e-mail dans le champ.
1. Cliquez sur **Enregistrer la configuration**.
1. Dans le volet de gauche, cliquez sur Clients > **Configuration du client**.
1. Dans le volet de droite, développez **Options de création de compte**.
1. Désélectionnez la case **Utiliser la valeur système** en regard du champ **Domaine d’e-mail par défaut**.
1. Saisissez un nom de domaine dans le champ .
1. Cliquez sur **Enregistrer la configuration**.
1. Si vous y êtes invité, videz le cache.

## Étape 2 : mettre à jour la configuration

Maintenant que vous avez modifié la configuration dans l’administration, écrivez la configuration partagée dans un fichier , comme indiqué dans cette section.

{{$include /help/_includes/config-save-config.md}}

Notez que même si `app/etc/env.php` (la configuration spécifique au système) a été mise à jour, ne l’archivez pas dans le contrôle de code source. Vous allez créer les mêmes paramètres de configuration sur votre système d’exploitation plus loin dans cette procédure.

## Étape 3 : mettre à jour votre système de génération et générer des fichiers

Maintenant que vous avez validé vos modifications de la configuration partagée dans le contrôle de code source, vous pouvez extraire ces modifications dans votre système de génération, compiler le code et générer des fichiers statiques. La dernière étape consiste à apporter ces modifications à votre système de production.

{{$include /help/_includes/config-update-build-system.md}}

## Etape 4 : Mise à jour du système d&#39;exploitation

La dernière étape du processus consiste à mettre à jour votre système de production. Vous devez le faire en deux parties :

- Mettre à jour les paramètres sensibles et spécifiques au système
- Mettre à jour les paramètres partagés

### Mettre à jour les paramètres sensibles et spécifiques au système

Pour définir les paramètres sensibles et spécifiques au système à l’aide de variables d’environnement, vous devez connaître les éléments suivants :

- Portée de chaque paramètre

  Si vous avez suivi les instructions de l’étape 1, la portée de l’option Envoyer des e-mails à est globale (c’est-à-dire la portée Configuration par défaut ) et la portée du domaine d’e-mail par défaut est site web.

  Vous devez connaître le code du site web pour définir la valeur de configuration Domaine de messagerie par défaut . Voir [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables) pour plus d’informations sur la manière de le trouver.

- Chemin de configuration pour chaque paramètre

  Les chemins de configuration utilisés dans cet exemple sont les suivants :

  | Nom du paramètre | Chemin de configuration |
  |--------------|--------------|
  | Envoyer Des E-Mails À | `contact/email/recipient_email` |
  | Domaine d’e-mail par défaut | `customer/create_account/email_domain` |

  Vous trouverez tous les chemins de configuration sensibles et spécifiques au système dans la [référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md).

#### Convertir les chemins de configuration en noms de variables

Comme indiqué dans la section [Utilisation des variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables), le format des variables est le suivant :

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

La valeur de `<SCOPE>` est `CONFIG__DEFAULT__` pour la portée globale ou `CONFIG__WEBSITES__<WEBSITE CODE>` pour la portée du site web.

Pour rechercher la valeur de `<SYSTEM__VARIABLE__NAME>`, remplacez chaque caractère `/` dans le chemin de configuration par deux traits de soulignement.

Les noms des variables sont les suivants :

| Nom | Chemin de configuration | Nom de la variable |
|--------------|--------------|--------------|
| Envoyer Des E-Mails À | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Domaine d’e-mail par défaut | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>Le tableau précédent contient un exemple de code de site web, `BASE`, pour le paramètre de configuration Domaine d’e-mail par défaut . Remplacez `BASE` par le code de site web approprié pour votre boutique.

#### Définition des variables à l’aide de variables d’environnement

Vous pouvez définir les valeurs de variable dans le `index.php` à l’aide du format suivant :

```php
$_ENV['VARIABLE'] = 'value';
```

**Pour définir des valeurs de variable** :

1. Connectez-vous à votre système de production en tant que propriétaire du système de fichiers ou passez à ce dernier.
1. Ouvrez `<Commerce root dir>/pub/index.php` dans un éditeur de texte.
1. N’importe où dans `index.php`, définissez des valeurs pour les variables similaires à ce qui suit :

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Enregistrez vos modifications dans `pub/index.php` et quittez l’éditeur de texte.
1. Passez à la section suivante.

### Mettre à jour les paramètres partagés

Cette section explique comment extraire toutes les modifications que vous avez apportées à vos systèmes de développement et de création, ce qui met à jour les paramètres de configuration partagés (nom de magasin et numéro de TVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Vérification des paramètres de configuration dans l’Administration

Cette section explique comment vérifier les paramètres de configuration dans l’administration de votre système d’exploitation.

**Pour vérifier les paramètres de configuration** :

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
