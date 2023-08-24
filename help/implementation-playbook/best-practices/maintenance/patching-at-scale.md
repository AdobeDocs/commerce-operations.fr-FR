---
title: Bonnes pratiques pour la distribution de correctifs à grande échelle
description: Découvrez comment l’application de correctifs centralisés pour Adobe Commerce peut vous aider à gérer les projets d’entreprise.
role: Developer
feature: Best Practices
badge: label="Contribution d&#39;Anton Evers, ingénieur en architecture technique, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Contribution d’Anton Evers"
source-git-commit: d8ee656b4b1741b39f2eef1f5628a299377e774c
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Bonnes pratiques pour la distribution de correctifs Adobe Commerce à grande échelle

Si vous gérez plusieurs installations Adobe Commerce, [correction](../../../upgrade/patches/apply.md) peut être un processus complexe. _Application de correctifs centralisée_ est une partie essentielle de [architecture de référence globale](../../architecture/global-reference.md) et une bonne pratique pour les entreprises. Il vous aide à appliquer les correctifs appropriés sur toutes vos installations Adobe Commerce. Cette rubrique explique comment obtenir une distribution de correctifs centralisée pour tous les types d’Adobe Commerce. [Correctifs](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Le contenu suivant a été initialement publié dans la [Distribution des correctifs Adobe Commerce à l’échelle](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) Article sur le blog Adobe Tech. Il a été modifié afin de se concentrer sur les étapes et les exemples de code pour mettre en oeuvre une stratégie de correctif centralisé. Pour plus d’informations sur les différents types de correctifs décrits ici, consultez la publication d’origine .

## Produits et versions concernés

[Toutes les versions prises en charge](../../../release/versions.md) de :

- Adobe Commerce sur l’infrastructure cloud
- Adobe Commerce sur site

## Stratégie

Comme il existe de nombreux types de correctifs différents et de nombreuses façons de les appliquer, comment savoir quel correctif est appliqué en premier ? Plus vous avez de correctifs, plus les chances qu’ils s’appliquent au même fichier ou à la même ligne de code sont grandes. Les correctifs sont appliqués dans l’ordre suivant :

1. **Correctifs de sécurité** font partie de la base de code statique d’une version d’Adobe Commerce.
1. **Correctifs du compositeur** through `composer install` et `composer update` modules externes tels que [cweagans/compositeur-correctifs](https://packagist.org/packages/cweagans/composer-patches).
1. Tous **correctifs requis** inclus dans la variable [Correctifs de cloud pour Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) module.
1. Sélectionné **correctifs de qualité** inclus dans la variable [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Correctifs personnalisés** et les correctifs de la prise en charge d’Adobe Commerce dans `/m2-hotfixes` par ordre alphabétique par nom de correctif.

   >[!IMPORTANT]
   >
   >Plus vous appliquez de correctifs, plus votre code devient complexe. Un code complexe peut rendre la mise à niveau vers une nouvelle version du commerce Adobe plus difficile et augmenter le coût total de possession.

Si vous êtes responsable de la maintenance de plusieurs installations d’Adobe Commerce, il peut s’avérer difficile de s’assurer que toutes les instances ont le même ensemble de correctifs installés. Chaque installation possède son propre référentiel git, `/m2-hotfixes` répertoire et `composer.json` fichier . La seule garantie que vous avez est que la variable **correctifs de sécurité** et **correctifs requis** pour les utilisateurs cloud sont tous installés dans le cadre de votre version Adobe Commerce principale.

Actuellement, il n’existe pas de solution centralisée unique pour ce problème, mais le compositeur d’expérience offre un moyen de combler le fossé. La variable [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) Le module vous permet de [appliquer des correctifs à partir des dépendances ;](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Vous pouvez créer un module Compositeur qui installe tous vos correctifs, puis en avoir besoin dans tous vos projets.

Les couvertures **correctifs de sécurité**, **correctifs requis**, et **Correctifs du compositeur**, mais qu’en est-il des correctifs de qualité et du contenu des `/m2-hotfixes` répertoire ?

## Application de correctifs de qualité et de correctifs logiciels

Vous pouvez installer des correctifs de qualité sur l’infrastructure cloud et les installations sur site à l’aide du `vendor/bin/magento-patches apply` . Vous devez vous assurer que la variable `vendor/bin/magento-patches apply` La commande s’exécute après `composer install` opérations.

>[!NOTE]
>
>Sur l’infrastructure cloud, vous pouvez également installer des correctifs de qualité en les répertoriant dans la liste de votre projet. `.magento.env.yaml` fichier . L’exemple présenté ici nécessite d’utiliser la méthode `vendor/bin/magento-patches apply` .

Vous pouvez spécifier les correctifs à appliquer dans le `composer.json` fichier d’un module de composant Compositeur personnalisé, puis créez un module externe qui exécute la commande après `composer install` opérations.

Pour résumer, cet exemple de correctif centralisé nécessite la création de deux packages compositeur personnalisés :

- **Package de composant :** `centralized-patcher`

   - Définit la liste des correctifs de qualité et `m2-hotfixes` pour installer
   - Nécessite le `centralized-patcher-composer-plugin` , qui exécute la variable `vendor/bin/magento-patches apply` command after `composer install` opérations

- **Module externe :** `centralized-patcher-composer-plugin`

   - Définit un `CentralizedPatcher` Classe PHP qui lit la liste des correctifs de qualité à partir de la `centralized-patcher` package
   - Exécute la variable `vendor/bin/magento-patches apply` pour installer la liste des correctifs de qualité après `composer install` opérations

### `centralized-patcher`

Vous pouvez créer un module de composant Compositeur (`centralized-patcher`) pour gérer de manière centralisée tous les correctifs de qualité et `/m2-hotfixes` sur toutes vos installations Adobe Commerce.

Le module de composant doit :

- Copiez le contenu de la `/m2-hotfixes` dans toutes vos installations pendant le déploiement.
- Définissez la liste des correctifs de qualité à installer.
- Exécutez la variable `vendor/bin/magento-patches` pour installer la même liste de correctifs de qualité sur toutes les installations (à l’aide de la commande [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) module externe en tant que dépendance).

Pour créer la variable `centralized-patcher` package de composant :

1. Créez un `composer.json` avec les contenus suivants :

   >[!NOTE]
   >
   >La variable `require` dans l’exemple suivant affiche une `require` dépendante de la variable [module externe](#centralized-patcher-composer-plugin) que vous devez créer plus tard dans cet exemple.

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

1. Créez un `/m2-hotfixes` répertoire dans votre package et ajoutez-le à la variable `map` dans votre `composer.json` fichier . La variable `map` contient les fichiers à copier de ce package dans la racine du projet cible que vous souhaitez corriger.

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
   >La variable `centralized-patcher` copie le contenu de la variable `/m2-hotfixes` répertoire dans le répertoire m2-hotfixes du projet cible sur `composer install`.  Puisque les scripts de déploiement cloud appliquent des correctifs m2 après `composer install`, tous les correctifs sont installés par le mécanisme de déploiement.

1. Définissez les correctifs de qualité à installer dans le `quality-patches` attribut.

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


La variable `quality-patches` dans l’exemple de code précédent contient deux correctifs de la fonction [liste complète de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) par exemple.  Ces correctifs de qualité sont installés sur chaque projet qui nécessite les `centralized-patcher` à l’aide du module `vendor/bin/magento-patches apply` .

À des fins de test, vous pouvez créer un exemple de correctif (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Vous devez placer vos propres correctifs dans la `m2-hotfixes` avec les correctifs que vous recevez directement de l’assistance Adobe Commerce.

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

Puisque cet exemple utilise la méthode sur site pour installer des correctifs de qualité, vous devez vous assurer que la variable `vendor/bin/magento-patches apply` La commande s’exécute après `composer install` opérations. Ce module externe est déclenché après `composer install` qui exécute la variable `vendor/bin/magento-patches apply` .

Pour créer la variable `centralized-patcher-compose-plugin` package de composant :

1. Créez un `composer.json` avec les contenus suivants :

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

1. Créez un fichier PHP et définissez une `CentralizedPatcher` pour lire la liste des correctifs de qualité à partir de la [`centralized-patcher`](#centralized-patcher) module de composant et installez-les immédiatement après chaque `composer install` opération.

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
>Voir [code-examples](#code-examples) pour voir en action les deux packages décrits dans cet exemple.


## Que faire des correctifs spécifiques à un projet

Il peut y avoir un scénario où seulement 95 % des correctifs sont requis dans tous les projets, tandis que quelques correctifs s’appliquent uniquement à une instance spécifique. La méthode régulière d’application de correction fonctionne toujours. Vous pouvez conserver les correctifs spécifiques au projet dans le `/m2-hotfixes` et installez des correctifs de qualité par projet.

Si vous utilisez cette approche, **ne pas** de soumettre tous les correctifs dans la fonction `/m2-hotfixes` répertoire qui a été copié dans votre projet par l’objet `centralized-patcher` module de composant. Vous pouvez empêcher les validations accidentelles en ajoutant `/m2-hotfixes` à votre `.gitignore` fichier . Après la mise à jour de la variable `.gitignore` , n’oubliez pas que tout `/m2-hotfixes` doit être ajouté à l’aide de la variable `git add –force` .

## Exécution de différentes versions d’Adobe Commerce

Assurez-vous de définir la dépendance appropriée dans la variable `centralized-patcher` module de composant. Par exemple, vous pouvez avoir besoin d’Adobe Commerce 2.4.5-p2 pour une version spécifique de votre package, qui ne fournit que les correctifs compatibles avec Adobe Commerce 2.4.5-p2. Vous pouvez avoir une autre version de ce module compatible avec Adobe Commerce 2.4.4.

## Comprendre le résultat

Comme avec Adobe Commerce sur l’infrastructure cloud, cet article suppose que votre processus de déploiement utilise la méthode `composer install` Commande et non `composer update` ou `git pull` pour déployer le nouveau code sur vos serveurs. Le flux d&#39;installation de correctifs centralisés se présente alors comme suit :

1. Installation du compositeur

   - Installe Adobe Commerce, y compris les correctifs de sécurité -p1 ou -p2 et fonctionnels.
   - Combine des éléments centralisés `/m2-hotfixes` et prise en charge des correctifs avec des `/m2-hotfixes` et correctifs de support
   - Applique tous les correctifs installés avec le `cweagans/composer-patches` Module de compositeur

1. Après `composer install`

   - Le module externe du compositeur installe des correctifs de qualité centralisés.

1. Déploiement

   - Les correctifs requis et les correctifs de qualité spécifiques au projet sont installés en fonction de la variable `.magento.env.yaml` (Adobe Commerce sur les projets d’infrastructure cloud uniquement).
   - Correctifs personnalisés et correctifs de prise en charge depuis `/m2-hotfixes` sont installés par ordre alphabétique par nom de correctif.

Ainsi, vous pouvez gérer de manière centralisée tous vos correctifs pour toutes vos installations et vous pouvez mieux garantir la sécurité et la stabilité de vos magasins Adobe Commerce. Utilisez les méthodes suivantes pour vérifier l’état du correctif :

- [Projets d’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Projets sur site](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Exemples de code

- [Correctifs centralisés en Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Correctifs centralisés dans Adobe Commerce sur l’infrastructure cloud](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Module externe du compositeur de patcher centralisé](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Composant du dispatcher centralisé](https://github.com/AntonEvers/centralized-patcher)
