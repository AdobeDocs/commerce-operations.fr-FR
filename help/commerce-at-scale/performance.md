---
title: Optimisation des performances AEM
description: Optimisez votre configuration Adobe Experience Manager par défaut pour prendre en charge les charges importantes sur Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Optimisation des performances AEM

Le Dispatcher AEM est un proxy inverse qui permet de fournir un environnement à la fois rapide et dynamique. Il fait partie d’un serveur HTML statique, tel que Apache HTTP Server, dans le but de stocker (ou de &quot;mettre en cache&quot;) la plus grande partie du contenu du site sous la forme de ressources statiques. Cette approche vise à minimiser la nécessité d’accéder autant que possible à la fonctionnalité de rendu de page d’AEM et au service GraphQL Adobe Commerce. Le fait de traiter la plupart des pages en tant que code HTML statique, CSS et JS offre des avantages en termes de performances aux utilisateurs et réduit les exigences d’infrastructure dans l’environnement. Toute page ou requête susceptible d’être répétée de manière identique d’un utilisateur à l’autre doit être prise en compte pour la mise en cache.

Les sections suivantes présentent à un haut niveau la zone d’intérêt technique recommandée à examiner pour permettre une mise en cache efficace sur AEM dans un environnement CIF/Adobe Commerce.

## Mise en cache basée sur TTL sur AEM dispatchers

La mise en cache d’un maximum de sites sur les dispatchers est une bonne pratique pour tout projet AEM. L’utilisation de l’invalidation du cache basée sur le temps mettra en cache les pages CIF rendues côté serveur, pendant une durée limitée. Une fois l’heure définie expirée, la requête suivante recrée la page à partir de l’éditeur AEM et de Adobe Commerce GraphQL et la stocke à nouveau dans le cache du Dispatcher jusqu’à l’invalidation suivante.

La fonction de mise en cache TTL peut être configurée AEM avec le composant &quot;Dispatcher TTL&quot; dans le package ACS AEM Commons et la définition de /enableTTL &quot;1&quot; dans le fichier de configuration dispatcher.any.

S’il est activé, le Dispatcher évalue les en-têtes de réponse du serveur principal et, s’ils contiennent un âge maximal de contrôle du cache ou une date d’expiration, un fichier vide auxiliaire en regard du fichier de cache est créé, avec l’heure de modification égale à la date d’expiration. Lorsque le fichier mis en cache est demandé après l’heure de modification, il est automatiquement redemandé depuis le serveur principal. Cela offre un mécanisme de mise en cache efficace qui ne nécessite aucune intervention ou maintenance manuelle, une fois que le délai de mise à jour du produit (TTL) a été reconnu et accepté par les parties prenantes de l’entreprise.

## Mise en cache du navigateur

L’approche TTL du dispatcher ci-dessus réduira considérablement les requêtes et le chargement sur l’éditeur. Toutefois, certaines ressources sont très improbables à modifier. Par conséquent, même les requêtes envoyées au dispatcher peuvent être réduites en mettant en cache les fichiers pertinents localement sur le navigateur d’un utilisateur. Par exemple, le logo du site, qui s’affiche sur chaque page du site dans le modèle de site, n’a pas besoin d’être demandé à chaque fois au Dispatcher. Cela peut être stocké dans le cache du navigateur de l’utilisateur. La réduction des exigences de bande passante pour chaque chargement de page aurait un impact important sur la réactivité du site et les temps de chargement des pages.

La mise en cache au niveau du navigateur est généralement effectuée via le &quot;Cache-Control: max-age=&quot; en-tête de réponse. Le paramètre maxage indique au navigateur combien de secondes il doit mettre en cache le fichier avant de tenter de le &quot;revalider&quot; ou de le demander de nouveau sur le site. Ce concept d’âge maximal du cache est généralement appelé &quot;expiration du cache&quot; ou TTL (&quot;durée de vie&quot;). Diffusion d’expériences commerciales à grande échelle - Avec Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Voici quelques zones d’un site AEM/CIF/Adobe Commerce pouvant être définies pour être mises en cache dans le navigateur du client :

