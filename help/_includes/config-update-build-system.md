---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Mettre à jour le système de génération

**Mise à jour du système de génération**:

1. Connectez-vous au système de génération en tant que propriétaire du système de fichiers.
1. Modifiez le répertoire racine de l’application.

   ```bash
   cd <Magento root dir>
   ```

1. Extrayez les modifications dans `app/etc/config.php` du contrôle source.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Compilez du code.

   ```bash
   bin/magento setup:di:compile
   ```

1. Une fois le code compilé, générez des fichiers d’affichage statiques.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Vérifiez les modifications dans le contrôle de code source.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
