---
title: Bonnes pratiques de distribution des correctifs à grande échelle
description: Découvrez comment les correctifs centralisés pour Adobe Commerce peuvent vous aider à gérer les projets d’entreprise.
role: Developer
feature: Best Practices
badge: label="Contribution de Tony Evers, architecte technique principal, Adobe" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="Contribution Tony Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Bonnes pratiques pour distribuer les correctifs Adobe Commerce à grande échelle

Si vous gérez plusieurs installations d’Adobe Commerce, l[application de correctifs](../../../upgrade/patches/apply.md) peut s’avérer un processus complexe. _Application de correctifs centralisée_ est une bonne pratique pour les entreprises. Vous pouvez ainsi appliquer les correctifs appropriés sur toutes vos installations Adobe Commerce. Cette rubrique explique comment obtenir une distribution centralisée des correctifs pour tous les types de [ Adobe Commercecorrectifs](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Le contenu suivant a été initialement publié dans l’article [ Distribution des correctifs Adobe Commerce à l’échelle ](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) sur le blog Adobe Tech. Il a été modifié pour se concentrer sur les étapes et les exemples de code pour la mise en œuvre d&#39;une stratégie de correctifs centralisée. Voir la publication d’origine pour plus d’informations sur les différents types de correctifs décrits ici.

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur les infrastructures cloud
- Adobe Commerce on-premise

## Stratégie

Comme il existe de nombreux types de correctifs et de nombreuses façons de les appliquer, comment savoir quel correctif est appliqué en premier ? Plus vous avez de correctifs, plus il y a de chances qu’ils s’appliquent au même fichier ou à la même ligne de code. Les correctifs sont appliqués dans l’ordre suivant :

1. Les **correctifs de sécurité** font partie de la base de code statique d’une version d’Adobe Commerce.
1. **Correctifs du compositeur** via des modules externes `composer install` et `composer update` tels que [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Tous les **correctifs requis** inclus dans le package [Correctifs cloud pour Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).
1. Sélection **correctifs de qualité** inclus dans le [[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md).
1. **Correctifs personnalisés** et les correctifs Adobe Commerce prennent en charge les correctifs du répertoire `/m2-hotfixes` dans l’ordre alphabétique par nom de correctif.

   >[!IMPORTANT]
   >
   >Plus vous appliquez de correctifs, plus votre code devient complexe. Un code complexe peut rendre la mise à niveau vers une nouvelle version d’Adobe Commerce plus difficile et augmenter votre coût total de possession.

Si vous êtes responsable de la maintenance de plusieurs installations d’Adobe Commerce, il peut être difficile de s’assurer que toutes les instances disposent du même ensemble de correctifs. Chaque installation possède son propre référentiel Git, son propre répertoire `/m2-hotfixes` et son propre fichier `composer.json`. La seule garantie que vous avez est que les **correctifs de sécurité** et **correctifs requis** pour les utilisateurs du cloud sont tous installés dans le cadre de votre version Adobe Commerce principale.

Actuellement, il n’existe pas de solution centralisée unique à ce problème, mais le compositeur offre un moyen de combler le fossé. Le package [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) vous permet d’appliquer [ des correctifs à partir de dépendances ](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Vous pouvez créer un package de compositeur qui installe tous les correctifs, puis qui requiert ce package dans tous vos projets.

Cela couvre les **correctifs de sécurité**, **correctifs requis** et **correctifs du compositeur**, mais qu’en est-il des correctifs de qualité et du contenu du répertoire `/m2-hotfixes` ?

## Application de correctifs de qualité et de correctifs

Vous pouvez installer des correctifs de qualité sur les installations sur site et sur l’infrastructure cloud à l’aide de la commande `vendor/bin/magento-patches apply`. Vous devez vous assurer que la commande `vendor/bin/magento-patches apply` s’exécute après les opérations `composer install`.

>[!NOTE]
>
>Sur les infrastructures cloud, vous pouvez également installer des correctifs de qualité en les répertoriant dans le fichier `.magento.env.yaml` de votre projet. L’exemple décrit ici nécessite l’utilisation de la commande `vendor/bin/magento-patches apply` .

Vous pouvez spécifier les correctifs à appliquer dans le fichier `composer.json` d’un package de composant du compositeur personnalisé, puis créer un package de module externe qui exécute la commande après `composer install` opérations.

En résumé, cet exemple de correctif centralisé nécessite que vous créiez deux packages Composer personnalisés :

- **Package de composants :** `centralized-patcher`

   - Définit la liste des correctifs de qualité et des `m2-hotfixes` à installer
   - Nécessite le package `centralized-patcher-composer-plugin`, qui exécute la commande `vendor/bin/magento-patches apply` après `composer install` opérations

- **Package de plug-in :** `centralized-patcher-composer-plugin`

   - Définit une classe PHP `CentralizedPatcher` qui lit la liste des patchs de qualité à partir du package `centralized-patcher`
   - Exécute la commande `vendor/bin/magento-patches apply` pour installer la liste des correctifs de qualité après `composer install` opérations

### `centralized-patcher`

Vous pouvez créer un package de composant Compositeur (`centralized-patcher`) afin de gérer de manière centralisée tous les correctifs et `/m2-hotfixes` de qualité pour toutes vos installations Adobe Commerce.

Le package de composants doit :

- Copiez le contenu du répertoire `/m2-hotfixes` dans toutes vos installations lors du déploiement.
- Définissez la liste des correctifs de qualité à installer.
- Exécutez la commande `vendor/bin/magento-patches` pour installer la même liste de correctifs de qualité sur toutes les installations (en utilisant le package de plug-in [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) comme dépendance).

Pour créer le package de composants `centralized-patcher` :

1. Créez un fichier `composer.json` avec les contenus suivants :

   >[!NOTE]
   >
   >L’attribut `require` dans l’exemple suivant illustre une dépendance `require` au package [plugin](#centralized-patcher-composer-plugin) que vous devez créer ultérieurement dans cet exemple.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Créez un répertoire `/m2-hotfixes` dans votre package et ajoutez-le à l’attribut `map` dans votre fichier `composer.json`. L’attribut `map` contient les fichiers à copier de ce package dans la racine du projet cible auquel vous souhaitez appliquer un correctif.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >Le package `centralized-patcher` copie le contenu du répertoire `/m2-hotfixes` dans le répertoire m2-hotfixes du projet cible sur `composer install`.  Comme les scripts de déploiement cloud appliquent des correctifs m2 après `composer install`, tous les correctifs sont installés par le mécanisme de déploiement.

1. Définissez les correctifs de qualité à installer dans l’attribut `quality-patches`.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


L’attribut `quality-patches` de l’exemple de code précédent contient deux correctifs de la [liste complète des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) à titre d’exemple.  Ces correctifs de qualité sont installés sur chaque projet qui nécessite le package `centralized-patcher` à l’aide de la commande `vendor/bin/magento-patches apply`.

À des fins de test, vous pouvez créer un exemple de correctif (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Vous devez placer vos propres correctifs dans le répertoire `m2-hotfixes`, ainsi que les correctifs que vous recevez directement du support Adobe Commerce.

Exemple de fichier de correctif (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`) :

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Comme cet exemple utilise la méthode locale pour installer des correctifs de qualité, vous devez vous assurer que la commande `vendor/bin/magento-patches apply` s’exécute après les opérations `composer install`. Ce plug-in est déclenché après les opérations `composer install`, qui exécutent la commande `vendor/bin/magento-patches apply`.

Pour créer le package de composants `centralized-patcher-compose-plugin` :

1. Créez un fichier `composer.json` avec les contenus suivants :

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Créez un fichier PHP et définissez une classe de `CentralizedPatcher` pour lire la liste des patchs de qualité à partir du package de composant [`centralized-patcher`](#centralized-patcher) et installez-les immédiatement après chaque opération de `composer install`.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Reportez-vous aux [exemples-de-code](#code-examples) pour voir les deux packages décrits dans cet exemple en action.


## Que faire avec les correctifs spécifiques au projet ?

Vous pouvez avoir un scénario dans lequel seulement 95 % des correctifs sont requis dans tous les projets, tandis que quelques correctifs s’appliquent uniquement à une instance spécifique. La méthode habituelle d’application des correctifs fonctionne toujours. Vous pouvez conserver les correctifs spécifiques au projet dans le répertoire `/m2-hotfixes` et installer les correctifs de qualité par projet.

Si vous utilisez cette approche, **ne validez pas** les correctifs du répertoire `/m2-hotfixes` qui ont été copiés dans votre projet par le package de composant `centralized-patcher`. Vous pouvez empêcher les validations accidentelles en ajoutant des `/m2-hotfixes` à votre fichier `.gitignore`. Après la mise à jour du fichier `.gitignore`, n’oubliez pas que tout `/m2-hotfixes` spécifique au projet doit être ajouté à l’aide de la commande `git add –force` .

## Exécution de différentes versions d’Adobe Commerce

Assurez-vous de définir la dépendance appropriée dans le package de composants `centralized-patcher`. Par exemple, vous pouvez avoir besoin d’Adobe Commerce 2.4.5-p2 pour une version spécifique de votre package, qui fournit uniquement des correctifs compatibles avec Adobe Commerce 2.4.5-p2. Vous disposez peut-être d’une autre version de ce package compatible avec Adobe Commerce 2.4.4.

## Comprendre le résultat

Comme avec Adobe Commerce sur les infrastructures cloud, cet article suppose que votre processus de déploiement utilise la commande `composer install` et non `composer update` ou `git pull` pour déployer du nouveau code sur vos serveurs. Le flux d’installation de correctifs centralisés se présente alors comme suit :

1. Installation du compositeur

   - Installe Adobe Commerce, y compris les correctifs de sécurité et fonctionnels -p1 ou -p2.
   - Combine des correctifs de `/m2-hotfixes` et de support centralisés avec des correctifs de `/m2-hotfixes` et de support spécifiques au projet
   - Applique tous les correctifs installés avec le package `cweagans/composer-patches` Composer

1. Après la `composer install`

   - Le plug-in Composer installe des correctifs de qualité centralisés.

1. Déploiement

   - Les correctifs requis et les correctifs de qualité spécifiques au projet sont installés en fonction du fichier `.magento.env.yaml` (Adobe Commerce sur les projets d’infrastructure cloud uniquement).
   - Les correctifs personnalisés et les correctifs de prise en charge du répertoire `/m2-hotfixes` sont installés par ordre alphabétique par nom de correctif.

Vous pouvez ainsi gérer de manière centralisée tous vos correctifs pour toutes vos installations et mieux garantir la sécurité et la stabilité de vos magasins Adobe Commerce. Utilisez les méthodes suivantes pour vérifier le statut du correctif :

- [ Projets d’infrastructure cloud ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Projets sur site](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Exemples de code

- [Correctifs centralisés dans Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Correctifs centralisés dans Adobe Commerce sur les infrastructures cloud](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Module externe du compositeur de correctif centralisé](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Composant de correctif centralisé](https://github.com/AntonEvers/centralized-patcher)
