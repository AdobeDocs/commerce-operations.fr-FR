---
title: Bonnes pratiques de débogage
description: Découvrez les techniques permettant de résoudre les problèmes de développement courants d’Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Bonnes pratiques de débogage pour Adobe Commerce

Cette rubrique explique comment déboguer systématiquement et efficacement le framework Adobe Commerce. L’objectif est de vous aider à vous attaquer rapidement à la racine d’un problème et de réduire le temps nécessaire aux enquêtes.

## Dépannage : les suspects habituels

Cette section décrit les problèmes les plus courants que vous pouvez rencontrer pendant le développement.

### Cache

- Videz le cache avant d’approfondir l’enquête
- Tenez compte du cache APC, du réseau CDN, du vernis, du code généré et des répertoires `var/view_preprocessed` et `pub/static/`
- Arrêtez et redémarrez les gestionnaires de file d’attente après avoir vidé le cache ou modifié le code

L’exemple de code suivant fournit des commandes utiles liées à la gestion du cache (ne pas exécuter dans les environnements de production) :

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### Données indexées

Réindexez tout si le problème peut être lié à l’index. Le débogage des données indexées se produit généralement dans les environnements hors production. Dans les environnements de production, vous pouvez rechercher l’origine de l’alignement incorrect des index avant de les réindexer. Les caractéristiques de l&#39;état défectueux peuvent vous en dire quelque chose sur l&#39;origine du problème.

### Compositeur

Il se peut que votre code soit obsolète en raison d’une modification de branche ou de fichiers principaux modifiés lors d’un effort de débogage précédent. Pour éliminer les problèmes potentiels, exécutez les commandes suivantes :

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Contenu généré

Recréez les fichiers frontend avant de déboguer le contenu généré dans les fichiers JS, CSS, images, traductions et autres.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Mode Développeur

Assurez-vous que votre installation locale est en mode `developer`.

### Nouveau module

Si vous avez créé un module, vérifiez les problèmes suivants :

- Le module est-il activé ?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Vérifiez le fichier `app/etc/config.php` pour votre nouveau module.

- Vérifiez l’imbrication des fichiers et de la structure des répertoires. Par exemple, les fichiers de disposition se trouvent-ils dans le répertoire `view/layout/` et non dans le répertoire `view/frontend/layout` ? Les modèles se trouvent-ils dans le répertoire `view/frontend/template` plutôt que dans le répertoire `view/frontend/templates` ?

## Dépannage : division en deux

Si les suspects habituels n’offrent pas de solution au problème, la façon la plus rapide de procéder est de diviser le problème en deux (ou en deux). Avec cette méthode, vous éliminez des blocs volumineux et divisez ce qui reste pour localiser la cause principale au lieu de parcourir le code de manière linéaire.

Voir les diagrammes suivants :

![Diagramme Bisect](../../../assets/playbooks/bisect.png)

![Diagramme Bisect](../../../assets/playbooks/bisect2.png)

Il existe plusieurs approches pour bissecter, mais Adobe recommande de suivre cet ordre :

- Diviser par sujet
- Diviser par validations
- Tri par fichiers

### Étape 1 : Bisecter par sujet

Si le problème n’est pas lié au code, éliminez d’abord les blocs volumineux. Voici quelques-uns des éléments importants à prendre en compte :

- **Framework Adobe Commerce**—Le problème est-il lié à Adobe Commerce ou pourrait-il être lié à un autre système connecté ?
- **Serveur et client** : videz le cache et le stockage du navigateur. Le problème est-il résolu ? Cela peut exclure une cause liée au serveur. Le problème existe-t-il toujours ? Plus besoin de perdre de temps dans le débogage du navigateur.
- **Session** : le problème se produit-il pour chaque utilisateur ? Si ce n’est pas le cas, votre problème peut se limiter à des rubriques liées à la session ou au navigateur.
- **Cache** : la désactivation de tous les caches change-t-elle quelque chose ? Si tel est le cas, vous pouvez vous concentrer sur les rubriques relatives au cache.
- **Base de données** : le problème se produit-il dans chaque environnement exécutant le même code ? Dans le cas contraire, recherchez les problèmes de configuration et d&#39;autres rubriques relatives à la base de données.
- **Code** : recherchez les problèmes de code si aucun des éléments ci-dessus ne résout le problème.

### Étape 2 : division par validations

