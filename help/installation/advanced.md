---
title: Installation sur site avancée
description: Découvrez les scénarios d’installation avancés d’Adobe Commerce sur l’infrastructure que vous possédez.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '2313'
ht-degree: 0%

---

# Installation sur site avancée

>[!TIP]
>
>Perdu ? Besoin d&#39;un coup de main ? Essayez nos guides [Installation rapide](composer.md) ou [Installation du contributeur](https://developer.adobe.com/commerce/contributor/guides/install/).

>[!NOTE]
>
>Si vous choisissez d&#39;activer SELinux, consultez [SELinux et iptables](prerequisites/security.md).

## Interface de ligne de commande (CLI)

Adobe Commerce dispose d’une interface de ligne de commande unique pour les tâches d’installation et de configuration : `<magento_root>/bin/magento`. L’interface effectue plusieurs tâches, notamment :

* Installation (et tâches connexes telles que la création ou la mise à jour du schéma de base de données, la création de la configuration de déploiement).
* Effacement du cache.
* Gestion des index, y compris la réindexation
* Création de dictionnaires et de packages de traduction.
* Génération de classes inexistantes telles que des usines et des intercepteurs pour les plug-ins, génération de la configuration d&#39;injection de dépendance pour le gestionnaire d&#39;objets.
* Déploiement de fichiers d’affichage statiques.
* Création d’une feuille de style CSS à partir de moins.

Autres avantages :

* Une seule commande (`<magento_root>/bin/magento list`) répertorie toutes les commandes d’installation et de configuration disponibles.
* Interface utilisateur cohérente basée sur Symfony.
* L’interface de ligne de commande est extensible afin que les développeurs tiers puissent s’y connecter. Cela a l&#39;avantage supplémentaire d&#39;éliminer la courbe d&#39;apprentissage des utilisateurs.
* Les commandes des modules désactivés ne s’affichent pas.

Cette rubrique aborde l’installation du logiciel Adobe Commerce à l’aide de l’interface de ligne de commande. Pour plus d’informations sur la configuration, consultez le [Guide de configuration](../configuration/overview.md).

Le programme d’installation peut être exécuté plusieurs fois si nécessaire afin que vous puissiez :

* Fournir des valeurs différentes

  Par exemple, après avoir configuré votre serveur web pour le protocole SSL (Secure Sockets Layer), vous pouvez exécuter le programme d’installation pour définir les options SSL.

* Corriger les erreurs dans les installations précédentes
* Installation d’Adobe Commerce dans une autre instance de base de données

## Avant de démarrer l’installation

Avant de commencer, effectuez les étapes suivantes :

* Vérifiez que votre système répond à la configuration requise décrite dans la section [ Configuration requise ](system-requirements.md).

* Effectuez toutes les tâches [prérequises](prerequisites/overview.md).

* Effectuez les premières étapes d’installation. Voir [chemin d’installation ou de mise à niveau](overview.md).

* Après vous être connecté au serveur d’applications, [passez au propriétaire du système de fichiers](prerequisites/file-system/overview.md).

* Consultez la présentation du [démarrage rapide de l’installation](composer.md).

>[!NOTE]
>
>Vous devez installer Adobe Commerce à partir du sous-répertoire `bin`.

Vous pouvez exécuter le programme d’installation plusieurs fois avec différentes options pour effectuer des tâches d’installation telles que :

* Installation en plusieurs phases : par exemple, après avoir configuré votre serveur web pour le protocole SSL (Secure Sockets Layer), vous pouvez exécuter à nouveau le programme d’installation pour définir les options SSL.

* Corrigez les erreurs dans les installations précédentes.

* Installez Adobe Commerce dans une autre instance de base de données.

>[!NOTE]
>
>Par défaut, le programme d’installation ne remplace pas la base de données si vous installez le logiciel dans la même instance de base de données. Vous pouvez utiliser le paramètre `cleanup-database` facultatif pour modifier ce comportement.

Voir aussi [Mise à jour, réinstallation, désinstallation](tutorials/uninstall.md).

### Installation sécurisée

{{$include /help/_includes/secure-install.md}}

## Commandes d’aide du programme d’installation

Vous pouvez exécuter les commandes suivantes pour rechercher des valeurs pour certains arguments requis :

| Argument du programme d’installation | Commande |
| ------------------ | ------------------------------- |
| Langue | `bin/magento info:language:list` |
| Devise monétaire | `bin/magento info:currency:list` |
| Fuseau horaire | `bin/magento info:timezone:list` |

