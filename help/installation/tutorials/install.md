---
title: Installation d’Adobe Commerce
description: Pour installer Adobe Commerce sur une infrastructure que vous détenez, procédez comme suit.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '2094'
ht-degree: 0%

---

# Installation d’Adobe Commerce

Avant de commencer, procédez comme suit :

* Vérifiez que votre système respecte les exigences décrites dans la section [configuration requise](../system-requirements.md).

* Compléter tout [condition](../prerequisites/overview.md) tâches.

* Effectuez les premières étapes d&#39;installation. Voir [Votre chemin d’installation ou de mise à niveau](../overview.md).

* Une fois connecté au serveur applicatif, [passer au propriétaire du système de fichiers](../prerequisites/file-system/overview.md).

* Consultez la section [Prise en main de l’installation de ligne de commande](../composer.md) aperçu.

>[!NOTE]
>
>Vous devez installer l’application à partir de son `bin` sous-répertoire .

Vous pouvez exécuter le programme d’installation plusieurs fois avec différentes options pour effectuer les tâches d’installation suivantes :

* Installation en phases : par exemple, après avoir configuré votre serveur web pour SSL (Secure Sockets Layer), vous pouvez à nouveau exécuter le programme d’installation pour définir les options SSL.

* Corrige les erreurs dans les installations précédentes.

* Installez l’application dans une autre instance de base de données.

>[!NOTE]
>
>Par défaut, le programme d’installation ne remplace pas la base de données si vous installez le logiciel Commerce dans la même instance de base de données. Vous pouvez utiliser le `cleanup-database` pour modifier ce comportement.

Voir aussi [Mettre à jour, réinstaller, désinstaller](uninstall.md).

## Installation sécurisée

{{$include /help/_includes/secure-install.md}}

## Commandes d’aide du programme

Vous pouvez exécuter les commandes suivantes pour rechercher des valeurs pour certains arguments requis :

| Argument du programme d&#39;installation | Commande |
| ------------------ | ------------------------------- |
| Langue | `magento info:language:list` |
| Devise | `magento info:currency:list` |
| Fuseau horaire | `magento info:timezone:list` |

