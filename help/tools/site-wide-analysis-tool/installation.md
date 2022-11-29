---
title: Guide d’installation
description: "Utilisation de ce guide pour l’installation [!DNL Site-Wide Analysis Tool] pour votre site web"
source-git-commit: bfcedda38f91f5dba8880bb1593ad40a6e3f8041
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Guide d’installation

Le [!DNL Site-Wide Analysis Tool] fournit 24/7 surveillance des performances, rapports et recommandations en temps réel pour garantir la sécurité et la maniabilité d’Adobe Commerce sur les installations d’infrastructure cloud. Il fournit également des informations détaillées sur les correctifs disponibles et installés, les extensions tierces et votre installation Adobe Commerce.

>[!INFO]
>
>En savoir plus [procédure d’activation](../site-wide-analysis-tool/access.md) la valeur [!DNL Site-Wide Analysis Tool] et générer des rapports.

Si vous disposez d’une installation sur site d’Adobe Commerce, vous devez installer un agent sur votre infrastructure pour utiliser l’outil. Vous n’avez pas besoin d’installer l’agent sur Adobe Commerce sur les projets d’infrastructure cloud.

## Agent

Le [!DNL Site-Wide Analysis Tool] L’agent vous permet d’utiliser la variable [!DNL Site-Wide Analysis Tool] pour les installations sur site d’Adobe Commerce.

Le [!DNL Site-Wide Analysis Tool] L’agent collecte les données de l’application et de l’entreprise, les analyse et fournit des informations supplémentaires sur l’intégrité de votre installation afin que vous puissiez améliorer l’expérience client. Il surveille votre application et vous aide à identifier les problèmes de performances, de sécurité, de disponibilité et d’application.

L’installation de l’agent nécessite les étapes suivantes :

1. Vérification de la configuration requise.

1. Configuration des clés d’API dans [!UICONTROL Commerce Services Connector] extension .

1. Installez l’agent.

1. Exécutez l’agent.

>[!INFO]
>
>L’agent prend en charge les installations Adobe Commerce à plusieurs noeuds. Vous devez installer et configurer l’agent sur chaque noeud.

## Configuration requise

Votre infrastructure sur site doit répondre aux exigences suivantes avant d’installer l’agent :

- Systèmes d’exploitation

   - [!DNL Linux x86-64] les distributions, telles que [!DNL RedHat Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], et similaires
   >[!IMPORTANT]
   >
   >Adobe Commerce n’est pas pris en charge sur [!DNL Microsoft Windows] ou [!DNL macOS].

- Adobe Commerce 2.4.1 ou version ultérieure

- [!DNL Commerce Services Connector extension]

- CLI PHP

- Utilitaires de base/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

L’agent requiert la variable [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) l’extension à installer sur votre système et [configuré](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) avec les clés API. Pour vérifier que l’extension est installée, exécutez la commande suivante :

```bash
bin/magento module:status Magento_ServicesConnector
```

Si vous avez installé l’extension et l’avez configurée à l’aide d’une clé d’API existante pour un autre service, vous **DOIT régénérer la clé API** et mettez-le à jour dans l’administrateur Adobe Commerce de l’agent.

1. Insérer votre site web dans [mode de maintenance](../../installation/tutorials/maintenance-mode.md).

1. Se connecter [accounts.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

1. Cliquez sur **[!UICONTROL API Portal]**.

1. Cliquez sur **[!UICONTROL Delete]** en regard de la clé API existante.

1. [Configurer](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) une nouvelle clé API.

>[!IMPORTANT]
>
> Si vous générez de nouvelles clés dans le portail API, mettez immédiatement à jour les clés API dans la variable [!DNL Admin configuration]. Si vous générez de nouvelles clés et ne les mettez pas à jour dans la variable [!DNL Admin], vos extensions SaaS ne fonctionneront plus et vous perdrez des données importantes.

Si l’extension n’est pas installée, procédez comme suit pour l’installer :

1. Ajoutez l’extension à votre `composer.json` et installez-le.

   ```bash
   composer require magento/services-connector:1.*
   ```

1. Activez l’extension .

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. Mettez à jour le schéma de la base de données.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configuration des clés d’API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) pour connecter l’extension à votre système.

## Installation de l’agent

