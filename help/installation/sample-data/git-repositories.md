---
title: Clonage de référentiels Git de données d’exemple
description: Pour installer les données d’exemple d’Adobe Commerce en clonant les référentiels Git, procédez comme suit.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Clonage de référentiels Git de données d’exemple

Cette rubrique explique comment cloner et ajouter des données d’exemple si vous avez cloné le référentiel GitHub de Magento Open Source. Cette méthode est destinée uniquement aux développeurs contributeurs (c’est-à-dire aux développeurs qui prévoient de contribuer à la base de code Magento Open Source).

Si vous n’êtes pas un développeur participant, choisissez l’une des autres options affichées dans la table des matières sur le côté gauche de la page.

Les développeurs contributeurs peuvent utiliser cette méthode d’installation des données d’exemple *uniquement* si ce qui suit est vrai :

* Vous utilisez Magento Open Source
* Vous [&#x200B; cloné le référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Vous pouvez utiliser des données d’exemple avec la branche `develop` (plus récente) ou une branche publiée (telle que `2.4` (plus stable)). Nous vous recommandons d’utiliser une branche publiée, car elle est plus stable. Si vous apportez du code au référentiel et que vous avez besoin du code le plus récent, utilisez la branche `develop`. Quelle que soit la branche que vous choisissez, vous devez [cloner](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) la branche correspondante du référentiel GitHub Magento Open Source. Par exemple, les exemples de données pour la branche `develop` peuvent être utilisés *uniquement* avec la branche Magento Open Source `develop`.

## Cloner le référentiel de données d’exemple

Cette section explique comment installer des données d’exemple en clonant le référentiel de données d’exemple. Vous pouvez cloner le référentiel de données d’exemple de l’une des manières suivantes :

* Clonez avec le protocole [SSH](#clone-with-ssh)
* Clonez avec le [protocole HTTPS](#clone-with-https)

### Cloner avec SSH

Pour cloner le référentiel GitHub de données d’exemple à l’aide du protocole SSH :

1. Dans un navigateur web, accédez au [référentiel de données d’exemple](https://github.com/magento/magento2-sample-data).
1. En regard du nom de la branche, cliquez sur **SSH** dans la liste.
1. Cliquez sur **Copier dans le presse-papiers**

   La figure suivante en est un exemple.

   ![Cloner le référentiel GitHub à l’aide de SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Accédez au répertoire racine du serveur web.

   En général, pour Ubuntu, c&#39;est `/var/www` et pour CentOS, c&#39;est `/var/www/html`.

1. Saisissez `git clone` et collez la valeur obtenue précédemment.

   Voici un exemple :

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Attendez que le référentiel soit cloné sur votre serveur.

   >[!NOTE]
   >
   >Si l’erreur suivante s’affiche, veillez à [partager votre clé SSH](https://docs.github.com/articles/generating-ssh-keys/) avec GitHub:<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Veillez à extraire la branche du référentiel de données d’exemple qui correspond à la branche que vous avez utilisée à partir du référentiel de `magento2` principal.

   Par exemple :

   Si vous avez utilisé la branche `2.4-develop` du référentiel GitHub de Magento Open Source, la branche Données d’exemple doit être `2.4-develop`.

   Pour extraire la branche appropriée, exécutez la commande suivante à partir du répertoire racine du référentiel de données d’exemple (en supposant que vous ayez besoin de la branche `2.4-develop`) :

   ```bash
   git checkout 2.4-develop
   ```

1. Remplacez par `<app_root>`.
1. Saisissez la commande suivante pour créer des liens symboliques entre les fichiers que vous avez clonés afin que les exemples de données fonctionnent correctement :

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Attendez que la commande soit terminée.

1. Voir [&#x200B; Définir les autorisations et la propriété du système de fichiers](#set-file-system-ownership-and-permissions).

1. Exécutez la commande suivante :

   ```bash
   bin/magento setup:upgrade
   ```

### Cloner avec HTTPS

Pour cloner le référentiel GitHub de données d’exemple à l’aide du protocole HTTPS :

1. Dans un navigateur web, accédez au [référentiel de données d’exemple](https://github.com/magento/magento2-sample-data).
1. Dans la partie droite de la page, sous le champ **Cloner l’URL**, cliquez sur **HTTPS**.
1. Cliquez sur **Copier dans le presse-papiers**.

   La figure suivante en est un exemple.

   ![Cloner le référentiel GitHub à l’aide de HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Accédez au répertoire racine du serveur web.

   En général, pour Ubuntu, c&#39;est `/var/www` et pour CentOS, c&#39;est `/var/www/html`.

1. Saisissez `git clone` et collez la valeur obtenue précédemment.

   Voici un exemple :

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Attendez que le référentiel soit cloné sur votre serveur.
1. Veillez à extraire la branche du référentiel de données d’exemple qui correspond à la branche que vous avez utilisée à partir du référentiel de `magento2` principal.

   Par exemple :

   Si vous avez utilisé la branche `2.4-develop` du référentiel GitHub de Magento Open Source, la branche Données d’exemple doit être `2.4-develop`.

   Pour extraire la branche appropriée, exécutez la commande suivante à partir du répertoire racine du référentiel de données d’exemple (en supposant que vous ayez besoin de la branche `2.4-develop`) :

   ```bash
   git checkout 2.4-develop
   ```

1. Remplacez par `<magento_root>`.
1. Saisissez la commande suivante pour créer des liens symboliques entre les fichiers que vous avez clonés afin que les exemples de données fonctionnent correctement :

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Par exemple,

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Attendez que la commande soit terminée.
1. Pour plus d&#39;informations, consultez la section suivante.

>[!WARNING]
>
>Si vous installez des données d’exemple *après* avoir installé Adobe Commerce, vous devez également exécuter la commande suivante pour mettre à jour la base de données et le schéma :
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Définition de la propriété et des autorisations du système de fichiers

Étant donné que le script `php build-sample-data.php` crée des liens symboliques entre le référentiel de données d’exemple et votre référentiel Magento Open Source, vous devez définir les autorisations et la propriété du système de fichiers dans le référentiel de données d’exemple. Dans le cas contraire, des erreurs se produisent lors de l’accès au storefront.

Pour définir les autorisations et la propriété du système de fichiers sur le référentiel de données d’exemple :

1. Accédez à votre répertoire de clone de données d’exemple.
1. Définir la propriété :

   ```bash
   chown -R :<your web server group name> .
   ```

   Exemples typiques :

   * CentOS : `chown -R :apache .`

   * Ubuntu : `chown -R :www-data .`

1. Définissez les autorisations :

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Effacer les fichiers statiques :

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Terminer l’installation des données d’exemple

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
