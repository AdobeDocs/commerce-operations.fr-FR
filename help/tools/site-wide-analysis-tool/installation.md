---
title: Guide d’installation
description: Utilisez ce guide pour installer  [!DNL Site-Wide Analysis Tool]  pour votre site web
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Guide d’installation

>[!IMPORTANT]
>
>À compter du 23 avril 2024, le [!DNL Site-Wide Analysis Tool] sera mis hors service pour tous les clients sur site d’Adobe Commerce.

Le [!DNL Site-Wide Analysis Tool] fournit une surveillance des performances en temps réel, des rapports et des recommandations 24h/24 et 7j/7 pour assurer la sécurité et l’opérabilité d’Adobe Commerce sur les installations d’infrastructure cloud. Elle fournit également des informations détaillées sur les correctifs disponibles et installés, les extensions tierces et votre installation Adobe Commerce.

>[!INFO]
>
>Découvrez [comment activer](../site-wide-analysis-tool/access.md) le [!DNL Site-Wide Analysis Tool] et générer des rapports.

Si vous disposez d’une installation locale de Adobe Commerce, installez un agent sur votre infrastructure pour utiliser l’outil. Vous n’avez pas besoin d’installer l’agent sur Adobe Commerce sur des projets d’infrastructure cloud.

## Agent

L’agent [!DNL Site-Wide Analysis Tool] vous permet d’utiliser la pour les [!DNL Site-Wide Analysis Tool] installations locales d’Adobe Commerce.

L’agent [!DNL Site-Wide Analysis Tool] collecte les données d’application et d’entreprise, les analyse et fournit des informations supplémentaires sur l’intégrité de votre installation afin que vous puissiez améliorer l’expérience client. Il surveille votre application et vous aide à identifier les problèmes de performances, de sécurité, de disponibilité et d’application.

L’installation de l’agent requiert les étapes suivantes :

1. Vérifiez la configuration système requise.

1. Configurez les clés API dans l’extension [!UICONTROL Commerce Services Connector].

1. Installez l’agent.

1. Exécutez l’agent.

>[!INFO]
>
>L’agent prend en charge les installations multi-nœuds Adobe Commerce. Installez et configurez l’agent sur chaque nœud.

## Configuration requise

Votre infrastructure locale doit répondre aux exigences suivantes avant d’installer l’agent :

- Systèmes d’exploitation

   - [!DNL Linux x86-64] distributions, telles que [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], etc

  >[!IMPORTANT]
  >
  >Adobe Commerce n’est pas pris en charge sur [!DNL Microsoft Windows] ou [!DNL macOS].

- Adobe Commerce 2.4.5-p1 ou version ultérieure (en raison de la dépendance de Service Connector)

- [!DNL Commerce Services Connector extension]

- CLI PHP

- Utilitaires Bash/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

L’agent nécessite que l’extension soit installée sur votre système et [configurée](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) avec des [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) clés API. Pour vérifier que l’extension est bien installée, exécutez la commande suivante :

```bash
bin/magento module:status Magento_ServicesId
```

Si vous avez installé l’extension et l’avez configurée à l’aide d’une clé d’API existante pour un autre service, vous **DEVEZ régénérer la clé** d’API et la mettre à jour dans l’administrateur Adobe Commerce de l’agent.

1. Mettez votre site Web en [mode](../../installation/tutorials/maintenance-mode.md) de maintenance.

