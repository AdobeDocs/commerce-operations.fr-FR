---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Mettre à jour la configuration partagée

**Mise à jour de la configuration**:

1. Connectez-vous à votre système de développement en tant que propriétaire du système de fichiers ou passez à .

1. Modifiez la racine de l’application et exécutez la commande dump .

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Par exemple, si Commerce est installé dans `/var/www/html/magento2`, saisissez :

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Confirmez que `app/etc/config.php` a été mis à jour.

   ```bash
   git status
   ```

   Exemple de réponse :

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Do _not_ d’envoyer les modifications au `generated`, `pub/media`, ou `pub/static` répertoires vers le contrôle source. Vous générez ces fichiers sur votre système de génération. Le système de développement comporte probablement du code, des thèmes, etc., qui ne sont pas prêts à être utilisés dans le système de production.

1. Archivez vos modifications dans `app/etc/config.php` uniquement au contrôle de code source.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
