---
title: Exemple d’utilisation de variables d’environnement
description: Consultez un exemple de la manière de définir des valeurs partagées, spécifiques au système et sensibles dans votre système de développement à l’aide de variables d’environnement.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Exemple d’utilisation de variables d’environnement

Cet exemple montre comment définir des valeurs partagées, spécifiques au système et sensibles dans votre système de développement, puis définir toutes les valeurs de votre système de production à l’aide d’une combinaison de la configuration partagée, `config.php` et des variables d’environnement PHP.

Ces paramètres de configuration peuvent être partagés entre les systèmes de développement et de production :

Numéro de TVA et Nom du magasin depuis **Magasins** > Paramètres > **Configuration** > Général > **Général**

Ces paramètres de configuration sont spécifiques au système ou sensibles, comme indiqué ci-dessous :

- Envoyer des emails à (sensible) à partir de **Magasins** > Paramètres > **Configuration** > Général > **Contacts**
- Domaine de messagerie par défaut (spécifique au système) de **Magasins** > Paramètres > **Configuration** > Clients > **Configuration client** > **Créer des options de compte**

Vous pouvez suivre la même procédure pour configurer les paramètres des références suivantes :

- [Référence des chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md)
- [Référence des chemins de configuration des paiements](../reference/config-reference-payment.md)
- [Référence générale sur les chemins de configuration](../reference/config-reference-general.md)
- [Référence sur les chemins de configuration de l’extension Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Avant de commencer

Avant de commencer, configurez les autorisations et la propriété du système de fichiers comme décrit dans la section [Condition préalable requise pour le développement, la création et les systèmes de production](../deployment/prerequisites.md).

## Hypothèses

Cette rubrique fournit un exemple de modification de la configuration du système de production. Si vous le souhaitez, vous pouvez choisir différentes options de configuration.

Pour les besoins de cet exemple, nous supposons que :

- Vous utilisez le contrôle source Git
- Le système de développement est disponible dans un référentiel distant Git nommé `mconfig`
- Votre branche de travail Git est nommée `m2.2_deploy`

## Étape 1 : définir la configuration dans le système de développement

Pour définir les paramètres régionaux et les unités de poids par défaut dans votre système de développement :

1. Connectez-vous à l’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Si plusieurs sites web sont disponibles, utilisez la liste **Affichage magasin** dans le coin supérieur gauche pour passer à un autre site web comme le montre la figure suivante.

   ![Changer de sites web](../../assets/configuration/split-deploy-switch-website.png)

1. Dans le volet de droite, développez **Informations sur le magasin**.
1. Si nécessaire, décochez la case **Utiliser la valeur par défaut** en regard du champ **Numéro de TVA** .
1. Entrez un nombre dans le champ (par exemple, `12345`).
1. Dans le champ **Nom de la boutique**, saisissez une valeur (comme `My Store`).
1. Cliquez sur **Enregistrer la configuration**.
1. Utilisez la liste **Affichage magasin** pour sélectionner la **configuration par défaut** comme le montre la figure suivante.

   ![Basculez vers la configuration par défaut](../../assets/configuration/split-deploy-default-config.png)

1. Dans le volet de navigation de gauche, sous Général, cliquez sur **Contacts**.
1. Décochez la case **Utiliser la valeur par défaut** en regard du champ **Envoyer les e-mails à** .
1. Entrez une adresse électronique dans le champ .
1. Cliquez sur **Enregistrer la configuration**.
1. Dans le volet de gauche, cliquez sur Clients > **Configuration client**.
1. Dans le volet de droite, développez **Créer des options de compte**.
1. Décochez la case **Utiliser la valeur système** en regard du champ **Domaine de messagerie par défaut** .
1. Saisissez un nom de domaine dans le champ .
1. Cliquez sur **Enregistrer la configuration**.
1. Si vous y êtes invité, videz le cache.

## Etape 2 : mise à jour de la configuration

Maintenant que vous avez modifié la configuration dans l’administrateur, écrivez la configuration partagée dans un fichier comme décrit dans cette section.

{{$include /help/_includes/config-save-config.md}}

Notez que même si `app/etc/env.php` (la configuration spécifique au système) a été mise à jour, ne l’archivez pas dans le contrôle source. Vous allez créer les mêmes paramètres de configuration sur votre système de production plus loin dans cette procédure.

## Étape 3 : Mettre à jour votre système de génération et générer des fichiers

Maintenant que vous avez validé vos modifications dans la configuration partagée pour le contrôle de code source, vous pouvez extraire ces modifications dans votre système de création, compiler du code et générer des fichiers statiques. La dernière étape consiste à extraire ces modifications dans votre système de production.

{{$include /help/_includes/config-update-build-system.md}}

## Étape 4 : mise à jour du système de production

La dernière étape du processus consiste à mettre à jour votre système de production. Vous devez le faire en deux parties :

- Mise à jour des paramètres sensibles et spécifiques au système
- Mise à jour des paramètres partagés

### Mise à jour des paramètres sensibles et spécifiques au système

Pour définir les paramètres sensibles et spécifiques au système à l’aide de variables d’environnement, vous devez connaître les éléments suivants :

- Portée de chaque paramètre

  Si vous avez suivi les instructions de l’étape 1, la portée de l’option Envoyer les emails à est globale (c’est-à-dire, la portée de la configuration par défaut) et la portée du domaine de courriel par défaut est le site web.

  Vous devez connaître le code du site web pour définir la valeur de configuration Domaine de messagerie par défaut. Pour plus d’informations sur sa recherche, voir [Utilisation de variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables) .

- Chemin de configuration de chaque paramètre

  Les chemins de configuration utilisés dans cet exemple sont les suivants :

  | Nom du paramètre | Chemin de configuration |
  |--------------|--------------|
  | Envoyer des emails à | `contact/email/recipient_email` |
  | Domaine de messagerie par défaut | `customer/create_account/email_domain` |

  Vous pouvez trouver tous les chemins de configuration sensibles et spécifiques au système dans la [référence de chemins de configuration sensibles et spécifiques au système](../reference/config-reference-sens.md).

#### Conversion des chemins de configuration en noms de variables

Comme expliqué dans la section [Utiliser des variables d&#39;environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables), le format des variables est le suivant :

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

La valeur de `<SCOPE>` est `CONFIG__DEFAULT__` pour la portée globale ou `CONFIG__WEBSITES__<WEBSITE CODE>` pour la portée du site web.

Pour trouver la valeur de `<SYSTEM__VARIABLE__NAME>`, remplacez chaque caractère `/` du chemin de configuration par deux traits de soulignement.

Les noms de variable sont les suivants :

| Nom | Chemin de configuration | Nom de variable |
|--------------|--------------|--------------|
| Envoyer des emails à | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Domaine de messagerie par défaut | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>Le tableau ci-dessus comporte un exemple de code de site web, `BASE`, pour le paramètre de configuration Domaine de messagerie par défaut . Remplacez `BASE` par le code de site web approprié pour votre boutique.

#### Définition des variables à l’aide de variables d’environnement

Vous pouvez définir les valeurs de variable dans le `index.php` en utilisant le format suivant :

```php
$_ENV['VARIABLE'] = 'value';
```

**Pour définir des valeurs de variable** :

1. Connectez-vous à votre système de production en tant que propriétaire du système de fichiers ou basculez vers .
1. Ouvrez `<Commerce root dir>/pub/index.php` dans un éditeur de texte.
1. N’importe où dans `index.php`, définissez des valeurs pour les variables similaires à ce qui suit :

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Enregistrez vos modifications dans `pub/index.php` et quittez l’éditeur de texte.
1. Passez à la section suivante.

### Mise à jour des paramètres partagés

Cette section explique comment extraire toutes les modifications que vous avez apportées à vos systèmes de développement et de création, ce qui met à jour les paramètres de configuration partagés (Nom du magasin et Numéro de TVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Vérification des paramètres de configuration dans Admin

Cette section explique comment vérifier les paramètres de configuration dans l’administrateur de votre système de production.

**Pour vérifier les paramètres de configuration** :

1. Connectez-vous à l’administrateur de votre système de production.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > Général > **Général**.
1. Utilisez la liste **Affichage magasin** dans le coin supérieur gauche pour passer à un autre site web.

   Les options de configuration partagées que vous définissez dans le système de développement s’affichent comme suit.

   ![Vérifiez les paramètres dans le système de production](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Le champ **Nom du magasin** est modifiable dans la portée du site web, mais si vous passez à la portée de configuration par défaut, il n’est pas modifiable. C’est le résultat de la définition des options dans le système de développement. La valeur de **Numéro de TVA** n’est pas modifiable dans la portée du site web.

1. Si vous ne l’avez pas déjà fait, passez à la portée de la configuration par défaut.
1. Dans le volet de navigation de gauche, sous Général, cliquez sur **Contacts**.

   Le champ **Envoyer des emails à** n’est pas modifiable, comme le montre la figure suivante. Il s’agit d’un paramètre sensible.

   ![Vérifiez les paramètres dans le système de production](../../assets/configuration/split-deploy-verify-contacts.png)

1. Dans le volet de gauche, cliquez sur Clients > **Configuration client**.
1. Dans le volet de droite, développez **Créer des options de compte**.

   La valeur du champ **Default Email Domain** s’affiche comme suit. Il s’agit d’un paramètre spécifique au système.

   ![Vérifiez les paramètres dans le système de production](../../assets/configuration/split-default-domain.png)
