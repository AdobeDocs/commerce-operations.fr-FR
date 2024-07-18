---
title: Clonage des exemples de référentiels Git de données
description: Suivez ces étapes pour installer des exemples de données Adobe Commerce en clonant des référentiels Git.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Clonage des exemples de référentiels Git de données

Cette rubrique explique comment cloner et ajouter des données d’exemple si vous avez cloné le référentiel GitHub Magento Open Source. Cette méthode est destinée uniquement aux développeurs qui contribuent (c’est-à-dire aux développeurs qui prévoient de contribuer au code base du Magento Open Source).

Si vous n’êtes pas un développeur contributeur, sélectionnez l’une des autres options affichées dans la table des matières du côté gauche de la page.

Les développeurs contributeurs peuvent utiliser cette méthode pour installer des exemples de données *uniquement* si ce qui suit est vrai :

* Vous utilisez Magento Open Source
* Vous [ avez cloné le référentiel GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Vous pouvez utiliser des exemples de données avec la branche `develop` (plus actuelle) ou une branche publiée (comme `2.4` (plus stable)). Nous vous recommandons d’utiliser une branche publiée, car elle est plus stable. Si vous contribuez du code au référentiel et que vous avez besoin du code le plus récent, utilisez la branche `develop`. Quelle que soit la branche choisie, vous devez [cloner](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) la branche correspondante du référentiel GitHub du Magento Open Source. Par exemple, des exemples de données pour la branche `develop` peuvent être utilisés *uniquement* avec la branche `develop` du Magento Open Source.

## Clonage du référentiel de données d’exemple

Cette section explique comment installer des exemples de données en clonant le référentiel de données d’exemple. Vous pouvez cloner le référentiel de données d’exemple de l’une des manières suivantes :

* Cloner avec le [protocole SSH](#clone-with-ssh)
* Cloner avec le [protocole HTTPS](#clone-with-https)

### Clonage avec SSH

Pour cloner le référentiel GitHub de données d’exemple à l’aide du protocole SSH :

1. Dans un navigateur web, accédez au [référentiel de données d’exemple](https://github.com/magento/magento2-sample-data).
1. En regard du nom de la branche, cliquez sur **SSH** dans la liste.
1. Cliquez sur **Copier vers le presse-papiers**

   La figure suivante illustre un exemple.

   ![Cloner le référentiel GitHub à l’aide de SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Modifiez le répertoire docroot de votre serveur web.

   En règle générale, Ubuntu est `/var/www` et CentOS `/var/www/html`.

1. Saisissez `git clone` et collez la valeur obtenue précédemment.

   Voici un exemple :

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Attendez que le référentiel soit cloné sur votre serveur.

   >[!NOTE]
   >
   >Si l’erreur suivante s’affiche, assurez-vous que vous avez [partagé votre clé SSH](https://docs.github.com/articles/generating-ssh-keys/) avec GitHub:<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Assurez-vous d’extraire la branche de l’exemple de référentiel de données correspondant à la branche que vous avez utilisée à partir du référentiel principal `magento2`.

   Par exemple :

   Si vous avez utilisé la branche `2.4-develop` du référentiel GitHub du Magento Open Source, la branche Sample Data doit être `2.4-develop`.

   Pour extraire la branche correcte, exécutez la commande suivante à partir du répertoire racine du référentiel de données d’exemple (en supposant que vous ayez besoin de la branche `2.4-develop`) :

   ```bash
   git checkout 2.4-develop
   ```

1. Remplacez par `<app_root>`.
1. Saisissez la commande suivante pour créer des liens symboliques entre les fichiers que vous avez clonés afin que les exemples de données fonctionnent correctement :

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Attendez que la commande soit terminée.

1. Voir [Définition des droits d’accès et de la propriété du système de fichiers](#set-file-system-ownership-and-permissions).

1. Exécutez la commande suivante :

   ```bash
   bin/magento setup:upgrade
   ```

### Cloner avec HTTPS

Pour cloner le référentiel GitHub de données d’exemple à l’aide du protocole HTTPS :

1. Dans un navigateur web, accédez au [référentiel de données d’exemple](https://github.com/magento/magento2-sample-data).
1. Sur le côté droit de la page, sous le champ **clone URL**, cliquez sur **HTTPS**.
1. Cliquez sur **Copier dans le Presse-papiers**.

   La figure suivante illustre un exemple.

   ![Cloner le référentiel GitHub à l’aide de HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Modifiez le répertoire docroot de votre serveur web.

   En règle générale, Ubuntu est `/var/www` et CentOS `/var/www/html`.

1. Saisissez `git clone` et collez la valeur obtenue précédemment.

   Voici un exemple :

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Attendez que le référentiel soit cloné sur votre serveur.
1. Assurez-vous d’extraire la branche de l’exemple de référentiel de données correspondant à la branche que vous avez utilisée à partir du référentiel principal `magento2`.

   Par exemple :

   Si vous avez utilisé la branche `2.4-develop` du référentiel GitHub du Magento Open Source, la branche Sample Data doit être `2.4-develop`.

   Pour extraire la branche correcte, exécutez la commande suivante à partir du répertoire racine du référentiel de données d’exemple (en supposant que vous ayez besoin de la branche `2.4-develop`) :

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
1. Voir la section suivante.

>[!WARNING]
>
>Si vous installez des exemples de données *après* l&#39;installation d&#39;Adobe Commerce, vous devez également exécuter la commande suivante pour mettre à jour la base de données et le schéma :
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Définition de la propriété et des autorisations du système de fichiers

Comme le script `php build-sample-data.php` crée des liens symboliques entre le référentiel de données d’exemple et votre référentiel de Magento Open Source, vous devez définir les autorisations et la propriété du système de fichiers dans le référentiel de données d’exemple. Sinon, des erreurs d’accès au storefront seront générées.

Pour définir les autorisations et la propriété du système de fichiers sur l’exemple de référentiel de données :

1. Modifiez votre répertoire de clone de données d’exemple.
1. Définir la propriété :

   ```bash
   chown -R :<your web server group name> .
   ```

   Exemples types :

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

## Effectuez l’installation des exemples de données

{{$include /help/_includes/sample-data-complete.md}}