Si le problème a commencé entre maintenant et il y a deux mois, restaurez le code à deux mois auparavant. Vérifiez si le problème existe toujours. Avance d&#39;un mois. Le problème se produit-il là-bas? Sinon, allez-y pendant deux semaines. Cela se produit-il maintenant ? Retourne une semaine en arrière. Toujours là ? Remontez quatre jours en arrière. À un moment donné, il ne vous reste qu’une seule validation, qui contient probablement du code lié au problème. Votre cause première est désormais probablement limitée aux fichiers modifiés dans cette validation.

Vous pouvez remplacer semaines et jours par des validations. Par exemple, annuler 100 validations, avancer 50, avancer 25, reculer 12.

### Étape 3 : Diviser par fichiers

- Divisez Adobe Commerce par types de fichiers (principaux et non principaux). Tout d’abord, désactivez tous les modules de marché et de client. Le problème existe-t-il toujours ? Il s’agit probablement d’une question secondaire.
- Activez à nouveau (en gros) la moitié des modules dans le fichier `app/etc/config.php`. Tenez compte des dépendances. Il est préférable d’activer les clusters de modules avec le même sujet en même temps. Le problème existe-t-il toujours ?
- Activez un quart des modules restants. Le problème existe-t-il toujours ? Désactivez la moitié de ce que vous avez activé. Cette méthode peut vous aider à isoler la cause première à un seul module.

## Gains de temps

Outre les techniques de dépannage, cette section fournit quelques règles générales qui peuvent vous aider à gagner du temps lors du débogage.

### Limiter les données

Déterminez si vous avez besoin du catalogue complet ou de toutes les vues de magasin pour répliquer le problème. Vous pouvez déboguer les problèmes d’indexation avec un clone de base de données dans lequel vous avez supprimé 95 % du catalogue avant de commencer le débogage. Cette méthode permet de gagner beaucoup de temps pendant les processus d’indexation. Créez un doublon de la base de données cliente avec un nombre de magasins et un catalogue réduits. Cela peut également s’appliquer à d’autres entités (comme les clients) en fonction de la zone que vous déboguez.

### Demander plus d&#39;informations

Parfois, une étape facile à oublier parmi tout le code et le travail technique : demandez plus d&#39;informations. Captures en plein écran, vidéo, conversation par vidéoconférence avec la personne qui a identifié le problème, étapes de réplication, questions pour savoir si d’autres événements apparemment sans importance se sont produits autour de l’événement problématique. Demandez-lui ce que quelqu&#39;un s&#39;attendait à voir se produire. S’agit-il vraiment d’un bug ou peut-être simplement d’une mauvaise compréhension du fonctionnement du code ?

### Langue et interprétation

La description du problème est-elle claire ? Êtes-vous certain qu’aucun terme ou description ne peut être interprété de plusieurs façons. Si oui, assurez-vous de parler de la même chose.

### Recherche sur Internet

Effectuez une recherche sur Internet avec les termes liés au problème. Il est probable que quelqu’un d’autre ait déjà rencontré le même problème. Recherchez parmi les [problèmes GitHub d’Adobe Commerce](https://github.com/magento/magento2/issues).

### Faites une pause

Si vous cherchez un problème depuis trop longtemps, il peut être difficile de trouver une solution. Déposez votre travail et prenez une autre tâche ou faites une promenade. La réponse peut vous venir lorsque vous oubliez la question pendant un certain temps.

## Outils

Les outils de l’interface de ligne de commande n98 magerun ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) offrent des fonctionnalités utiles pour travailler avec Adobe Commerce à partir de la ligne de commande. En particulier, ces commandes :

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Fragments de code

Les rubriques suivantes fournissent des fragments de code qui peuvent être utilisés pour consigner ou identifier des problèmes dans les projets Commerce.

### Vérifier si un fichier XML est utilisé par Commerce

Ajoutez une erreur de syntaxe évidente dans un fichier XML pour voir si elle est utilisée. Ouvrez une balise sans la fermer par exemple :

```xml
<?xml version="1.0"?>
<test
```

Si ce fichier est utilisé, il génère une erreur. Si ce n&#39;est pas le cas, il se peut que votre module ne soit pas utilisé ou activé, par exemple, ou que le fichier XML se trouve au mauvais emplacement.

### Journalisation

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monologue]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### Journalisation de bas niveau

Deux exemples qui fonctionnent toujours dans n&#39;importe quel fichier PHP :

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

Et pour une trace de pile :

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
