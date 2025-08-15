---
title: Application de correctifs
description: Découvrez les méthodes d’application de correctifs à un projet Adobe Commerce.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Application de correctifs

Vous pouvez appliquer des correctifs à l’aide de l’une des méthodes suivantes :

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr){target="_blank"}
- [Ligne de commande](../patches/apply.md#command-line)
- [Compositeur](../patches/apply.md#composer)


>[!TIP]
>
>Consultez [Bonnes pratiques](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) pour plus d’informations sur l’application de correctifs centralisée pour Adobe Commerce à l’échelle de l’entreprise.

## Compositeur

>[!IMPORTANT]
>
>Pour appliquer les correctifs de qualité officiels, utilisez le [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr){target="_blank"} . Effectuez toujours des tests complets avant de déployer un correctif personnalisé.

Pour appliquer un correctif personnalisé à l’aide du compositeur :

1. Ouvrez votre application de ligne de commande et accédez au répertoire du projet.
1. Ajoutez le module externe `cweagans/composer-patches` au fichier `composer.json`.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Modifiez le fichier `composer.json` et ajoutez la section suivante pour spécifier :
   - **Module:** *\« magento/module-pay\ »*
   - **Title:** *\« MAGETWO-56934 : la page de passage en caisse se fige lors de la commande avec Authorize.net avec une carte de crédit non valide\ »*
   - **Chemin d’accès au correctif :** *\ »patches/composer/github-issue-6474.diff\ »*

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

1. Appliquez le correctif. N’utilisez l’option `-v` que si vous souhaitez afficher les informations de débogage.

   ```bash
   composer -v install
   ```

1. Mettez à jour le fichier `composer.lock`. Le fichier de verrouillage effectue le suivi des correctifs qui ont été appliqués à chaque package du compositeur dans un objet .

   ```bash
   composer update --lock
   ```

## Ligne de commande

Pour appliquer des correctifs à partir de la ligne de commande :

1. Chargez le fichier local dans le répertoire `<Magento_root>` du serveur par FTP, SFTP, SSH ou votre méthode de transport normale.
1. Connectez-vous au serveur en tant qu’[utilisateur administrateur](../../configuration/cli/config-cli.md#prerequisites) et vérifiez que le fichier se trouve dans le répertoire approprié.
1. Dans l’interface de ligne de commande, exécutez les commandes suivantes en fonction de l’extension de correctif :

   ```bash
   patch < patch_file_name.patch
   ```

   La commande suppose que le fichier à corriger se trouve par rapport au fichier de correctif.

   >[!NOTE]
   >
   >Si la ligne de commande indique : `File to patch:`, cela signifie qu’elle ne peut pas localiser le fichier prévu, même si le chemin d’accès semble correct. Dans la zone affichée dans le terminal de ligne de commande, la première ligne indique le fichier à corriger. Copiez le chemin d’accès au fichier et collez-le dans l’invite de `File to patch:`, appuyez sur `Enter` et le correctif doit être terminé.

1. Pour que les modifications soient répercutées, actualisez le cache dans Admin sous **Système** > Outils > **Gestion du cache**.

   Alternativement, le correctif peut être appliqué localement avec la même commande, puis validé et poussé normalement.
