---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Mise à jour de la configuration partagée

**Pour mettre à jour la configuration** :

1. Connectez-vous à votre système de développement en tant que propriétaire du système de fichiers ou passez à ce système.

1. Passez à la racine de l’application et exécutez la commande dump.

   ```shell
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Par exemple, si Commerce est installé dans `/var/www/html/magento2`, saisissez :

   ```shell
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Vérifiez que `app/etc/config.php` a été mis à jour.

   ```shell
   git status
   ```

   Exemple de réponse :

   ```text
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >N’envoyez _pas_ les modifications apportées aux répertoires `generated`, `pub/media` ou `pub/static` au contrôle de code source. Vous générez ces fichiers sur votre système de génération. Le système de développement comporte probablement du code, des thèmes, etc., qui ne sont pas prêts à être utilisés sur le système de production.

1. Archivez vos modifications dans `app/etc/config.php` uniquement au contrôle de code source.

   ```shell
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
