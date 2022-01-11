---
title: Appliquer les correctifs
description: Découvrez les méthodes d’application de correctifs à un projet Adobe Commerce ou Magento Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Appliquer les correctifs

Vous pouvez appliquer des correctifs à l’aide de l’une des méthodes suivantes :

- [Outil Correctifs de qualité](https://devdocs.magento.com/quality-patches/tool.html)
- [Ligne de commande](../patches/apply.md#command-line)
- [Compositeur](../patches/apply.md#composer)

## Compositeur

>[!IMPORTANT]
>
>Pour appliquer des correctifs de qualité officiels, utilisez la méthode [Outil Correctifs de qualité](https://devdocs.magento.com/quality-patches/tool.html). Effectuez toujours des tests complets avant de déployer un correctif personnalisé.

Pour appliquer un correctif personnalisé à l’aide du compositeur :

1. Ouvrez votre application de ligne de commande et accédez au répertoire de votre projet.
1. Ajoutez la variable `cweagans/composer-patches` du module externe `composer.json` fichier .

   ```bash
   composer require cweagans/composer-patches
   ```

1. Modifiez la variable `composer.json` et ajoutez la section suivante pour spécifier :
   - **Module :** *\&quot;magento/module-payment\&quot;*
   - **Titre :** *\&quot;MAGETTwo-56934 : La page de paiement se bloque lors de la commande avec Authorize.net avec une carte de crédit non valide\&quot;*
   - **Chemin d’accès au correctif :** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Par exemple :

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Si un correctif affecte plusieurs modules, vous devez créer plusieurs fichiers de correctif ciblant plusieurs modules.

1. Appliquez le correctif. Utilisez la variable `-v` uniquement si vous souhaitez afficher les informations de débogage.

   ```bash
   composer -v install
   ```

1. Mettez à jour le `composer.lock` fichier . Le fichier de verrouillage effectue le suivi des correctifs appliqués à chaque module de compositeur dans un objet.

   ```bash
   composer update --lock
   ```

## Ligne de commande

Pour appliquer des correctifs à partir de la ligne de commande :

1. Téléchargez le fichier local dans le `<Magento_root>` sur le serveur à l’aide de FTP, SFTP, SSH ou de votre méthode de transport normale.
1. Connectez-vous au serveur en tant que [utilisateur administrateur](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli.html#config-install-cli-first) et vérifiez que le fichier se trouve dans le répertoire approprié.
1. Dans l&#39;interface de ligne de commande, exécutez les commandes suivantes en fonction de l&#39;extension de correctif :

   ```bash
   patch < patch_file_name.patch
   ```

   La commande suppose que le fichier à corriger se trouve par rapport au fichier de correctif.

   >[!NOTE]
   >
   >Si la ligne de commande affiche : `File to patch:`, cela signifie qu’il ne peut pas localiser le fichier prévu, même si le chemin semble correct. Dans la zone affichée dans le terminal de ligne de commande, la première ligne affiche le fichier à corriger. Copiez le chemin du fichier et collez-le dans le `File to patch:` invite et appuyez sur `Enter` et le correctif doit être terminé.

1. Pour que les modifications soient répercutées, actualisez le cache dans l’Admin sous **Système** > Outils > **Gestion du cache**.

   Sinon, le correctif peut être appliqué localement avec la même commande, puis validé et envoyé normalement.