>[!NOTE]
>
>Si une erreur s’affiche lors de l’exécution de ces commandes, vérifiez que vous avez mis à jour les dépendances d’installation comme décrit dans la section [Mise à jour des dépendances d’installation](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installation à partir de la ligne de commande

La commande install utilise le format suivant :

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

Les tableaux suivants décrivent les noms et les valeurs des options d’installation, telles que les commandes d’installation. Voir [Exemples d’installations localhost](#sample-localhost-installations).

>[!NOTE]
>
>Toutes les options contenant des espaces ou des caractères spéciaux doivent être entourées de guillemets simples ou doubles.

**Informations d’identification de l’administrateur :**

Les options suivantes spécifient les informations d’identification et les informations d’identification de l’utilisateur administrateur.

Dans Adobe Commerce version 2.2.8 et ultérieure, vous pouvez créer l’utilisateur administrateur pendant ou après l’installation. Si vous créez l’utilisateur pendant l’installation, toutes les variables d’informations d’identification d’administrateur sont requises. Voir [Exemples d’installations localhost](#sample-localhost-installations).

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--admin-firstname` | Prénom de l’utilisateur administrateur. | Oui |
| `--admin-lastname` | Nom de l’utilisateur administrateur. | Oui |
| `--admin-email` | Adresse électronique de l’utilisateur administrateur. | Oui |
| `--admin-user` | Nom d’utilisateur administrateur. | Oui |
| `--admin-password` | Mot de passe de l’administrateur. Le mot de passe doit contenir au moins 7 caractères et au moins un caractère alphabétique et au moins un caractère numérique. Nous vous recommandons un mot de passe plus long et plus complexe. Entourez l’intégralité de la chaîne du mot de passe de guillemets simples. Par exemple, `--admin-password='A0b9%t3g'` | Oui |

**Options de configuration du site et de la base de données :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--base-url` | URL de base à utiliser pour accéder à votre Admin et à votre storefront dans l’un des formats suivants :<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Remarque :** Le schéma (http:// ou https://) et une barre oblique à la fin sont tous les deux requis.<br><br>`<your install dir>` est le chemin d’accès relatif au docroot dans lequel installer l’application. Selon la configuration de votre serveur web et de vos hôtes virtuels, le chemin peut être magento2 ou il peut être vide.<br><br>Pour accéder à l’application sur localhost, vous pouvez utiliser l’une des méthodes suivantes : `http://127.0.0.1/<your install dir>/` ou `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` qui représente une URL de base définie par un paramètre d’hôte virtuel ou par un environnement de virtualisation tel que Docker. Par exemple, si vous configurez un hôte virtuel avec le nom d’hôte commerce.example.com, vous pouvez installer l’application avec `--base-url={{base_url}}` et accéder à l’administrateur avec une URL telle que `http://commerce.example.com/admin`. | Oui |
| `--backend-frontname` | URI (Uniform Resource Identifier) pour accéder à l’administrateur. Vous pouvez omettre ce paramètre pour laisser l’application générer un URI aléatoire pour vous avec le modèle suivant. <code>admin_jkhgdfq</code>.<br><br>Nous recommandons un URI aléatoire à des fins de sécurité. Un URI aléatoire est plus difficile à exploiter pour les hackers ou les logiciels malveillants.<br><br>L’URI s’affiche à la fin de l’installation. Vous pouvez l’afficher ultérieurement à tout moment à l’aide de la variable `magento info:adminuri` .<br><br>Si vous choisissez de saisir une valeur, nous vous recommandons de ne pas utiliser un mot commun tel que admin, backend. L’URI d’administration peut contenir des valeurs alphanumériques et un caractère de soulignement (`_`) uniquement. | Non |
| `--db-host` | Utilisez l’une des méthodes suivantes :<br><br>- Nom d’hôte ou adresse IP complet du serveur de base de données.<br><br>- `localhost` (par défaut) ou `127.0.0.1` si votre serveur de base de données se trouve sur le même hôte que votre serveur web.localhost, la bibliothèque cliente MySQL utilise des sockets UNIX pour se connecter à la base de données. `127.0.0.1` La bibliothèque cliente utilise le protocole TCP. Pour plus d’informations sur les sockets, voir [Documentation PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Remarque :** Vous pouvez éventuellement spécifier le port du serveur de base de données dans son nom d’hôte comme www.example.com:9000 | Oui |
| `--db-name` | Nom de l&#39;instance de base de données dans laquelle vous souhaitez installer les tables de base de données.<br><br>Par défaut : `magento2`. | Oui |
| `--db-user` | Nom d’utilisateur du propriétaire de l’instance de base de données.<br><br>Par défaut : `root`. | Oui |
| `--db-password` | Mot de passe du propriétaire de l’instance de base de données. | Oui |
| `--db-prefix` | À utiliser uniquement si vous installez les tables de base de données dans une instance de base de données qui contient déjà des tables Adobe Commerce.<br><br>Dans ce cas, utilisez un préfixe pour identifier les tables pour cette installation. Certains clients disposent de plusieurs instances Adobe Commerce s’exécutant sur un serveur avec toutes les tables dans la même base de données.<br><br>Le préfixe peut contenir, au maximum, cinq caractères. Il doit commencer par une lettre et ne peut contenir que des lettres, des chiffres et des caractères de soulignement.<br><br>Cette option permet à ces clients de partager le serveur de base de données avec plusieurs installations. | Non |
| `--db-ssl-key` | Chemin d’accès à la clé client. | Non |
| `--db-ssl-cert` | Chemin d’accès au certificat client. | Non |
| `--db-ssl-ca` | Chemin d’accès au certificat du serveur. | Non |
| `--language` | Code de langue à utiliser dans l’Admin et le storefront. (Si vous ne l’avez pas déjà fait, vous pouvez afficher la liste des codes de langue en saisissant `magento info:language:list` du répertoire bin.) | Non |
| `--currency` | Devise par défaut à utiliser dans le storefront. (Si vous ne l’avez pas déjà fait, vous pouvez afficher la liste des devises en saisissant `magento info:currency:list` du répertoire bin.) | Non |
| `--timezone` | Fuseau horaire par défaut à utiliser dans l’administration et le storefront. (Si vous ne l’avez pas déjà fait, vous pouvez afficher la liste des fuseaux horaires en saisissant `magento info:timezone:list` du répertoire bin.) | Non |
| `--use-rewrites` | `1` signifie que vous utilisez des réécritures de serveur web pour les liens générés dans le storefront et l’administrateur.<br><br>`0` désactive l’utilisation des réécritures de serveur web. Il s’agit du paramètre par défaut. | Non |
| `--use-secure` | `1` permet l’utilisation de SSL (Secure Sockets Layer) dans les URL de storefront. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` désactive l’utilisation de SSL. Dans ce cas, toutes les autres options d’URL sécurisées sont également supposées être 0. Il s’agit du paramètre par défaut. | Non |
| `--base-url-secure` | URL de base sécurisée à utiliser pour accéder à votre Admin et à votre storefront au format suivant : `http[s]://<host or ip>/<your install dir>/` | Non |
| `--use-secure-admin` | `1` signifie que vous utilisez SSL pour accéder à l’administrateur. Assurez-vous que votre serveur web prend en charge SSL avant de sélectionner cette option.<br><br>`0` signifie que vous n’utilisez pas SSL avec l’administrateur. Il s’agit du paramètre par défaut. | Non |
| `--admin-use-security-key` | 1 fait en sorte que l’application utilise une valeur de clé générée de manière aléatoire pour accéder aux pages dans l’administrateur et dans les formulaires. Ces valeurs clés permettent d’éviter les attaques par falsification de script intersite. Il s’agit du paramètre par défaut.<br><br>`0` désactive l’utilisation de la clé. | Non |
| `--session-save` | Utilisez l’une des méthodes suivantes :<br><br>- `db` pour stocker les données de session dans la base de données. Choisissez le stockage de la base de données si vous disposez d’une base de données en grappe ; dans le cas contraire, le stockage basé sur les fichiers n’offre pas beaucoup d’avantages.<br><br>- `files` pour stocker les données de session dans le système de fichiers. Le stockage des sessions basées sur des fichiers est approprié, sauf si l’accès au système de fichiers est lent, si vous disposez d’une base de données en grappe ou si vous souhaitez stocker des données de session dans Redis.<br><br>- `redis` pour stocker les données de session dans Redis. Si vous utilisez Redis pour la mise en cache des pages ou par défaut, Redis doit être déjà installé. Pour plus d’informations sur la configuration de la prise en charge de Redis, reportez-vous à la section Utilisation des rendus pour le stockage de session . | Non |
| `--key` | Si vous en avez un, spécifiez une clé pour crypter les données sensibles dans la base de données. Si vous n’en avez pas, l’application en génère une pour vous. | Oui |
| `--cleanup-database` | Pour déposer les tables de base de données avant d&#39;installer l&#39;application, indiquez ce paramètre sans valeur. Sinon, la base de données reste intacte. | Non |
| `--db-init-statements` | Paramètre de configuration MySQL avancé. Utilise les instructions d’initialisation de base de données à exécuter lors de la connexion à la base de données MySQL. Consultez une référence similaire à celle-ci avant de définir des valeurs.<br><br>Par défaut : `SET NAMES utf8;`. | Non |
| `--sales-order-increment-prefix` | Spécifiez une valeur string à utiliser comme préfixe pour les commandes client. En règle générale, il est utilisé pour garantir des numéros de commande uniques aux responsables du paiement. | Non |

>[!TIP]
>
>Pour activer les services de stockage distant lors de l’installation, voir [Configuration du stockage distant](../../configuration/remote-storage/remote-storage.md) dans le _Guide de configuration_.

**Options de configuration du moteur de recherche :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--search-engine` | Version du moteur de recherche. Les valeurs possibles sont `elasticsearch7`, `elasticsearch6`, et `elasticsearch5`. La valeur par défaut est `elasticsearch7`. Si vous avez installé OpenSearch comme moteur de recherche, indiquez la valeur `elasticsearch7`. Elasticsearch 5 a été abandonné et n’est pas recommandé. | Non |
| `--elasticsearch-host` | Nom d’hôte ou adresse IP où le moteur de recherche est en cours d’exécution. La valeur par défaut est `localhost`. | Non |
| `--elasticsearch-port` | Port des requêtes HTTP entrantes. La valeur par défaut est `9200`. | Non |
| `--elasticsearch-index-prefix` | Préfixe qui identifie l’index de recherche. La valeur par défaut est `magento2`. | Non |
| `--elasticsearch-timeout` | Nombre de secondes avant que le système ne s’arrête. La valeur par défaut est `15`. | Non |
| `--elasticsearch-enable-auth` | Active l’authentification sur le serveur du moteur de recherche. La valeur par défaut est `false`. | Non |
| `--elasticsearch-username` | ID utilisateur à authentifier | Non, sauf si l’authentification est activée |
| `--elasticsearch-password` | Mot de passe pour l’authentification | Non, sauf si l’authentification est activée |

**[!DNL RabbitMQ]options de configuration :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--amqp-host` | N’utilisez pas la variable `--amqp` à moins d’avoir déjà configuré une installation [!DNL RabbitMQ]. Voir [!DNL RabbitMQ] installation pour plus d’informations sur l’installation et la configuration [!DNL RabbitMQ].<br><br>Nom d’hôte où [!DNL RabbitMQ] est installé. | Non |
| `--amqp-port` | Port à utiliser pour la connexion à [!DNL RabbitMQ]. La valeur par défaut est 5672. | Non |
| `--amqp-user` | Nom d’utilisateur pour la connexion à [!DNL RabbitMQ]. N’utilisez pas l’utilisateur par défaut `guest`. | Non |
| `--amqp-password` | Mot de passe de connexion à [!DNL RabbitMQ]. N’utilisez pas le mot de passe par défaut `guest`. | Non |
| `--amqp-virtualhost` | L’hôte virtuel pour la connexion à [!DNL RabbitMQ]. La valeur par défaut est `/`. | Non |
| `--amqp-ssl` | Indique si la connexion à [!DNL RabbitMQ]. La valeur par défaut est `false`. Voir [!DNL RabbitMQ] pour plus d’informations sur la configuration de SSL pour [!DNL RabbitMQ]. | Non |
| `--consumers-wait-for-messages` | Les consommateurs doivent-ils attendre un message de la file d’attente ? 1 - Oui, 0 - Non | Non |

**Options de stockage à distance :**

| Nom | Description | Obligatoire ? |
|--- |--- |--- |
| `remote-storage-driver` | Nom de l’adaptateur<br>Valeurs possibles :<br>**fichier**: désactive le stockage distant et utilise le système de fichiers local.<br>**aws-s3**: utilisez la variable [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) | Non |
| `remote-storage-bucket` | Stockage d’objet ou nom du conteneur | Non |
| `remote-storage-prefix` | Préfixe facultatif (emplacement dans le stockage d’objets) | Non |
| `remote-storage-region` | Nom de la région | Non |
| `remote-storage-key` | Clé d’accès facultative | Non |
| `remote-storage-secret` | Clé secrète facultative | Non |

**Verrouiller les options de configuration :**

| Nom | Valeur | Obligatoire ? |
|--- |--- |--- |
| `--lock-provider` | Verrouillez le nom du fournisseur.<br><br>Opérateurs de verrouillage disponibles : `db`, `zookeeper`, `file`.<br><br>Le fournisseur de verrouillage par défaut : `db` | Non |
| `--lock-db-prefix` | Préfixe db spécifique pour éviter les conflits de verrouillage lors de l’utilisation de `db` fournisseur de verrouillage.<br><br>La valeur par défaut : `NULL` | Non |
| `--lock-zookeeper-host` | Hôte et port pour vous connecter à la grappe Zookeeper lorsque vous utilisez `zookeeper` fournisseur de verrouillage.<br><br>Par exemple : `127.0.0.1:2181` | Oui, si vous définissez `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Chemin d’accès dans lequel le gardien de page enregistre les verrous.<br><br>Le chemin par défaut est le suivant : `/magento/locks` | Non |
| `--lock-file-path` | Chemin d’accès où les verrous de fichier sont enregistrés. | Oui, si vous définissez `--lock-provider=file` |

**Options de configuration des consommateurs :**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Pour activer ou désactiver les modules après l’installation de l’application, voir [Activation et désactivation des modules](manage-modules.md).

**Données sensibles :**

{{$include /help/_includes/sensitive-data.md}}

### Exemples d’installations localhost

Les exemples suivants présentent les commandes permettant d’installer Adobe Commerce en local avec différentes options.

#### Exemple 1 : installation de base avec compte utilisateur admin

L’exemple suivant installe l’application avec les options suivantes :

* L’application est installée dans la variable `magento2` répertoire relatif au docroot du serveur web `localhost` et le chemin d’accès à l’administrateur est `admin`; par conséquent :

  Votre URL de storefront est `http://127.0.0.1`

* Le serveur de base de données se trouve sur le même hôte que le serveur web.

  Le nom de la base est `magento`, et le nom d’utilisateur et le mot de passe sont les deux `magento`

* Utilise les réécritures du serveur

* L’administrateur possède les propriétés suivantes :

   * Les prénoms et les noms sont `Commerce User`
   * Nom d’utilisateur `admin` et le mot de passe est `admin123`
   * L’adresse électronique est `user@example.com`

* La langue par défaut est `en_US` (Anglais américain)
* La devise par défaut est le dollar américain
* Le fuseau horaire par défaut est centré aux États-Unis (Amérique/Chicago)
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

Messages similaires à l’affichage suivant pour indiquer une installation réussie :

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Exemple 2 : installation de base sans compte utilisateur administrateur

Vous pouvez installer l’application sans créer d’utilisateur administrateur, comme illustré dans l’exemple suivant.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Les messages comme celui-ci s’affichent si l’installation est réussie :

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Une fois l’installation terminée, vous pouvez créer un utilisateur administrateur à l’aide de la méthode `admin:user:create` command :
[Créer ou modifier un administrateur](admin.md#create-or-edit-an-administrator)

#### Exemple 3 : installation avec des options supplémentaires

L’exemple suivant installe l’application avec les options suivantes :

* Magapplication est installé dans la variable `magento2` répertoire relatif au docroot du serveur web `localhost` et le chemin d’accès à l’administrateur est `admin`; par conséquent :

  Votre URL de storefront est `http://127.0.0.1`

* Le serveur de base de données se trouve sur le même hôte que le serveur web.

  Le nom de la base est `magento`, et le nom d’utilisateur et le mot de passe sont les deux `magento`

* L’administrateur possède les propriétés suivantes :

   * Les prénoms et les noms sont `Commerce User`
   * Nom d’utilisateur `admin` et le mot de passe est `admin123`
   * L’adresse électronique est `user@example.com`

* La langue par défaut est `en_US` (Anglais américain)
* La devise par défaut est le dollar américain
* Le fuseau horaire par défaut est centré aux États-Unis (Amérique/Chicago)
* Le programme d’installation nettoie d’abord la base de données avant d’installer les tables et le schéma.
* Vous utilisez une `ORD$` préfixe d’incrément de commande client (car il contient un caractère spécial) [`$`], la valeur doit être entre guillemets doubles)
* Les données de session sont enregistrées dans la base de données.
* Utilise les réécritures du serveur
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
>Vous devez saisir la commande sur une seule ligne ou, comme dans l&#39;exemple précédent, avec une `\` à la fin de chaque ligne.

Les messages comme celui-ci s’affichent si l’installation est réussie :

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>Si vous disposez d’un compte utilisateur pour accéder au serveur d’applications, reportez-vous à la section [définir un masque](../next-steps/set-umask.md). Ce type de configuration est typique pour l’hébergement partagé.
