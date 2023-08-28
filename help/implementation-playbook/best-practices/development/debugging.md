---
title: Bonnes pratiques relatives au débogage
description: Découvrez des techniques pour résoudre les problèmes de développement courants d’Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---


# Bonnes pratiques relatives au débogage pour Adobe Commerce

Cette rubrique explique comment déboguer de manière systématique et efficace la structure Adobe Commerce. L’objectif est de vous aider à atteindre rapidement la racine d’un problème et de réduire le temps d’enquête.

## Dépannage : suspects usuels

Cette section décrit les problèmes les plus courants que vous pouvez rencontrer lors du développement.

### Cache

- Videz le cache avant d’approfondir l’enquête
- Tenez compte du cache d’APC, du réseau de diffusion de contenu, du vernis, du code généré et de la variable `var/view_preprocessed` et `pub/static/` répertoires
- Arrêtez et redémarrez les gestionnaires de file d’attente après avoir vidé le cache ou modifié le code.

L’exemple de code suivant fournit des commandes utiles relatives à la gestion du cache (ne pas exécuter sur les environnements de production) :

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

Réindexez tout si le problème peut être lié à l’index. Le débogage des données indexées se produit généralement dans des environnements hors production. Dans les environnements de production, vous pouvez examiner l’origine du décalage d’index avant de réindexer. Les caractéristiques de l&#39;état défectueux peuvent vous donner une idée de l&#39;origine du problème.

### Compositeur

Le code peut être obsolète en raison d’un changement de branche ou des fichiers principaux qui ont été modifiés lors d’un précédent débogage. Pour éliminer les problèmes potentiels, exécutez les commandes suivantes :

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Contenu généré

Recréez les fichiers frontend avant de déboguer le contenu généré dans JS, CSS, images, traductions et autres fichiers.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Mode Développeur

Vérifiez que votre installation locale se trouve dans `developer` mode .

### Nouveau module

Si vous avez créé un module, recherchez les problèmes suivants :

- Le module est-il activé ?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Vérifiez les `app/etc/config.php` pour votre nouveau module.

- Vérifiez l’imbrication du fichier et de la structure de répertoires. Par exemple, les fichiers de mise en page se trouvent dans la variable `view/layout/` au lieu du répertoire `view/frontend/layout` répertoire ? Sont des modèles dans la variable `view/frontend/template` au lieu du répertoire `view/frontend/templates` répertoire ?

## Dépannage : Partage à moitié

Si les suspects habituels ne proposent pas de solution au problème, la façon la plus rapide de procéder est de diviser à moitié (ou de diviser) le problème. Avec cette méthode, vous éliminez les blocs volumineux et divisez ce qui reste pour localiser la cause principale au lieu de parcourir le code de manière linéaire.

Voir les diagrammes suivants :

![Diagramme de bord](../../../assets/playbooks/bisect.png)

![Diagramme de bord](../../../assets/playbooks/bisect2.png)

Il existe plusieurs approches de la segmentation, mais Adobe recommande de suivre cet ordre :

- Biscuit par rubrique
- Bisculez par validations
- Biscuit par fichier

### Etape 1 : biaiser par sujet

Si le problème peut ne pas être lié au code, supprimez d’abord les gros blocs. Voici quelques-uns des grands blocs à envisager :

- **Structure Adobe Commerce**— Le problème est-il lié à Adobe Commerce ou pourrait-il être lié à un autre système connecté ?
- **Serveur et client**: effacez le cache et le stockage du navigateur. Le problème est-il résolu ? Cela peut exclure une cause liée au serveur. Le problème existe-t-il encore ? Il n’est plus nécessaire de perdre du temps dans le débogage du navigateur.
- **Session**: le problème se produit-il pour chaque utilisateur ? Si ce n’est pas le cas, votre problème peut se limiter aux rubriques liées à la session ou au navigateur.
- **Cache**—La désactivation de tous les caches change-t-elle quoi que ce soit ? Si tel est le cas, vous pouvez vous concentrer sur les rubriques liées au cache.
- **Base**: le problème se produit-il sur chaque environnement exécutant le même code ? Si ce n’est pas le cas, recherchez les problèmes de configuration et d’autres sujets liés à la base de données.
- **Code**: recherchez des problèmes de code si aucun des problèmes ci-dessus n’a résolu le problème.

### Étape 2 : biaiser par validations

