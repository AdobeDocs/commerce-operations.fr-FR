---
title: Utiliser memcached pour le stockage de session
description: Découvrez comment utiliser memcached pour le stockage des sessions Commerce.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Utiliser memcached pour le stockage de session

Memcached est un système de mise en cache de mémoire distribuée à usage général. Elle est souvent utilisée pour accélérer les sites web dynamiques pilotés par une base de données en mettant en cache des données et des objets dans la RAM afin de réduire le nombre de fois qu’une source de données externe (telle qu’une base de données ou une API) doit être lue.

Memcached fournit une table de hachage volumineuse qui peut être distribuée sur plusieurs ordinateurs. Lorsque le tableau est plein, les insertions suivantes entraînent la purge des données plus anciennes dans l&#39;ordre d&#39;utilisation le moins récent (LRU). La taille de cette table de hachage est souvent très grande. (Source : [memcached.org](https://www.memcached.org/))

Commerce utilise la mise en cache de mémoire pour le stockage de session, mais pas pour la mise en cache de page. Pour la mise en cache de page, nous vous recommandons d’utiliser [Redis](../cache/redis-pg-cache.md) ou [Varnish](../cache/config-varnish.md).

**Pour configurer Commerce afin d’utiliser memcached** :

1. Ouvrez `<your install dir>/app/etc/env.php` dans un éditeur de texte.
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

   memcached comporte des paramètres de démarrage facultatifs qui ne font pas partie de ce guide. Vous trouverez plus d’informations à leur sujet dans la documentation [memcached](https://www.php.net/manual/en/memcached.sessions.php), le code source et les journaux de modifications.

1. Passez à la section suivante.

**Pour vérifier que memcached fonctionne avec Commerce** :

1. Supprimez le contenu des répertoires ci-dessous de votre répertoire d’installation Commerce :

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Accédez à n’importe quelle page du storefront.

1. Connectez-vous à l’Administration et accédez à plusieurs pages.

   Si aucune erreur ne s’affiche, félicitations ! memcached fonctionne ! Vous pouvez éventuellement examiner le stockage mis en cache, comme indiqué à l’étape suivante.

   Si des erreurs s’affichent (par exemple, une erreur HTTP 500 (Internal Server Error)), activez le mode Développeur et diagnostiquez le problème. Assurez-vous que memcached est en cours d&#39;exécution, correctement configuré et qu&#39;`env.php` n&#39;a aucune erreur de syntaxe.

1. (Facultatif.) Utilisez Telnet pour examiner le stockage en mémoire cache.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Les résultats s’affichent de la manière suivante :

   ```
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
