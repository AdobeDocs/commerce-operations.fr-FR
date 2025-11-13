---
title: Créer, modifier ou déverrouiller un compte administrateur
description: Pour gérer le compte administrateur de votre application Adobe Commerce Admin, procédez comme suit.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: aaed7dba7d11085eb8e2793cefffb8c8b082e750
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Créer, modifier ou déverrouiller un compte administrateur

Avant d’utiliser cette commande, vous devez effectuer les opérations suivantes :

- [Création de la configuration de déploiement](deployment.md)
- [Activez au minimum les modules Magento_Authorization et Magento_User](manage-modules.md)
- Création du schéma de base de données

>[!NOTE]
>
>La méthode la plus simple pour créer la base de données consiste à utiliser l’`magento setup:upgrade` de commande .

## Créer ou modifier un administrateur

Utilisez cette commande pour créer un administrateur ou modifier un administrateur existant.

>[!NOTE]
>
>Si vous modifiez un administrateur, seuls les `first name`, `last name` et `password` peuvent être modifiés.

Utilisation des commandes :

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Où le tableau suivant définit les paramètres et valeurs :

| Nom | Valeur | Obligatoire ? |
|--- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| `--admin-firstname` | Prénom de l’utilisateur administrateur. | Oui |
| `--admin-lastname` | Nom de l’utilisateur administrateur. | Oui |
| `--admin-email` | Adresse électronique de l’utilisateur administrateur. | Oui |
| `--admin-user` | Nom d’utilisateur de l’administrateur. | Oui |
| `--admin-password` | Mot de passe de l’utilisateur administrateur. Le mot de passe doit comporter au moins 12 caractères, au moins une lettre et au moins un chiffre. <br><br>Adobe recommande de spécifier un mot de passe plus long et plus complexe. Si la chaîne de mot de passe contient des caractères spéciaux qui nécessitent une interprétation littérale (tels que des barres obliques inverses ou des espaces), placez le mot de passe entre guillemets simples. | Oui |
| `--magento-init-params` | Ajoutez à n&#39;importe quelle commande pour personnaliser les paramètres d&#39;initialisation de l&#39;application<br/><br/>Par exemple : `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Non |

Exemple d’utilisation :

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

Si vous ne spécifiez aucun des paramètres requis, l’application les interroge dans l’interface de ligne de commande :

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

L’exemple suivant met à jour les `first name`, `last name` et `password` d’`j.doe` utilisateur administrateur :

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## Déverrouiller un compte administrateur

Utilisez cette commande pour déverrouiller le compte d’un administrateur verrouillé, généralement en raison de plusieurs tentatives de connexion incorrectes.

```bash
bin/magento admin:user:unlock {username}
```

Vous devez indiquer le nom d’utilisateur de l’administrateur. Exemple :

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

Si le compte n’est pas déverrouillé ou en cas de problème, le message suivant s’affiche :

```
The user account "admin" was not locked or could not be unlocked
```

Vérifiez que l’utilisateur est un administrateur, qu’il est actif et que le compte est verrouillé. Pour afficher la liste des utilisateurs verrouillés dans Admin, connectez-vous en tant qu’administrateur et cliquez sur **Système** > **Autorisations** > **Utilisateurs verrouillés**.

Si le compte n’existe pas, le message suivant s’affiche :

```
Couldn't find the user account "bob"
```
