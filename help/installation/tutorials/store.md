---
title: Configuration du magasin
description: Pour configurer votre boutique Adobe Commerce, procédez comme suit.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Configuration du magasin

Avant d’exécuter cette commande, vous devez effectuer les opérations suivantes *ou* vous devez [installer l’application](../advanced.md) :

* [Créer ou mettre à jour la configuration de déploiement](deployment.md)
* [Création du schéma de base de données](database.md)

## Installation sécurisée

{{$include /help/_includes/secure-install.md}}

## Configuration du magasin

Utilisation des commandes :

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Où le tableau suivant définit les paramètres et valeurs :

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--base-url` | URL de base à utiliser pour accéder à votre administration et à votre storefront dans l’un des formats suivants :<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Remarque :** le schéma (`http://` ou `https://`) et une barre oblique sont tous deux requis. `<your install dir>` est le chemin relatif à docroot dans lequel installer l’application. Selon la configuration de votre serveur web et de vos hôtes virtuels, le chemin d’accès peut être magento2 ou vide.<br><br>Pour accéder à l’application sur localhost, vous pouvez utiliser `http://127.0.0.1/<your install dir>/`.<br><br> : `{{base_url}}` qui représente une URL de base définie par un paramètre d’hôte virtuel ou par un environnement de virtualisation tel que Docker. Par exemple, si vous configurez un hôte virtuel avec le nom d’hôte commerce.example.com, vous pouvez installer l’application avec `--base-url={{base_url}}` et accéder à Admin avec une URL telle que `http://commerce.example.com/admin`. | Non |
| `--language` | Code de langue à utiliser dans Admin et Storefront.<br><br>(Si vous ne l’avez pas déjà fait, vous pouvez consulter la liste des codes de langue en saisissant `magento info:language:list` à partir du répertoire `bin`). | Non |
| `--currency` | Devise par défaut à utiliser dans le storefront. <br><br>(Si vous ne l&#39;avez pas déjà fait, vous pouvez consulter la liste des devises en saisissant `magento info:currency:list` depuis le répertoire `bin`.) | Non |
| `--timezone` | Fuseau horaire par défaut à utiliser dans Admin et Storefront. (Si vous ne l’avez pas déjà fait, vous pouvez consulter la liste des fuseaux horaires en saisissant `magento info:timezone:list` dans le répertoire `bin`.) | Non |
| `--use-rewrites` | `1` signifie que vous utilisez des réécritures de serveur web pour les liens générés dans le storefront et Admin.<br><br>`0` désactive l’utilisation des réécritures du serveur web. Il s’agit de la valeur par défaut. | Non |
| `--use-secure` | `1` permet l’utilisation du protocole SSL (Secure Sockets Layer) dans les URL de storefront. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` désactive l’utilisation de SSL. Dans ce cas, toutes les autres options d’URL sécurisée sont supposées également être 0. Il s’agit de la valeur par défaut. | Non |
| `--base-url-secure` | URL de base sécurisée à utiliser pour accéder à votre administration et storefront au format suivant : `http[s]://<host or ip>/<your install dir>/` | Non |
| `--use-secure-admin` | `1` signifie que vous utilisez SSL pour accéder à l’administrateur. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` signifie que vous n’utilisez pas SSL avec l’administrateur. Il s’agit de la valeur par défaut. | Non |
| `--admin-use-security-key` | `1` entraîne l’utilisation par l’application d’une valeur de clé générée de manière aléatoire pour accéder aux pages dans Admin et dans les formulaires. Ces valeurs clés permettent d’empêcher les attaques multisites par falsification de script. Il s’agit de la valeur par défaut.<br/><br/>`0` désactive l’utilisation de la clé . | Non |
| `--magento-init-params` | Ajoutez à n&#39;importe quelle commande pour personnaliser les paramètres d&#39;initialisation de l&#39;application<br/><br/>Par exemple : `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Non |
