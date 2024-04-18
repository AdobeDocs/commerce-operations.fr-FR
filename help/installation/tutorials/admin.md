---
title: Création, modification ou déverrouillage d’un compte administrateur
description: Pour gérer le compte administrateur de votre application d’administration Adobe Commerce, procédez comme suit.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Création, modification ou déverrouillage d’un compte administrateur

Avant de pouvoir utiliser cette commande, vous devez effectuer les opérations suivantes :

- [Création de la configuration de déploiement](deployment.md)
- [Activez au minimum les modules Magento_Authorization et Magento_User .](manage-modules.md)
- Création du schéma de la base de données

>[!NOTE]
>
>La méthode la plus simple pour créer la base de données consiste à utiliser la commande . `magento setup:upgrade`.

## Créer ou modifier un administrateur

Utilisez cette commande pour créer un administrateur ou pour modifier un administrateur existant.

>[!NOTE]
>
>Si vous modifiez un administrateur, seule la variable `first name`, `last name`, et `password` peut être modifié.

Utilisation des commandes :

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Où le tableau suivant définit des paramètres et des valeurs :

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--admin-firstname` | Prénom de l’utilisateur administrateur. | Oui |
| `--admin-lastname` | Nom de l’utilisateur administrateur. | Oui |
| `--admin-email` | Adresse électronique de l’utilisateur administrateur. | Oui |
| `--admin-user` | Nom d’utilisateur administrateur. | Oui |
| `--admin-password` | Mot de passe de l’administrateur. Le mot de passe doit contenir au moins 7 caractères et au moins un caractère alphabétique et au moins un caractère numérique. <br><br>Nous vous recommandons un mot de passe plus long et plus complexe. Si la chaîne de mot de passe contient des caractères spéciaux nécessitant une interprétation littérale (barres obliques inverses ou espaces, par exemple), placez le mot de passe entre guillemets simples. | Oui |
| `--magento-init-params` | Ajouter à toute commande pour personnaliser les paramètres d’initialisation de l’application<br/><br/>Par exemple : `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Non |

Exemple d’utilisation :

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

Si vous ne spécifiez aucun des paramètres requis, l’application les demande dans l’interface de ligne de commande :

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

L’exemple suivant met à jour : `first name`, `last name`, et `password` de `j.doe` utilisateur admin :

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## Déverrouillage d’un compte administrateur

Utilisez cette commande pour déverrouiller le compte d’un administrateur verrouillé, généralement en raison de plusieurs tentatives de connexion incorrectes.

```bash
bin/magento admin:user:unlock {username}
```

Vous devez indiquer le nom d’utilisateur de l’administrateur. Exemple :

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

Si le compte n’est pas déverrouillé ou en cas de problème, le message suivant s’affiche :

```terminal
The user account "admin" was not locked or could not be unlocked
```

Vérifiez que l’utilisateur est un administrateur, qu’il est actif et que le compte est verrouillé. Pour afficher la liste des utilisateurs verrouillés dans l’administrateur, connectez-vous en tant qu’administrateur, puis cliquez sur **Système** > **Autorisations** > **Utilisateurs verrouillés**.

Si le compte n’existe pas, le message suivant s’affiche :

```terminal
Couldn't find the user account "bob"
```