Nous avons créé une [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) pour simplifier l’installation. Nous vous recommandons d’utiliser le script shell, mais vous pouvez suivre le [installation manuelle](#manual) si nécessaire.

>[!INFO]
>
>Une fois l’agent installé, il se met à jour automatiquement lorsqu’une nouvelle version est disponible.

### Scripts

1. Téléchargez et exécutez le script shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Nous vous recommandons d’installer l’agent en dehors de votre répertoire de projet Adobe Commerce racine.

1. Vérifiez l’installation.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Après avoir téléchargé et installé l’agent, vous devez [configurer son exécution](#run-the-agent) en utilisant l’une des méthodes suivantes :

   - [Service](#service) (recommandé si vous disposez de l’accès racine)

   - [Cron](#cron)

### Manuel {#manual}

Si vous ne souhaitez pas utiliser notre [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) pour installer l’agent, vous devez l’installer manuellement en procédant comme suit :

1. Créez un répertoire dans lequel vous souhaitez télécharger l’agent.

   >[!TIP]
   >
   >Nous vous recommandons d’installer l’agent en dehors de votre répertoire de projet Adobe Commerce racine.

1. Téléchargez le fichier binaire et décompressez-le.

   >[!INFO]
   >
   >Pour utiliser la variable [!DNL Site-Wide Analysis Tool], vous devez d’abord lire et accepter les Conditions d’utilisation qui s’affichent lorsque vous accédez au tableau de bord à partir de l’administrateur Adobe Commerce.

   Pour le **AMD64** architecture :

   1. Téléchargez l’archive du lanceur.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Décompressez l’archive du lanceur.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   Pour le **ARM64** architecture :

   1. Téléchargez l’archive du lanceur.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Décompressez l’archive du lanceur.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *(Facultatif)* Vérifiez la signature du fichier de somme de contrôle.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Facultatif)* Vérifiez la somme de contrôle.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Créez le `config.yaml` avec le contenu suivant.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Vérifiez l’installation.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Après avoir téléchargé et installé l’agent, vous devez [configurer son exécution](#run-the-agent) en utilisant l’une des méthodes suivantes :

   - [Service](#service) (recommandé si vous disposez de l’accès racine)

   - [Cron](#cron)

## Exécution de l’agent {#run-the-agent}

Nous vous recommandons de configurer l’agent pour qu’il s’exécute en tant que service. Si vous disposez d’un accès limité à votre infrastructure et que vous ne disposez pas d’autorisations racine, vous devez utiliser [cron](#cron) au lieu de .

### Service {#service}

1. Création d’un fichier d’unité systemd `(/etc/systemd/system/scheduler.service)` avec la configuration suivante (remplacez `<filesystemowner>` avec l’utilisateur Unix propriétaire du répertoire dans lequel l’agent et le logiciel Adobe Commerce sont installés). Si vous avez téléchargé l’agent en tant qu’utilisateur root, modifiez le répertoire et le propriétaire des fichiers imbriqués.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Lancez le service.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Vérifiez que le service est en cours d’exécution.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Si vous ne disposez pas d’autorisations root ou si vous ne disposez pas des autorisations nécessaires pour configurer un service en tant que root, vous pouvez utiliser cron à la place.

Mettez à jour votre planning cron :

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Désinstaller

Exécutez les commandes suivantes pour désinstaller le service de votre système et supprimer tous les fichiers générés :

1. Arrêtez le planificateur.

   ```bash
   systemctl stop scheduler
   ```

1. Désactivez le planificateur.

   ```bash
   systemctl disable scheduler
   ```

1. Suppression de la fonction du service de planificateur `systemd` fichier d’unité.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Rechargez la variable `systemd` configuration du gestionnaire.

   ```bash
   systemctl daemon-reload
   ```

1. Réinitialiser les `systemd` d’un état en échec.

   ```bash
   systemctl reset-failed
   ```

1. Supprimez le répertoire du service du planificateur.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Supprimez le fichier binaire du planificateur.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Si vous avez configuré l’agent pour qu’il s’exécute avec cron à la place, utilisez les instructions suivantes :

1. Supprimez l’agent de la liste crontab.

   ```bash
   crontab -e
   ```

1. Arrêtez la tâche en cours.

   ```bash
   ps aux | grep scheduler
   ```

1. Supprimez le répertoire dans lequel vous avez installé l’agent.

   ```bash
   rm -rf swat-agent
   ```

## Remplacement du fichier de configuration

Vous pouvez remplacer les valeurs que vous avez spécifiées dans le fichier de configuration lors de l’installation à l’aide de variables d’environnement. Cela préserve la compatibilité ascendante avec les versions antérieures de l’agent. Consultez le tableau suivant pour connaître les valeurs recommandées :

| PROPRIÉTÉ | DESCRIPTION |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | Nom de la société ou du site fourni lors de l’installation de l’agent |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | Chemin d’accès à votre interpréteur de ligne de commande PHP (généralement `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Répertoire racine où est installée votre application Adobe Commerce (généralement `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Utilisateur de base de données pour votre installation Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Mot de passe de la base de données de l’utilisateur spécifié pour votre installation Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Hôte de base de données de votre installation Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Nom de la base de données pour votre installation Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Port de base de données de votre installation Adobe Commerce (généralement `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Préfixe de tableau pour votre installation Adobe Commerce (valeur par défaut) : `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Si votre installation Adobe Commerce possède une instance de base de données secondaire (généralement `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | Répertoire temporaire de l’agent (généralement `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | Collecter les données lors de la première exécution (généralement `1`) |
| `SWAT_AGENT_LOG_LEVEL` | Détermine les événements consignés en fonction de la gravité (généralement `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | Active la mise à niveau automatique (redémarrage requis après une mise à niveau) ; l’agent ne vérifie pas les mises à niveau si l’option est désactivée ; `true` ou `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | Activation du mode sandbox pour utiliser l’agent dans l’environnement d’évaluation |

>[!INFO]
>
>Voir [Accès [!DNL Site-Wide Analysis Tool] et générer des rapports ;](../site-wide-analysis-tool/access.md).
