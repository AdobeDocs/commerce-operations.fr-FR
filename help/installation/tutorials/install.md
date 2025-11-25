---
title: Installation d’Adobe Commerce
description: Pour installer Adobe Commerce sur l’infrastructure que vous possédez, procédez comme suit.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 0%

---

# Installation d’Adobe Commerce

Avant de commencer, effectuez les étapes suivantes :

* Vérifiez que votre système répond à la configuration requise décrite dans la section [ Configuration requise ](../system-requirements.md).

* Effectuez toutes les tâches [prérequises](../prerequisites/overview.md).

* Effectuez les premières étapes d’installation. Voir [Votre chemin d’installation ou de mise à niveau](../overview.md).

* Après vous être connecté au serveur d’applications, [passez au propriétaire du système de fichiers](../prerequisites/file-system/overview.md).

* Consultez la présentation [Prise en main de l’installation en ligne de commande](../composer.md) .

>[!NOTE]
>
>Vous devez installer l’application à partir de son sous-répertoire `bin`.

Vous pouvez exécuter le programme d’installation plusieurs fois avec différentes options pour effectuer des tâches d’installation telles que :

* Installation en plusieurs phases : par exemple, après avoir configuré votre serveur web pour le protocole SSL (Secure Sockets Layer), vous pouvez exécuter à nouveau le programme d’installation pour définir les options SSL.

* Corrigez les erreurs dans les installations précédentes.

* Installez l’application dans une autre instance de base de données.

>[!NOTE]
>
>Par défaut, le programme d’installation ne remplace pas la base de données si vous installez le logiciel Commerce dans la même instance de base de données. Vous pouvez utiliser le paramètre `cleanup-database` facultatif pour modifier ce comportement.

Voir aussi [Mise à jour, réinstallation, désinstallation](uninstall.md).

## Installation sécurisée

{{$include /help/_includes/secure-install.md}}

## Commandes d’aide du programme d’installation

Vous pouvez exécuter les commandes suivantes pour rechercher des valeurs pour certains arguments requis :

| Argument du programme d’installation | Commande |
| ------------------ | ------------------------------- |
| Langue | `magento info:language:list` |
| Devise monétaire | `magento info:currency:list` |
| Fuseau horaire | `magento info:timezone:list` |

>[!NOTE]
>
>Si une erreur s&#39;affiche lorsque vous exécutez ces commandes, vérifiez que vous avez mis à jour les dépendances d&#39;installation, comme indiqué dans la section [Mettre à jour les dépendances d&#39;installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).

## Installation à partir de la ligne de commande

La commande d&#39;installation utilise le format suivant :

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

Les tableaux suivants décrivent les noms et valeurs des options d&#39;installation, telles que les commandes d&#39;installation. Voir [Exemples d’installations localhost](#sample-localhost-installations).

>[!NOTE]
>
>Toutes les options qui contiennent des espaces ou des caractères spéciaux doivent être placées entre guillemets simples ou doubles.

**Informations d’identification de l’administrateur :**

Les options suivantes spécifient les informations d’identification et d’identification de l’utilisateur administrateur.

