---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Mettre à jour le système de build

**Pour mettre à jour le système de build** :

1. Connectez-vous au système de génération en tant que propriétaire du système de fichiers.
1. Accédez au répertoire racine de l’application.

   ```shell
   cd <Magento root dir>
   ```

1. Extrayez les modifications apportées à `app/etc/config.php` à partir du contrôle de code source.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Compilez le code.

   ```shell
   bin/magento setup:di:compile
   ```

1. Une fois le code compilé, générez des fichiers de vue statiques.

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. Vérifiez les modifications dans le contrôle de code source.

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
