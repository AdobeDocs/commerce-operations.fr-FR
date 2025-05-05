---
title: Appliquer les correctifs
description: Découvrez les méthodes d’application de correctifs à un projet Adobe Commerce.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Appliquer les correctifs

Vous pouvez appliquer des correctifs à l’aide de l’une des méthodes suivantes :

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr){target="_blank"}
- [Ligne de commande](../patches/apply.md#command-line)
- [Compositeur](../patches/apply.md#composer)


>[!TIP]
>
>Pour plus d’informations sur le correctif centralisé pour Adobe Commerce à l’échelle de l’entreprise, voir [bonnes pratiques](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) .

## Compositeur

>[!IMPORTANT]
>
>Pour appliquer des correctifs de qualité officiels, utilisez le [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr){target="_blank"}. Effectuez toujours des tests complets avant de déployer un correctif personnalisé.

Pour appliquer un correctif personnalisé à l’aide du compositeur :

1. Ouvrez votre application de ligne de commande et accédez au répertoire de votre projet.
1. Ajoutez le module externe `cweagans/composer-patches` au fichier `composer.json`.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Modifiez le fichier `composer.json` et ajoutez la section suivante pour spécifier :
   - **Module :** *\&quot;magento/module-payment\&quot;*
   - **Titre :** *\&quot;MAGETWO-56934 : la page de passage en caisse se bloque lors de la commande avec Authorize.net avec carte de crédit non valide\&quot;*
   - **Chemin vers le correctif :** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Par exemple :

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

1. Appliquez le correctif. Utilisez l’option `-v` uniquement si vous souhaitez afficher les informations de débogage.

   ```bash
   composer -v install
   ```

1. Mettez à jour le fichier `composer.lock`. Le fichier de verrouillage effectue le suivi des correctifs appliqués à chaque module de compositeur dans un objet.

   ```bash
   composer update --lock
   ```

## Ligne de commande

Pour appliquer des correctifs à partir de la ligne de commande :

1. Téléchargez le fichier local dans le répertoire `<Magento_root>` du serveur à l’aide de FTP, SFTP, SSH ou de votre méthode de transport normale.
1. Connectez-vous au serveur en tant qu’ [utilisateur admin](../../configuration/cli/config-cli.md#prerequisites) et vérifiez que le fichier se trouve dans le répertoire approprié.
1. Dans l&#39;interface de ligne de commande, exécutez les commandes suivantes en fonction de l&#39;extension de correctif :

   ```bash
   patch < patch_file_name.patch
   ```

   La commande suppose que le fichier à corriger se trouve par rapport au fichier de correctif.

   >[!NOTE]
   >
   >Si la ligne de commande affiche : `File to patch:`, cela signifie qu’il ne peut pas localiser le fichier prévu, même si le chemin semble correct. Dans la zone affichée dans le terminal de ligne de commande, la première ligne affiche le fichier à corriger. Copiez le chemin du fichier et collez-le dans l’invite `File to patch:` et appuyez sur `Enter` pour terminer le correctif.

1. Pour que les modifications soient prises en compte, actualisez le cache dans l’Admin sous **Système** > Outils > **Gestion du cache**.

   Sinon, le correctif peut être appliqué localement avec la même commande, puis validé et envoyé normalement.