Si le problème a commencé entre maintenant et il y a deux mois, ramenez le code à il y a deux mois. Vérifiez si le problème existe toujours. Avance d&#39;un mois. Le problème se produit-il là ? Si ce n&#39;est pas le cas, passez deux semaines. Cela se produit-il maintenant ? Reviens une semaine en arrière. Toujours là ? Retournez quatre jours en arrière. À un moment donné, il ne vous reste qu’une seule validation susceptible de contenir du code lié au problème. Votre cause principale est désormais probablement limitée aux fichiers modifiés dans cette validation.

Vous pouvez remplacer les semaines et les jours par des validations. Par exemple, basculez 100 validations, 50, 25, 12.

### Étape 3 : sélection par fichiers

- Divisez Adobe Commerce par types de fichiers (core et non-core). Tout d’abord, désactivez tous les modules client et marketplace. Le problème existe-t-il encore ? Il s&#39;agit probablement d&#39;une question non fondamentale.
- Activez (environ) à nouveau la moitié des modules dans la fonction `app/etc/config.php` fichier . Tenez compte des dépendances. Il est préférable d’activer simultanément des grappes de modules avec le même sujet. Le problème existe-t-il encore ?
- Activez un quart des modules restants. Le problème existe-t-il encore ? Désactivez la moitié de ce que vous avez activé. Cette méthode peut vous aider à isoler la cause racine d’un seul module.

## Économies de temps

Outre les techniques de dépannage, cette section fournit des règles générales qui peuvent vous aider à gagner du temps lors du débogage.

### Limiter les données

Déterminez si vous avez besoin du catalogue complet ou de toutes les vues de magasin pour répliquer le problème. Vous pouvez déboguer des problèmes d’indexation avec un clone de base de données où vous avez supprimé 95 % du catalogue avant de commencer le débogage. Cette méthode permet de gagner un temps considérable lors des processus d’indexation. Créez un doublon de la base de données client avec un nombre et un catalogue réduits. Cela peut également s’appliquer à d’autres entités (telles que les clients) en fonction de la zone que vous déboguez.

### Demander plus d’informations

Parfois, une étape facile à oublier au milieu de tout le code et le travail technique : demander plus d&#39;informations. Captures plein écran, vidéo, conversation vidéo avec la personne qui a identifié le problème, étapes de réplication, questions sur le fait que d&#39;autres choses apparemment sans importance se soient produites autour de l&#39;événement problématique. Demandez ce que quelqu&#39;un s&#39;attendait à ce qu&#39;il se produise. S’agit-il vraiment d’un bogue ou peut-être simplement d’un malentendu sur le fonctionnement du code ?

### Langue et interprétation

La description du problème est-elle claire ? Êtes-vous certain qu’aucun terme ou description ne peut être interprété de plusieurs façons. Si c&#39;est le cas, assurez-vous de parler de la même chose.

### Recherche Internet

Effectuez une recherche Internet avec des termes liés au problème. Il est probable que quelqu&#39;un d&#39;autre ait déjà rencontré le même problème. Effectuez une recherche dans le [Problèmes liés à Adobe Commerce GitHub](https://github.com/magento/magento2/issues).

### Faites une pause

Si vous cherchez un problème pendant trop longtemps, il peut être difficile de trouver une solution. Posez votre travail et prenez une autre tâche ou faites une promenade. La réponse peut vous venir à l&#39;esprit lorsque vous oubliez le problème pendant un moment.

## Outils

Outils d’interface de ligne de commande n98 Magerun ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) fournissent des fonctionnalités utiles pour travailler avec Adobe Commerce à partir de la ligne de commande. En particulier, ces commandes :

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Fragments de code

Les rubriques suivantes contiennent des fragments de code qui peuvent être utilisés pour consigner ou identifier des problèmes dans les projets Commerce.

### Vérifier si un fichier XML est utilisé par Commerce

Ajoutez une erreur de syntaxe évidente dans un fichier XML pour vérifier s’il est utilisé. Ouvrez une balise et ne la fermez pas, par exemple :

```xml
<?xml version="1.0"?>
<test
```

Si ce fichier est utilisé, une erreur est générée. Si ce n’est pas le cas, votre module peut ne pas être utilisé ou activé par exemple, ou le fichier XML peut se trouver au mauvais emplacement.

### Journalisation

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monolog]

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