>[!NOTE]
>
>Si une erreur s&#39;affiche lorsque vous exécutez ces commandes, vérifiez que vous avez mis à jour les dépendances d&#39;installation, comme indiqué dans la section [Mettre à jour les dépendances d&#39;installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installation à partir de la ligne de commande

La commande d&#39;installation utilise le format suivant :

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

Les tableaux suivants décrivent les noms et valeurs des options d&#39;installation. Pour obtenir un exemple des commandes d’installation, voir [Exemples d’installations localhost](#sample-localhost-installations).

>[!NOTE]
>
>Toutes les options qui contiennent des espaces ou des caractères spéciaux doivent être placées entre guillemets simples ou doubles.

**Informations d’identification de l’administrateur :**

Les options suivantes spécifient les informations d’identification et d’identification de l’utilisateur Admin.

Vous pouvez créer l’utilisateur administrateur pendant ou après l’installation. Si vous créez l’utilisateur lors de l’installation, toutes les variables d’informations d’identification d’administrateur sont requises. Voir [Exemples d’installations localhost](#sample-localhost-installations).

Les tableaux suivants fournissent de nombreux paramètres d’installation, mais pas tous. Pour obtenir une liste complète, voir [Référence des outils de ligne de commande](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises).

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--admin-firstname` | Prénom de l’utilisateur administrateur. | Oui |
| `--admin-lastname` | Nom de l’utilisateur administrateur. | Oui |
| `--admin-email` | Adresse électronique de l’utilisateur administrateur. | Oui |
| `--admin-user` | Nom d’utilisateur de l’administrateur. | Oui |
| `--admin-password` | Mot de passe de l’utilisateur administrateur. Le mot de passe doit comporter au moins 7 caractères, au moins un caractère alphabétique et au moins un caractère numérique. Nous vous recommandons un mot de passe plus long et plus complexe. Placez l’intégralité de la chaîne de mot de passe entre guillemets simples. Par exemple, `--admin-password='A0b9%t3g'` | Oui |

**Options de configuration du site et de la base de données :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--base-url` | URL de base à utiliser pour accéder à votre administration et à votre storefront dans l’un des formats suivants :<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Remarque :** le schéma (http:// ou https://) et une barre oblique sont tous deux requis.<br><br>`<your install dir>` est le chemin relatif à docroot dans lequel installer le logiciel Adobe Commerce. Selon la configuration de votre serveur web et de vos hôtes virtuels, le chemin d’accès peut être magento2 ou vide.<br><br>Pour accéder à Adobe Commerce ou MagenAdobe Commerceuse, `http://127.0.0.1/<your install dir>/` ou `http://127.0.0.1/<your install dir>/`.<br><br> : `{{base_url}}` qui représente une URL de base définie par un paramètre d’hôte virtuel ou par un environnement de virtualisation tel que Docker. Par exemple, si vous configurez un hôte virtuel avec le nom d’hôte `magento.example.com`, vous pouvez installer le logiciel avec `--base-url={{base_url}}` et accéder à l’administrateur avec une URL telle que `http://magento.example.com/admin`. | Oui |
| `--backend-frontname` | Uniform Resource Identifier (URI) pour accéder à l’administrateur. Vous pouvez omettre ce paramètre pour permettre à l’application de générer un URI aléatoire à votre place avec le modèle suivant <code>admin_jkhgdfq</code>.<br><br>Nous vous recommandons d’utiliser un URI aléatoire à des fins de sécurité. Un URI aléatoire est plus difficile à exploiter pour les pirates ou les logiciels malveillants.<br><br>L’URI s’affiche à la fin de l’installation. Vous pouvez l&#39;afficher ultérieurement à tout moment à l&#39;aide de la commande `bin/magento info:adminuri`.<br><br>Si vous choisissez de saisir une valeur, nous vous recommandons de ne pas utiliser un mot commun tel que admin, backend. L’URI d’administration ne peut contenir que des valeurs alphanumériques et le caractère de soulignement (`_`). | Non |
| `--db-host` | Utilisez l’une des méthodes suivantes : <br><br>- Le nom d’hôte complet ou l’adresse IP complète du serveur de base de données.<br><br>- `localhost` (par défaut) ou `127.0.0.1` si votre serveur de base de données se trouve sur le même hôte que votre serveur web.localhost signifie que la bibliothèque cliente MySQL utilise des sockets UNIX pour se connecter à la base de données. `127.0.0.1` entraîne l’utilisation du protocole TCP par la bibliothèque cliente. Pour plus d’informations sur les sockets, consultez la documentation [PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Remarque :** vous pouvez éventuellement spécifier le port du serveur de base de données dans son nom d’hôte, tel que www.example.com:9000 | Oui |
| `--db-name` | Nom de l’instance de base de données dans laquelle vous souhaitez installer les tables de base de données.<br><br>La valeur par défaut est `magento2`. | Oui |
| `--db-user` | Nom d’utilisateur du propriétaire de l’instance de base de données.<br><br>La valeur par défaut est `root`. | Oui |
| `--db-password` | Mot de passe du propriétaire de l&#39;instance de base de données. | Oui |
| `--db-prefix` | À utiliser uniquement si vous installez les tables de la base de données dans une instance de base de données qui contient déjà des tables Adobe Commerce.<br><br>Dans ce cas, utilisez un préfixe pour identifier les tables de cette installation. Certains clients disposent de plusieurs serveurs Adobe Commerce ou MagenAdobe Commerceserver avec toutes les tables dans la même base de données.<br><br>La longueur du préfixe ne peut pas excéder cinq caractères. Elle doit commencer par une lettre et ne peut contenir que des lettres, des chiffres et des traits de soulignement.<br><br>Cette option permet à ces clients de partager le serveur de base de données avec plusieurs installations Adobe Commerce |
| `--db-ssl-key` | Chemin d’accès à la clé client. | Non |
| `--db-ssl-cert` | Chemin d’accès au certificat client. | Non |
| `--db-ssl-ca` | Chemin d’accès au certificat du serveur. | Non |
| `--language` | Code de langue à utiliser dans Admin et Storefront. (Si vous ne l&#39;avez pas déjà fait, vous pouvez afficher la liste des codes de langue en saisissant `bin/magento info:language:list` à partir du répertoire bin.) | Non |
| `--currency` | Devise par défaut à utiliser dans le storefront. (Si vous ne l&#39;avez pas déjà fait, vous pouvez consulter la liste des devises en saisissant `bin/magento info:currency:list` à partir du répertoire bin.) | Non |
| `--timezone` | Fuseau horaire par défaut à utiliser dans Admin et Storefront. (Si vous ne l’avez pas déjà fait, vous pouvez consulter la liste des fuseaux horaires en saisissant `bin/magento info:timezone:list` dans le répertoire `bin/`.) | Non |
| `--use-rewrites` | `1` signifie que vous utilisez des réécritures de serveur web pour les liens générés dans le storefront et Admin.<br><br>`0` désactive l’utilisation des réécritures du serveur web. Il s’agit de la valeur par défaut. | Non |
| `--use-secure` | `1` permet l’utilisation du protocole SSL (Secure Sockets Layer) dans les URL de storefront. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` désactive l’utilisation de SSL. Dans ce cas, toutes les autres options d’URL sécurisée sont supposées également être 0. Il s’agit de la valeur par défaut. | Non |
| `--base-url-secure` | URL de base sécurisée à utiliser pour accéder à votre administration et storefront au format suivant : `http[s]://<host or ip>/<your install dir>/` | Non |
| `--use-secure-admin` | `1` signifie que vous utilisez SSL pour accéder à l’administrateur. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` signifie que vous n’utilisez pas SSL avec l’administrateur. Il s’agit de la valeur par défaut. | Non |
| `--admin-use-security-key` | 1 entraîne l’utilisation par l’application d’une valeur de clé générée de manière aléatoire pour accéder aux pages dans Admin et dans les formulaires. Ces valeurs clés permettent d’empêcher les attaques multisites par falsification de script. Il s’agit de la valeur par défaut.<br><br>`0` désactive l’utilisation de la clé . | Non |
| `--session-save` | Utilisez l’une des méthodes suivantes : <br><br>- `db` pour stocker les données de session dans la base de données. Choisissez le stockage de la base de données si vous disposez d&#39;une base de données en cluster ; sinon, le stockage basé sur des fichiers ne sera pas très avantageux.<br><br> : `files` de stocker les données de session dans le système de fichiers. Le stockage des sessions basé sur des fichiers est approprié, sauf si l’accès au système de fichiers est lent, si vous disposez d’une base de données en cluster ou si vous souhaitez stocker les données de session dans Redis.<br><br>- `redis` de stocker les données de session dans Redis. Si vous utilisez Redis pour la mise en cache par défaut ou de pages, Redis doit être déjà installé. Consultez la section Utilisation de Redis pour le stockage de session pour plus d’informations sur la configuration de la prise en charge de Redis. | Non |
| `--key` | Si vous en avez une, spécifiez une clé pour chiffrer les données sensibles dans la base de données. Si vous n’en avez pas, l’application en génère une pour vous. | Oui |
| `--cleanup-database` | Pour supprimer des tables de base de données avant d’installer Adobe Commerce, spécifiez ce paramètre sans valeur. Dans le cas contraire, la base de données reste intacte. | Non |
| `--db-init-statements` | Paramètre de configuration MySQL avancé. Utilise les instructions d&#39;initialisation de base de données à exécuter lors de la connexion à la base de données MySQL. Consultez une référence similaire à celle-ci avant de définir des valeurs.<br><br>La valeur par défaut est `SET NAMES utf8;`. | Non |
| `--sales-order-increment-prefix` | Spécifiez une valeur de chaîne à utiliser comme préfixe pour les commandes client. En règle générale, cela permet de garantir des numéros de commande uniques pour les processeurs de paiement. | Non |

**Options de configuration du moteur de recherche :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--search-engine` | Version d’Elasticsearch ou OpenSearch à utiliser comme moteur de recherche. La valeur par défaut est `elasticsearch7`. Elasticsearch 5 a été abandonné et n’est pas recommandé. | Non |
| `--elasticsearch-host` | Nom d’hôte ou adresse IP sur lequel Elasticsearch est exécuté. La valeur par défaut est `localhost`. | Non |
| `--elasticsearch-port` | Port Elasticsearch pour les requêtes HTTP entrantes. La valeur par défaut est `9200`. | Non |
| `--elasticsearch-index-prefix` | Préfixe qui identifie l’index de recherche Elasticsearch. La valeur par défaut est `magento2`. | Non |
| `--elasticsearch-timeout` | Nombre de secondes avant l’expiration du système. La valeur par défaut est `15`. | Non |
| `--elasticsearch-enable-auth` | Active l’authentification sur le serveur Elasticsearch. La valeur par défaut est `false`. | Non |
| `--elasticsearch-username` | ID utilisateur pour l’authentification auprès du serveur Elasticsearch. | Non, sauf si l’authentification est activée |
| `--elasticsearch-password` | Mot de passe pour l’authentification sur le serveur Elasticsearchserver. | Non, sauf si l’authentification est activée |
| `--opensearch-host` | Nom d’hôte ou adresse IP sur lequel OpenSearch est exécuté. La valeur par défaut est `localhost`. | Non |
| `--opensearch-port` | Port OpenSearch pour les requêtes HTTP entrantes. La valeur par défaut est `9200`. | Non |
| `--opensearch-index-prefix` | Préfixe qui identifie l’index de recherche OpenSearch. La valeur par défaut est `magento2`. | Non |
| `--opensearch-timeout` | Nombre de secondes avant l’expiration du système. La valeur par défaut est `15`. | Non |
| `--opensearch-enable-auth` | Active l’authentification sur le serveur OpenSearch. La valeur par défaut est `false`. | Non |
| `--opensearch-username` | ID utilisateur pour l’authentification auprès du serveur OpenSearch. | Non, sauf si l’authentification est activée |
| `--opensearch-password` | Mot de passe pour l’authentification sur le serveur OpenSearch. | Non, sauf si l’authentification est activée |

**[!DNL RabbitMQ]options de configuration :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--amqp-host` | N’utilisez pas les options de `--amqp`, sauf si vous avez déjà configuré une installation de [!DNL RabbitMQ]. Pour plus d’informations sur l’installation et la configuration de [!DNL RabbitMQ], consultez [!DNL RabbitMQ] installation .<br><br>Nom d’hôte sur lequel [!DNL RabbitMQ] est installé. | Non |
| `--amqp-port` | Port à utiliser pour la connexion à [!DNL RabbitMQ]. La valeur par défaut est 5672. | Non |
| `--amqp-user` | Nom d’utilisateur pour la connexion à [!DNL RabbitMQ]. N’utilisez pas l’`guest` utilisateur par défaut. | Non |
| `--amqp-password` | Mot de passe de connexion à [!DNL RabbitMQ]. N’utilisez pas le mot de passe par défaut `guest`. | Non |
| `--amqp-virtualhost` | L’hôte virtuel pour la connexion à [!DNL RabbitMQ]. La valeur par défaut est `/`. | Non |
| `--amqp-ssl` | Indique s’il faut se connecter à [!DNL RabbitMQ]. La valeur par défaut est `false`. Voir [!DNL RabbitMQ] pour plus d’informations sur la configuration de SSL pour [!DNL RabbitMQ]. | Non |
| `--consumers-wait-for-messages` | Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non | Non |

**Verrouiller les options de configuration :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--lock-provider` | Verrouillez le nom du fournisseur.<br><br>Fournisseurs de verrous disponibles : `db`, `zookeeper`, `file`.<br><br>Fournisseur de verrous par défaut : `db` | Non |
| `--lock-db-prefix` | Préfixe de base de données spécifique pour éviter les conflits de verrouillage lors de l&#39;utilisation `db` fournisseur de verrouillage.<br><br>Valeur par défaut : `NULL` | Non |
| `--lock-zookeeper-host` | Hôte et port pour la connexion au cluster Zookeeper lorsque vous utilisez `zookeeper` fournisseur de verrouillage.<br><br>Par exemple : `127.0.0.1:2181` | Oui, si vous définissez `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Chemin où Zookeeper enregistre les verrous.<br><br>Le chemin d’accès par défaut est : `/magento/locks` | Non |
| `--lock-file-path` | Chemin d’accès où les verrous de fichier sont enregistrés. | Oui, si vous définissez `--lock-provider=file` |

**Options de configuration des consommateurs :**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Pour activer ou désactiver les modules après l’installation d’Adobe Commerce, voir [ Activer et désactiver les modules](tutorials/manage-modules.md).

**Données sensibles :**

{{$include /help/_includes/sensitive-data.md}}

### Exemples d’installations localhost

Les exemples suivants montrent les commandes pour installer Adobe Commerce localement avec différentes options.

#### Exemple 1 : installation de base avec un compte utilisateur administrateur

L’exemple suivant installe Adobe Commerce avec les options suivantes :

* L’application est installée dans le répertoire `magento2` relatif au serveur web docroot sur `localhost` et le chemin d’accès à l’administrateur est `admin` ; par conséquent :

  Votre URL de storefront est `http://127.0.0.1`

* Le serveur de base de données se trouve sur le même hôte que le serveur Web.

  Le nom de la base de données est `magento` et le nom d&#39;utilisateur et le mot de passe sont tous deux `magento`

* Utilise les réécritures serveur

* L’administrateur possède les propriétés suivantes :

   * Les prénoms et noms sont `Magento User`
   * Le nom d’utilisateur est `admin` et le mot de passe est `admin123`
   * Adresse e-mail `user@example.com`

* La langue par défaut est le `en_US` (anglais (États-Unis)
* La devise par défaut est le dollar américain
* Le fuseau horaire par défaut est U.S. Central (Amérique/Chicago)
* OpenSearch 1.2 est installé sur `os-host.example.com` et se connecte sur le port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Des messages similaires au suivant s’affichent pour indiquer une installation réussie :

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Exemple 2 : installation de base sans compte utilisateur administrateur

Vous pouvez installer Adobe Commerce sans créer d’utilisateur administrateur, comme le montre l’exemple ci-dessous.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Des messages comme celui-ci s’affichent si l’installation est réussie :

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Après l’installation, vous pouvez créer un utilisateur administrateur à l’aide de la commande `admin:user:create` :
[Créer ou modifier un administrateur](tutorials/admin.md#create-or-edit-an-administrator)

#### Exemple 3 : installation avec des options supplémentaires

L’exemple suivant installe Adobe Commerce avec les options suivantes :

* L’application est installée dans le répertoire `magento2` relatif au serveur web docroot sur `localhost` et le chemin d’accès à l’administrateur est `admin` ; par conséquent :

  Votre URL de storefront est `http://127.0.0.1`

* Le serveur de base de données se trouve sur le même hôte que le serveur Web.

  Le nom de la base de données est `magento` et le nom d&#39;utilisateur et le mot de passe sont tous deux `magento`

* L’administrateur possède les propriétés suivantes :

   * Les prénoms et noms sont `Magento User`
   * Le nom d’utilisateur est `admin` et le mot de passe est `admin123`
   * Adresse e-mail `user@example.com`

* La langue par défaut est le `en_US` (anglais (États-Unis)
* La devise par défaut est le dollar américain
* Le fuseau horaire par défaut est U.S. Central (Amérique/Chicago)
* Le programme d’installation nettoie d’abord la base de données avant d’installer les tables et le schéma
* Vous pouvez utiliser le préfixe d&#39;incrémentation de commande client `ORD$` (puisqu&#39;il contient un caractère spécial [`$`], la valeur doit être placée entre guillemets doubles)
* Les données de session sont enregistrées dans la base de données
* Utilise les réécritures serveur
* OpenSearch est installé sur `os-host.example.com` et se connecte sur le port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>Vous devez saisir la commande sur une seule ligne ou, comme dans l&#39;exemple précédent, avec un caractère `\` à la fin de chaque ligne.

Des messages comme celui-ci s’affichent si l’installation est réussie :

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