1. Connectez-vous à [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Si vous ne parvenez pas à accéder à votre compte, consultez [Impossible de se connecter au support Adobe Commerce ou au compte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) cloud pour obtenir de l’aide sur la résolution des problèmes.

1. Cliquez sur **[!UICONTROL API Portal]**.

1. Cliquez **[!UICONTROL Delete]** en regard de la clé API existante.

1. [Configurez](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) une nouvelle clé API.

>[!IMPORTANT]
>
> Si vous générez de nouvelles clés dans le portail API, mettez immédiatement à jour les clés API dans le [!DNL Admin configuration]fichier . Si vous générez de nouvelles clés et ne mettez pas à jour les clés dans le [!DNL Admin], vos extensions SaaS ne fonctionneront plus et vous perdrez des données précieuses.

Si l’extension n’est pas installée, suivez les instructions suivantes pour l’installer :

1. Ajoutez l’extension à votre `composer.json` fichier et installez-la.

   ```bash
   composer require magento/services-id
   ```

1. Activez l’extension.

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

1. [Configurez les clés API pour](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) connecter l’extension à votre système.

## Installation de l’agent

Nous avons créé un [script](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) shell pour simplifier l’installation. Nous vous recommandons d’utiliser le script shell, mais vous pouvez suivre la méthode d’installation[&#128279;](#manual) manuelle si nécessaire.

>[!INFO]
>
>Une fois l’agent installé, il se met à jour automatiquement lorsqu’une nouvelle version est disponible.

### Script

1. Téléchargez et exécutez le script shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Nous vous recommandons d’installer l’agent en dehors du répertoire de votre projet Adobe Commerce racine.

1. Vérifiez l’installation.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Après avoir téléchargé et installé l’agent, configurez-le [pour qu’il s’exécute](#run-the-agent) à l’aide de l’une des méthodes suivantes :

   - [Service](#service) (de préférence si vous avez un accès root)

   - [Cron](#cron)

### Manuelle {#manual}

Si vous ne souhaitez pas utiliser notre [script](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) shell pour installer l’agent, vous devez l’installer manuellement en procédant comme suit :

1. Créez un répertoire dans lequel vous souhaitez télécharger l’agent.

   >[!TIP]
   >
   >Nous vous recommandons d’installer l’agent en dehors du répertoire de votre projet Adobe Commerce racine.

1. Téléchargez le fichier binaire et décompressez-le.

   >[!INFO]
   >
   >Pour utiliser le [!DNL Site-Wide Analysis Tool], vous devez d’abord lire et accepter les conditions d’utilisation qui sont présentées lorsque vous accédez au tableau de bord à partir de l’administrateur Adobe Commerce.

   Pour l’architecture **AMD64** :

   1. Téléchargez l’archive du lanceur.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Décompressez l’archive du lanceur.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Pour l’architecture **ARM64** :

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

1. Créez le fichier `config.yaml` avec le contenu suivant.

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

1. Après avoir téléchargé et installé l’agent, vous devez [le configurer pour qu’il s’exécute](#run-the-agent) à l’aide de l’une des méthodes suivantes :

   - [Service](#service) (de préférence si vous avez un accès root)

   - [Cron](#cron)

## Exécuter l’agent {#run-the-agent}

Nous vous recommandons de configurer l’agent pour qu’il s’exécute en tant que service. Si vous avez un accès limité à votre infrastructure et ne disposez pas des autorisations root, vous devez utiliser [cron](#cron) à la place.

### Service {#service}

1. Créez un fichier `(/etc/systemd/system/scheduler.service)` d’unité systemd avec la configuration suivante (remplacez `<filesystemowner>` par l’utilisateur UNIX® propriétaire du répertoire où l’agent et le logiciel Adobe Commerce sont installés). Si vous avez téléchargé l’agent en tant qu’utilisateur root, modifiez le propriétaire du répertoire et des fichiers imbriqués.

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

1. Launch le service.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Vérifiez que le service est opérationnel.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Si vous ne disposez pas des autorisations root ou de configurer un service en tant que root, vous pouvez utiliser cron à la place.

Mettez à jour la planification cron :

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

1. Supprimez le fichier d’unité du service de `systemd` planification.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Rechargez la configuration du `systemd` gestionnaire.

   ```bash
   systemctl daemon-reload
   ```

1. Réinitialisez toutes les `systemd` unités d’un état d’échec.

   ```bash
   systemctl reset-failed
   ```

1. Supprimez le répertoire du service de planification.

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

1. Arrêtez le traitement en cours.

   ```bash
   ps aux | grep scheduler
   ```

1. Supprimez le répertoire dans lequel vous avez installé l’agent.

   ```bash
   rm -rf swat-agent
   ```

## Dépannage

### Clés d’accès non analysées correctement

L’erreur suivante peut s’afficher si vos clés d’accès ne sont pas analysées correctement :

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Pour résoudre cette erreur, essayez les étapes suivantes :

1. Effectuez une [installation par script](#scripted), enregistrez la sortie et recherchez les erreurs éventuelles dans la sortie.
1. Vérifiez le fichier `config.yaml` généré et vérifiez que le chemin d&#39;accès à votre instance Commerce et PHP est correct.
1. Assurez-vous que l’utilisateur qui exécute le planificateur appartient au groupe[&#128279;](../../installation/prerequisites/file-system/overview.md) Unix propriétaire du système de fichiers ou est le même utilisateur que le propriétaire du système de fichiers.
1. Assurez-vous que les clés du [connecteur](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html) Commerce Services sont correctement installées et essayez de les mettre à jour pour connecter l’extension à votre système.
1. [Désinstallez](#uninstall) l’agent après la mise à jour des clés et réinstallez-le à l’aide du script[&#128279;](#scripted) d’installation.
1. Exécutez le planificateur et voyez si la même erreur persiste.
1. Si la même erreur persiste, augmentez le niveau de journalisation dans le `config.yaml` pour déboguer et ouvrez un ticket de support.

### *Erreur SIGFAULT*

Si vous voyez une *erreur SIGFAULT* lors de l’exécution du fichier binaire, vous ne l’exécutez probablement pas en tant que propriétaire du fichier de Adobe fichiers Commerce et Agent.
Pour résoudre ce problème, veuillez vérifier si tous les fichiers à l’intérieur du répertoire de l’agent qui ont le même utilisateur que le propriétaire du fichier que les fichiers Adobe Commerce ont, et binaire doivent également être exécutés sous cet utilisateur.
Vous pouvez utiliser la `chown` commande pour modifier le propriétaire des fichiers et basculer vers l’utilisateur approprié.
Assurez-vous que votre mécanisme de démonisation (Cron ou System.d) exécute le processus sous l’utilisateur approprié.

>[!INFO]
>
>Voir [Comment accéder [!DNL Site-Wide Analysis Tool] aux rapports](../site-wide-analysis-tool/access.md) et les générer.