- Images (dans le modèle d’AEM lui-même, par exemple le logo du site et les images de conception de modèle - les images de produit de catalogue sont appelées à partir d’Adobe Commerce via Fastly, et la mise en cache de ces images est discutée ultérieurement)
- Fichiers HTML (pour les pages rarement modifiées - page de conditions générales, etc.)
- Fichiers CSS
- Tous les fichiers JavaScript du site, y compris les fichiers JavaScript CIF

## Optimisation de la période de grâce et du niveau de statut du Dispatcher

La configuration Dispatcher par défaut utilise le paramètre /statfilelevel &quot;0&quot;, ce qui signifie qu’un seul fichier &quot;.stat&quot; est placé à la racine du répertoire htdocs (répertoire racine du document). Si une modification est apportée à une page ou à un fichier dans AEM, l’heure de modification de ce fichier stat unique est mise à jour au moment de la modification. Si le temps est plus récent que l’heure de modification de la ressource, le Dispatcher considère que toutes les ressources sont invalidées et toute requête ultérieure pour une ressource invalidée déclenche un appel à l’instance de publication. Donc essentiellement, avec ce paramètre, chaque activation invalidera l’ensemble du cache.

Pour tous les sites, en particulier les sites de commerce avec une charge importante, cela placerait une charge inutile sur le niveau Publication AEM pour que la structure entière du site soit invalidée avec une seule mise à jour de page.

Au lieu de cela, le paramètre statfilelevel peut être modifié à une valeur supérieure, correspondant à la profondeur des sous-répertoires du répertoire htdocs à partir du répertoire racine du document, de sorte que lorsqu’un fichier situé à un certain niveau est invalidé, seuls les fichiers au niveau du répertoire .stat et au-dessous sont mis à jour.

Par exemple : supposons que vous ayez un modèle de page de produit à l’adresse :

```
content/ecommerce/us/en/products/product-page.html
```

Chaque niveau de dossier aurait un &quot;niveau de départ&quot;, comme illustré dans le tableau ci-dessus.

| content (docroot) | commerce électronique | us | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

Dans ce cas, si vous avez laissé la propriété statfilelevel définie sur &quot;0&quot; par défaut et que le modèle product-page.html est mis à jour et activé déclenchant une invalidation, tous les fichiers .stat de docroot jusqu’au niveau 4 seront touchés et les fichiers invalidés, ce qui provoquera une requête supplémentaire de la part des instances de publication AEM pour toutes les pages du site (y compris d’autres sites web, pays et langues) à partir de cette seule modification.

Cependant, si la propriété statfilelevel est définie sur le niveau 4 et qu’une modification est apportée à product-page.html , seul le fichier .stat du répertoire de produits pour ce site web/pays/langue spécifique est modifié.

Veuillez noter que le niveau du fichier .stat ne doit pas être défini sur un niveau trop élevé ; plus de 20 peut avoir un impact sur les performances. L’exécution d’une activation de fichier en masse lors de l’exécution d’un test de performance doit vous donner le niveau de statistiques correct.

Un autre paramètre du Dispatcher à optimiser lors de la configuration du niveau de fichier stat est le paramètre gracePeriod. Cela définit le nombre de secondes pendant lesquelles une ressource obsolète, invalidée automatiquement, peut toujours être diffusée à partir du cache après la dernière activation. Les ressources invalidées automatiquement sont invalidées par toute activation (lorsque leur chemin correspond à la section dispatcher /invalidate et au niveau spécifié dans la propriété statfileslevel). La définition du paramètre gracePeriod sur 2 secondes peut être utilisée pour empêcher un scénario où plusieurs requêtes sont continuellement envoyées à l’éditeur, même si l’éditeur est encore en train de créer la page.

