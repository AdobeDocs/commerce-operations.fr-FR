---
title: Guide d’installation
description: Utilisation de ce guide pour l’installation [!DNL Site-Wide Analysis Tool] pour votre site web
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
source-git-commit: 4210746509be99bb3c943906c99f70ea420ba74a
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---

# Guide d’installation

Le [!DNL Site-Wide Analysis Tool] fournit 24/7 surveillance des performances, rapports et recommandations en temps réel pour garantir la sécurité et la maniabilité d’Adobe Commerce sur les installations d’infrastructure cloud. Il fournit également des informations détaillées sur les correctifs disponibles et installés, les extensions tierces et votre installation Adobe Commerce.

>[!INFO]
>
>En savoir plus [procédure d’activation](../site-wide-analysis-tool/access.md) la valeur [!DNL Site-Wide Analysis Tool] et générer des rapports.

Si vous disposez d’une installation sur site d’Adobe Commerce, installez un agent sur votre infrastructure pour utiliser l’outil. Vous n’avez pas besoin d’installer l’agent sur Adobe Commerce sur les projets d’infrastructure cloud.

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
>L’agent prend en charge les installations Adobe Commerce à plusieurs noeuds. Installez et configurez l’agent sur chaque noeud.

## Configuration requise

Votre infrastructure sur site doit répondre aux exigences suivantes avant d’installer l’agent :

- Systèmes d’exploitation

   - [!DNL Linux x86-64] les distributions, telles que [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], et similaires
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
bin/magento module:status Magento_ServicesId
```

Si vous avez installé l’extension et l’avez configurée à l’aide d’une clé d’API existante pour un autre service, vous **DOIT régénérer la clé API** et mettez-le à jour dans l’administrateur Adobe Commerce de l’agent.

1. Insérer votre site web dans [mode de maintenance](../../installation/tutorials/maintenance-mode.md).

1. Se connecter [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Si vous rencontrez des problèmes pour accéder à votre compte, reportez-vous à la section [Impossible de se connecter au support Adobe Commerce ou au compte cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) pour obtenir de l’aide sur la résolution des problèmes.

1. Cliquez sur **[!UICONTROL API Portal]**.

1. Cliquez sur **[!UICONTROL Delete]** en regard de la clé API existante.

1. [Configurer](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) une nouvelle clé API.

>[!IMPORTANT]
>
> Si vous générez de nouvelles clés dans le portail API, mettez immédiatement à jour les clés API dans la variable [!DNL Admin configuration]. Si vous générez de nouvelles clés et que vous ne mettez pas à jour les clés dans la variable [!DNL Admin], vos extensions SaaS ne fonctionneront plus et vous perdrez des données importantes.

Si l’extension n’est pas installée, procédez comme suit pour l’installer :

1. Ajoutez l’extension à votre `composer.json` et installez-le.

   ```bash
   composer require magento/services-id
   ```

1. Activez l’extension .

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Mettez à jour le schéma de la base de données.

   ```bash
   bin/magento setup:upgrade
   ```

1. Effacez le cache.

   ```bash
   bin/magento cache:clean
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

1. Après avoir téléchargé et installé l’agent, [configurer son exécution](#run-the-agent) en utilisant l’une des méthodes suivantes :

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
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Décompressez l’archive du lanceur.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   Pour le **ARM64** architecture :

   1. Téléchargez l’archive du lanceur.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
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

1. Création d’un fichier d’unité systemd `(/etc/systemd/system/scheduler.service)` avec la configuration suivante (remplacez `<filesystemowner>` avec l’utilisateur UNIX® propriétaire du répertoire dans lequel l’agent et le logiciel Adobe Commerce sont installés). Si vous avez téléchargé l’agent en tant qu’utilisateur root, modifiez le répertoire et le propriétaire des fichiers imbriqués.

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

## Dépannage

### Clés d’accès non analysées correctement

L’erreur suivante peut s’afficher si vos clés d’accès ne sont pas correctement analysées :

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Pour résoudre cette erreur, procédez comme suit :

1. Effectuez une [installation par script](#scripted), enregistrez la sortie et vérifiez la sortie pour les erreurs.
1. Vérifiez les `config.yaml` et vérifiez que le chemin d’accès à votre instance Commerce et à votre instance PHP est correct.
1. Assurez-vous que l’utilisateur qui exécute le planificateur se trouve dans la variable [propriétaire du système de fichiers](../../installation/prerequisites/file-system/overview.md) Groupe Unix ou est le même utilisateur que le propriétaire du système de fichiers.
1. Assurez-vous que la variable [Connecteur Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) les clés sont correctement installées et essayez de les mettre à jour pour connecter l’extension à votre système.
1. [Désinstaller](#uninstall) l’agent après la mise à jour des clés et la réinstallation à l’aide de la fonction [script d’installation](#scripted).
1. Exécutez le planificateur et vérifiez si vous recevez toujours la même erreur.
1. Si vous recevez toujours la même erreur, augmentez le niveau de journalisation dans la variable `config.yaml` pour déboguer et ouvrir un ticket d’assistance.

### *SIGFAULT* Erreur

Si une *SIGFAULT* lors de l’exécution du fichier binaire, vous ne l’exécutez probablement pas en tant que propriétaire de fichier des fichiers Adobe Commerce et Agent.
Pour résoudre ce problème, vérifiez si tous les fichiers du répertoire de l’agent qui ont le même utilisateur que le propriétaire de fichier que les fichiers Adobe Commerce et le fichier binaire doivent être exécutés sous cet utilisateur.
Vous pouvez utiliser la variable `chown` pour modifier le propriétaire des fichiers et passer à l’utilisateur approprié.
Assurez-vous que votre mécanisme de démonisation (Cron ou System.d) exécute le processus sous l’utilisateur approprié.

>[!INFO]
>
>Voir [Accès [!DNL Site-Wide Analysis Tool] et générer des rapports ;](../site-wide-analysis-tool/access.md).