Dans Adobe Commerce version 2.2.8 et ultérieure, vous pouvez créer l’utilisateur administrateur pendant ou après l’installation. Si vous créez l’utilisateur lors de l’installation, toutes les variables d’informations d’identification d’administrateur sont requises. Voir [Exemples d’installations localhost](#sample-localhost-installations).

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
| `--base-url` | URL de base à utiliser pour accéder à votre administration et à votre storefront dans l’un des formats suivants :<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Remarque :** le schéma (http:// ou https://) et une barre oblique sont tous deux requis.<br><br>`<your install dir>` est le chemin relatif à docroot dans lequel installer l’application. Selon la configuration de votre serveur web et de vos hôtes virtuels, le chemin d’accès peut être magento2 ou vide.<br><br>Pour accéder à l’application sur localhost, vous pouvez utiliser `http://127.0.0.1/<your install dir>/` ou `http://127.0.0.1/<your install dir>/`.<br><br> : `{{base_url}}` qui représente une URL de base définie par un paramètre d’hôte virtuel ou par un environnement de virtualisation tel que Docker. Par exemple, si vous configurez un hôte virtuel avec le nom d’hôte commerce.example.com, vous pouvez installer l’application avec `--base-url={{base_url}}` et accéder à Admin avec une URL telle que `http://commerce.example.com/admin`. | Oui |
| `--backend-frontname` | Uniform Resource Identifier (URI) pour accéder à l’administrateur. Vous pouvez omettre ce paramètre pour permettre à l’application de générer un URI aléatoire à votre place avec le modèle suivant <code>admin_jkhgdfq</code>.<br><br>Nous vous recommandons d’utiliser un URI aléatoire à des fins de sécurité. Un URI aléatoire est plus difficile à exploiter pour les pirates ou les logiciels malveillants.<br><br>L’URI s’affiche à la fin de l’installation. Vous pouvez l&#39;afficher ultérieurement à tout moment à l&#39;aide de la commande `magento info:adminuri`.<br><br>Si vous choisissez de saisir une valeur, nous vous recommandons de ne pas utiliser un mot commun tel que admin, backend. L’URI d’administration ne peut contenir que des valeurs alphanumériques et le caractère de soulignement (`_`). | Non |
| `--db-host` | Utilisez l’une des méthodes suivantes : <br><br>- Le nom d’hôte complet ou l’adresse IP complète du serveur de base de données.<br><br>- `localhost` (par défaut) ou `127.0.0.1` si votre serveur de base de données se trouve sur le même hôte que votre serveur web.localhost signifie que la bibliothèque cliente MySQL utilise des sockets UNIX pour se connecter à la base de données. `127.0.0.1` entraîne l’utilisation du protocole TCP par la bibliothèque cliente. Pour plus d’informations sur les sockets, consultez la documentation [PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Remarque :** vous pouvez éventuellement spécifier le port du serveur de base de données dans son nom d’hôte, tel que www.example.com:9000 | Oui |
| `--db-name` | Nom de l’instance de base de données dans laquelle vous souhaitez installer les tables de base de données.<br><br>La valeur par défaut est `magento2`. | Oui |
| `--db-user` | Nom d’utilisateur du propriétaire de l’instance de base de données.<br><br>La valeur par défaut est `root`. | Oui |
| `--db-password` | Mot de passe du propriétaire de l&#39;instance de base de données. | Oui |
| `--db-prefix` | À utiliser uniquement si vous installez les tables de la base de données dans une instance de base de données qui contient déjà des tables Adobe Commerce.<br><br>Dans ce cas, utilisez un préfixe pour identifier les tables de cette installation. Certains clients disposent de plusieurs instances Adobe Commerce s’exécutant sur un serveur avec toutes les tables dans la même base de données.<br><br>La longueur du préfixe ne peut pas excéder cinq caractères. Elle doit commencer par une lettre et ne peut contenir que des lettres, des chiffres et des traits de soulignement.<br><br>Cette option permet à ces clients de partager le serveur de base de données avec plusieurs installations. | Non |
| `--db-ssl-key` | Chemin d’accès à la clé client. | Non |
| `--db-ssl-cert` | Chemin d’accès au certificat client. | Non |
| `--db-ssl-ca` | Chemin d’accès au certificat du serveur. | Non |
| `--language` | Code de langue à utiliser dans Admin et Storefront. (Si vous ne l&#39;avez pas déjà fait, vous pouvez afficher la liste des codes de langue en saisissant `magento info:language:list` à partir du répertoire bin.) | Non |
| `--currency` | Devise par défaut à utiliser dans le storefront. (Si vous ne l&#39;avez pas déjà fait, vous pouvez consulter la liste des devises en saisissant `magento info:currency:list` à partir du répertoire bin.) | Non |
| `--timezone` | Fuseau horaire par défaut à utiliser dans Admin et Storefront. (Si vous ne l’avez pas déjà fait, vous pouvez afficher la liste des fuseaux horaires en saisissant `magento info:timezone:list` à partir du répertoire bin.) | Non |
| `--use-rewrites` | `1` signifie que vous utilisez des réécritures de serveur web pour les liens générés dans le storefront et Admin.<br><br>`0` désactive l’utilisation des réécritures du serveur web. Il s’agit de la valeur par défaut. | Non |
| `--use-secure` | `1` permet l’utilisation du protocole SSL (Secure Sockets Layer) dans les URL de storefront. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` désactive l’utilisation de SSL. Dans ce cas, toutes les autres options d’URL sécurisée sont supposées également être 0. Il s’agit de la valeur par défaut. | Non |
| `--base-url-secure` | URL de base sécurisée à utiliser pour accéder à votre administration et storefront au format suivant : `http[s]://<host or ip>/<your install dir>/` | Non |
| `--use-secure-admin` | `1` signifie que vous utilisez SSL pour accéder à l’administrateur. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` signifie que vous n’utilisez pas SSL avec l’administrateur. Il s’agit de la valeur par défaut. | Non |
| `--admin-use-security-key` | 1 entraîne l’utilisation par l’application d’une valeur de clé générée de manière aléatoire pour accéder aux pages dans Admin et dans les formulaires. Ces valeurs clés permettent d’empêcher les attaques multisites par falsification de script. Il s’agit de la valeur par défaut.<br><br>`0` désactive l’utilisation de la clé . | Non |
| `--session-save` | Utilisez l’une des méthodes suivantes : <br><br>- `db` pour stocker les données de session dans la base de données. Choisissez le stockage de la base de données si vous disposez d&#39;une base de données en cluster ; sinon, le stockage basé sur des fichiers ne sera pas très avantageux.<br><br> : `files` de stocker les données de session dans le système de fichiers. Le stockage des sessions basé sur des fichiers est approprié, sauf si l’accès au système de fichiers est lent, si vous disposez d’une base de données en cluster ou si vous souhaitez stocker les données de session dans Redis.<br><br>- `redis` de stocker les données de session dans Redis. Si vous utilisez Redis pour la mise en cache par défaut ou de pages, Redis doit être déjà installé. Consultez la section Utilisation de Redis pour le stockage de session pour plus d’informations sur la configuration de la prise en charge de Redis. | Non |
| `--key` | Si vous en avez une, spécifiez une clé pour chiffrer les données sensibles dans la base de données. Si vous n’en avez pas, l’application en génère une pour vous. | Oui |
| `--cleanup-database` | Pour supprimer des tables de base de données avant d&#39;installer l&#39;application, spécifiez ce paramètre sans valeur. Dans le cas contraire, la base de données reste intacte. | Non |
| `--db-init-statements` | Paramètre de configuration MySQL avancé. Utilise les instructions d&#39;initialisation de base de données à exécuter lors de la connexion à la base de données MySQL. Consultez une référence similaire à celle-ci avant de définir des valeurs.<br><br>La valeur par défaut est `SET NAMES utf8;`. | Non |
| `--sales-order-increment-prefix` | Spécifiez une valeur de chaîne à utiliser comme préfixe pour les commandes client. En règle générale, cela permet de garantir des numéros de commande uniques pour les processeurs de paiement. | Non |

>[!TIP]
>
>Pour activer les services de stockage distant lors de l’installation, consultez [Configuration du stockage distant](../../configuration/remote-storage/remote-storage.md) dans le _Guide de configuration_.

**Options de configuration du moteur de recherche :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--search-engine` | Version du moteur de recherche. Les valeurs possibles sont `elasticsearch7`, `elasticsearch6` et `elasticsearch5`. La valeur par défaut est `elasticsearch7`. Si vous avez installé OpenSearch en tant que moteur de recherche, indiquez la valeur `elasticsearch7`. Elasticsearch 5 a été abandonné et n’est pas recommandé. | Non |
| `--elasticsearch-host` | Nom d’hôte ou adresse IP où s’exécute le moteur de recherche. La valeur par défaut est `localhost`. | Non |
| `--elasticsearch-port` | Port pour les requêtes HTTP entrantes. La valeur par défaut est `9200`. | Non |
| `--elasticsearch-index-prefix` | Préfixe qui identifie l’index de recherche. La valeur par défaut est `magento2`. | Non |
| `--elasticsearch-timeout` | Nombre de secondes avant l’expiration du système. La valeur par défaut est `15`. | Non |
| `--elasticsearch-enable-auth` | Active l’authentification sur le serveur du moteur de recherche. La valeur par défaut est `false`. | Non |
| `--elasticsearch-username` | ID de l’utilisateur à authentifier | Non, sauf si l’authentification est activée |
| `--elasticsearch-password` | Mot de passe pour l’authentification | Non, sauf si l’authentification est activée |

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

**Options de configuration d’ActiveMQ Artemis :**

>[!NOTE]
>
>ActiveMQ Artemis a été introduit dans Adobe Commerce 2.4.6 et les versions ultérieures.

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--stomp-host` | N’utilisez pas les options `--stomp`, sauf si vous avez déjà configuré une installation d’ActiveMQ Artemis. Consultez Installation d’ActiveMQ Artemis pour plus d’informations sur l’installation et la configuration d’ActiveMQ Artemis.<br><br>Nom d’hôte sur lequel ActiveMQ Artemis est installé. | Non |
| `--stomp-port` | Port à utiliser pour la connexion aux artéfacts ActiveMQ. La valeur par défaut est 61613. | Non |
| `--stomp-user` | Nom d’utilisateur pour la connexion aux artéfacts ActiveMQ. N’utilisez pas l’`artemis` utilisateur par défaut. | Non |
| `--stomp-password` | Mot de passe de connexion à ActiveMQ Artemis. N’utilisez pas le mot de passe par défaut `artemis`. | Non |
| `--stomp-ssl` | Indique s’il faut se connecter à ActiveMQ Artemis à l’aide de SSL. La valeur par défaut est `false`. Consultez ActiveMQ Artemis pour plus d’informations sur la configuration de SSL pour ActiveMQ Artemis. | Non |
| `--consumers-wait-for-messages` | Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non | Non |

**Options de stockage à distance :**

| Nom | Description | Obligatoire ? |
|--- |--- |--- |
| `remote-storage-driver` | Nom de la carte<br>Valeurs possibles :<br>**file** : désactive le stockage distant et utilise le système de fichiers local <br>**aws-s3** : utilisez le [service Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) | Non |
| `remote-storage-bucket` | Nom du conteneur ou de stockage d’objets | Non |
| `remote-storage-prefix` | Préfixe facultatif (emplacement dans le stockage des objets) | Non |
| `remote-storage-region` | Nom de la région | Non |
| `remote-storage-key` | Clé d’accès facultative | Non |
| `remote-storage-secret` | Clé secrète facultative | Non |

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
>Pour activer ou désactiver les modules après l’installation de l’application, voir [ Activer et désactiver les modules](manage-modules.md).

**Données sensibles :**

{{$include /help/_includes/sensitive-data.md}}

### Exemples d’installations localhost

Les exemples suivants montrent les commandes pour installer Adobe Commerce localement avec différentes options.

#### Exemple 1 : installation de base avec un compte utilisateur administrateur

L’exemple suivant installe l’application avec les options suivantes :

* L’application est installée dans le répertoire `magento2` relatif au serveur web docroot sur `localhost` et le chemin d’accès à l’administrateur est `admin` ; par conséquent :

  Votre URL de storefront est `http://127.0.0.1`

* Le serveur de base de données se trouve sur le même hôte que le serveur Web.

  Le nom de la base de données est `magento` et le nom d&#39;utilisateur et le mot de passe sont tous deux `magento`

* Utilise les réécritures serveur

* L’administrateur possède les propriétés suivantes :

   * Les prénoms et noms sont `Commerce User`
   * Le nom d’utilisateur est `admin` et le mot de passe est `admin123`
   * Adresse e-mail `user@example.com`

* La langue par défaut est le `en_US` (anglais (États-Unis)
* La devise par défaut est le dollar américain
* Le fuseau horaire par défaut est U.S. Central (Amérique/Chicago)
* Elasticsearch 7 est installé sur `es-host.example.com` et se connecte sur le port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
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

Vous pouvez installer l’application sans créer d’utilisateur administrateur, comme le montre l’exemple suivant.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
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
[Créer ou modifier un administrateur](admin.md#create-or-edit-an-administrator)

#### Exemple 3 : installation avec des options supplémentaires

L’exemple suivant installe l’application avec les options suivantes :

* Magapplication est installé dans le répertoire `magento2` relatif au serveur web docroot sur `localhost` et le chemin d’accès à l’administrateur est `admin` ; par conséquent :

  Votre URL de storefront est `http://127.0.0.1`

* Le serveur de base de données se trouve sur le même hôte que le serveur Web.

  Le nom de la base de données est `magento` et le nom d&#39;utilisateur et le mot de passe sont tous deux `magento`

* L’administrateur possède les propriétés suivantes :

   * Les prénoms et noms sont `Commerce User`
   * Le nom d’utilisateur est `admin` et le mot de passe est `admin123`
   * Adresse e-mail `user@example.com`

* La langue par défaut est le `en_US` (anglais (États-Unis)
* La devise par défaut est le dollar américain
* Le fuseau horaire par défaut est U.S. Central (Amérique/Chicago)
* Le programme d’installation nettoie d’abord la base de données avant d’installer les tables et le schéma
* Vous utilisez un préfixe d&#39;incrément de commande client `ORD$` (puisqu&#39;il contient un caractère spécial [`$`], la valeur doit être placée entre guillemets doubles)
* Les données de session sont enregistrées dans la base de données
* Utilise les réécritures serveur
* Elasticsearch 7 est installé sur `es-host.example.com` et se connecte sur le port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
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

#### Exemple 4 : installation avec ActiveMQ Artemis

L’exemple suivant montre comment installer Adobe Commerce avec ActiveMQ Artemis comme courtier de messages :

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 --stomp-host=localhost --stomp-port=61613 \
--stomp-user=artemis --stomp-password=artemis
```

>[!NOTE]
>
>L’installation d’ActiveMQ Artemis nécessite Adobe Commerce 2.4.6 ou une version ultérieure.

>[!TIP]
>
>Si vous ne disposez que d’un compte utilisateur pour accéder au serveur d’applications, voir [définition d’un masque](../next-steps/set-umask.md). Ce type de configuration est courant pour l’hébergement partagé.

<!-- Last updated from includes: 2024-04-16 09:42:31 -->