>[!NOTE]
>
> Une lecture plus détaillée de cette rubrique est disponible dans le référentiel [aem-dispatcher-expériences](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub.

## CIF - Mise en cache GraphQL via des composants

Les composants individuels d’AEM peuvent être définis pour être mis en cache, ce qui signifie que la demande GraphQL peut être Adobe.
Commerce est appelé une fois, puis les demandes suivantes, jusqu’à la limite de temps configurée, sont récupérées du cache AEM et ne placent pas d’autre chargement sur Adobe Commerce. Il peut s’agir, par exemple, d’une navigation sur le site basée sur une arborescence de catégories affichée sur chaque page et sur les options d’une fonctionnalité de recherche à facettes. Il s’agit de deux zones qui nécessitent la création de requêtes gourmandes en ressources sur Adobe Commerce. Il est donc peu probable qu’elles changent régulièrement et constituent de bons choix pour la mise en cache. Ainsi, par exemple, même lorsqu’un PDP ou un PLP est en cours de reconstruction par l’éditeur, la requête GraphQL gourmande en ressources pour la version de navigation n’atteint pas Adobe Commerce et peut être récupérée à partir du cache GraphQL sur AEM CIF.

Un exemple ci-dessous indique que le composant de navigation doit être mis en cache, car il envoie la même requête GraphQL sur toutes les pages du site. La requête ci-dessous met en cache les 100 dernières entrées pendant 10 minutes pour la structure de navigation :

```
venia/components/structure/navigation:true:100:600
```

L’exemple ci-dessous met en cache les 100 dernières options de recherche facettée dans une page de recherche pendant 1 heure :

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

La requête, y compris tous les en-têtes et variables HTTP personnalisés, doit correspondre exactement pour que le cache soit &quot;accès&quot; et pour empêcher un appel de répétition vers Adobe Commerce. Une fois défini, il doit être noté qu’il n’existe aucun moyen facile d’invalider manuellement ce cache. Cela peut donc signifier que si une nouvelle catégorie est ajoutée dans Adobe Commerce, elle ne commencera pas à apparaître dans la navigation tant que le délai d’expiration défini dans le cache ci-dessus n’aura pas expiré et que la requête GraphQL n’aura pas été actualisée. Idem pour les facettes de recherche. Toutefois, étant donné les avantages de performances que cette mise en cache offre, il s’agit généralement d’un compromis acceptable.

Les options de mise en cache ci-dessus peuvent être définies à l’aide de la console de configuration OSGi d’AEM dans &quot;Client GraphQL&quot;.
Usine de configuration&quot;. Chaque entrée de configuration du cache peut être spécifiée au format suivant :

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Mise en cache hybride : demandes GraphQL côté client dans les pages Dispatcher mises en cache

Il est également possible d’utiliser une approche hybride de la mise en cache des pages : il est possible qu’une page CIF contienne des composants qui demanderaient toujours les dernières informations à Adobe Commerce directement depuis le navigateur du client. Cela peut s’avérer utile pour des zones spécifiques de la page dans un modèle qui sont importantes pour être à jour avec des informations en temps réel : Prix des produits au sein d’un PDP, par exemple. Lorsque les prix changent fréquemment en raison de la correspondance dynamique des prix, ces informations peuvent être configurées pour ne pas être mises en cache sur le Dispatcher. Au contraire, les prix peuvent être récupérés côté client dans le navigateur du client à partir d’Adobe Commerce directement via les API GraphQL avec des composants web CIF AEM.

Cela peut être configuré via les paramètres des composants d’AEM : pour les informations de prix sur les pages de liste de produits, il peut être configuré dans le modèle de liste de produits, en sélectionnant le composant de liste de produits dans les paramètres de la page et en cochant l’option &quot;Charger les prix&quot;. La même approche pourrait fonctionner pour le niveau des stocks.

Les méthodes ci-dessus ne doivent être utilisées que dans le cas où des informations en temps réel et constamment à jour sont nécessaires. Dans l’exemple ci-dessus avec la tarification, il peut être convenu avec les parties prenantes de mettre à jour les prix uniquement tous les jours à des heures de faible trafic et d’effectuer ensuite le vidage du cache. Cela éviterait d’avoir besoin de requêtes d’informations de tarification en temps réel et de la charge supplémentaire qui s’ensuivrait sur Adobe Commerce lors de la création de chaque page affichant des informations de tarification.

## Requêtes GraphQL pouvant être mises en cache

Les composants de données dynamiques spécifiques dans les pages ne doivent pas être mis en cache et nécessiteront toujours un appel GraphQL à Adobe Commerce, comme pour le panier d’achat et les appels sur les pages de passage en caisse. Ces informations sont spécifiques à un utilisateur et changent constamment en raison de l’activité du client sur le site, par exemple en ajoutant des produits à son panier.

Les résultats de la requête GraphQL ne doivent pas être mis en cache pour les clients connectés si la conception du site donnerait des réponses différentes en fonction du rôle de l’utilisateur. Par exemple, vous pouvez créer plusieurs groupes de clients et configurer différents prix de produit ou une visibilité de catégorie de produit différente pour chaque groupe. Des résultats de mise en cache de ce type peuvent amener les clients à voir les prix d’un autre groupe de clients ou à afficher des catégories incorrectes.

## Ignorer les paramètres de suivi sur AEM cache du Dispatcher

Les sites d’e-commerce peuvent diriger le trafic vers leur site à l’aide de publicités PPC ou de campagnes sur les médias sociaux.

L’utilisation de ces supports signifie qu’un ID de suivi est ajouté sur le lien sortant de cette plateforme. Par exemple, Facebook ajoute un identifiant de clic Facebook (fbclid) à l’URL, Google Ad ajoute un identifiant de clic Google (gclid), ce qui fait apparaître les liens entrants vers votre interface AEM comme ci-dessous, comme dans l’exemple suivant :

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

Le gclid et fbclid changeront avec chaque utilisateur qui clique sur la publicité, ceci est destiné à des fins de suivi. Toutefois, avec ses paramètres par défaut, AEM considère chaque demande comme une page unique, ce qui contourne le Dispatcher et génère une charge supplémentaire inutile sur l’éditeur et Adobe Commerce.

Lors d’un événement de montée en puissance, cela peut même entraîner une surcharge des éditeurs AEM et une perte de réactivité. Lorsqu’un paramètre est défini pour être ignoré pour une page, la page est mise en cache la première fois que la page est demandée. Les requêtes suivantes pour la page sont diffusées à la page mise en cache, quelle que soit la valeur du paramètre dans la requête.

>[!NOTE]
>
>Vous trouverez plus d’informations sur l’importance de la définition de `ignoreUrlParams` dans le référentiel [aem-dispatcher-expériences](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub.

Il doit donc être configuré pour ignorer tous les paramètres par défaut dans &quot;ignoreUrlParams&quot;, sauf lorsqu’un paramètre GET est utilisé pour modifier la structure HTML d’une page. Par exemple, une page de recherche dans laquelle le terme de recherche figure dans l’URL en tant que paramètre de GET serait utilisée. Dans ce cas, vous devez ensuite configurer manuellement ignoreUrlParams pour ignorer les paramètres tels que gclid, fbclid et tout autre paramètre de suivi utilisé par vos canaux publicitaires, sans affecter les paramètres de GET requis pour les opérations normales du site.

## Limites des travailleurs MPM sur les dispatchers

Les paramètres de traitement MPM sont une configuration de serveur Apache HTTP avancée qui nécessite des tests approfondis pour optimiser en fonction du processeur et de la mémoire vive de votre Dispatcher. Cependant, dans le cadre de ce livre blanc, nous suggérons que ServerLimit et MaxRequestWorkers, soient augmentés à un niveau que le processeur et la RAM disponibles du serveur prennent en charge, puis que les MinSpareThreads et MaxSpareThreads soient tous deux augmentés à un niveau correspondant à MaxRequestWorkers.

Cette configuration laisse Apache HTTP sur un &quot;paramètre de préparation complet&quot; qui est une configuration haute performance pour les serveurs avec une RAM importante et plusieurs coeurs de processeur. Cette configuration produira les meilleurs temps de réponse possibles à partir d’Apache HTTP en maintenant des connexions ouvertes persistantes prêtes à servir les requêtes et supprimera tout délai dans la frai de nouveaux processus en réponse à des soudaines augmentations de trafic, comme lors des ventes Flash.
