---
title: Utiliser la mémoire mise en cache pour le stockage de session
description: Découvrez comment utiliser la mémoire mise en cache pour le stockage de session dans Commerce.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Utiliser la mémoire mise en cache pour le stockage de session

Memcached est un système de mise en cache de mémoire distribuée d’usage général. Il est souvent utilisé pour accélérer les sites web dynamiques pilotés par la base de données en mettant en cache des données et des objets dans la mémoire RAM afin de réduire le nombre de fois où une source de données externe (telle qu’une base de données ou une API) doit être lue.

Memcached fournit une grande table de hachage qui peut être distribuée sur plusieurs machines. Lorsque le tableau est plein, les insertions suivantes provoquent la purge des données plus anciennes dans l’ordre des données les moins récemment utilisées (LRU). La taille de cette table de hachage est souvent très grande. (Source : [memcached.org](https://www.memcached.org/))

Commerce utilise la mémoire mise en cache pour le stockage de session, mais pas pour la mise en cache de page. Pour la mise en cache des pages, nous vous recommandons de [Redis](../cache/redis-pg-cache.md) ou [Varnish](../cache/config-varnish.md).

**Pour configurer Commerce de manière à utiliser la mémoire mise en cache**:

1. Ouvrir `<your install dir>/app/etc/env.php` dans un éditeur de texte.
1. Recherchez les éléments suivants :

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Modifiez-le comme suit :

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memmis en cache comporte des paramètres de démarrage facultatifs qui vont au-delà de la portée de ce guide. Vous trouverez plus d’informations à leur sujet dans la section [memcached](https://www.php.net/manual/en/memcached.sessions.php) documentation, code source et journaux de modification.

1. Passez à la section suivante.

**Pour vérifier que la mémoire mise en cache fonctionne avec Commerce**:

1. Supprimez le contenu des répertoires suivants sous votre répertoire d’installation Commerce :

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Accédez à n’importe quelle page du storefront.

1. Connectez-vous à l’administrateur et accédez à plusieurs pages.

   Si aucune erreur ne s&#39;affiche, félicitations ! memcached fonctionne ! Vous pouvez éventuellement examiner le stockage en mémoire cache comme décrit à l’étape suivante.

   Si des erreurs s’affichent (par exemple, un HTTP 500 (Erreur interne du serveur)), activez le mode Développeur et diagnostiquez le problème. Assurez-vous que la mémoire mise en cache est en cours d’exécution, configurée correctement et que `env.php` ne contient aucune erreur de syntaxe.

1. (Facultatif.) Utilisez Telnet pour examiner le stockage en mémoire cache.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Les résultats s’affichent comme suit :

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
