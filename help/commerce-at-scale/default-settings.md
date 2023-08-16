---
title: Optimisation des performances d’Adobe Commerce
description: Préparez votre projet Adobe Commerce à utiliser Adobe Experience Manager en tant que CMS en modifiant certains paramètres par défaut.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
feature: Integration, Cache
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Optimisation des performances d’Adobe Commerce

## Emplacement géographique de l’AEM et de l’infrastructure Adobe Commerce

Pour réduire la latence entre l’éditeur AEM et Adobe Commerce GraphQL lors de la création de pages, la configuration initiale des deux infrastructures distinctes doit être hébergée dans la même région d’AWS (ou Azure). L’emplacement géographique choisi pour les deux clouds doit également être le plus proche de la majorité de votre base de clients, de sorte que les demandes GraphQL côté client soient diffusées à partir d’un emplacement géographique proche de la majorité de vos clients.

## Mise en cache de GraphQL dans Adobe Commerce

Lorsque le navigateur de l’utilisateur ou l’éditeur AEM appelle Adobe Commerce GraphQL, certains appels sont mis en cache en mode Fastly. Les requêtes mises en cache sont généralement celles qui contiennent des données non personnelles et qui sont peu susceptibles de changer fréquemment. Par exemple : catégories, categoryList et produits. Ceux qui ne sont pas explicitement mis en cache sont ceux qui changent régulièrement et si la mise en cache peut présenter des risques pour les données personnelles et les opérations sur le site, comme les requêtes de panier et de customerpaymentTokens.

GraphQL vous permet d’effectuer plusieurs requêtes dans un seul appel. Il est important de noter que si vous spécifiez une seule requête qu’Adobe Commerce ne met pas en cache avec de nombreuses autres requêtes qui ne peuvent pas être mises en cache, Adobe Commerce contournera le cache de toutes les requêtes de l’appel . Cela doit être pris en compte par les développeurs lors de la combinaison de plusieurs requêtes afin de s’assurer que les requêtes pouvant être mises en cache ne sont pas involontairement contournées.

>[!NOTE]
>
> Pour plus d’informations sur les requêtes pouvant être mises en cache et non mises en cache, voir Adobe Commerce [documentation destinée aux développeurs](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Tableau plat du catalogue

L’utilisation de tableaux plats pour les produits et les catégories n’est pas recommandée. L’utilisation de cette fonctionnalité obsolète peut entraîner des dégradations de performances et des problèmes d’indexation. Par conséquent, les catalogues plats doivent être désactivés via l’administrateur Adobe Commerce, dans la section storefront. Certains modules et personnalisations tiers ne nécessitent pas de tableaux plats pour fonctionner correctement. Il est recommandé d’effectuer une évaluation afin de comprendre les impacts et les risques liés à l’utilisation de tableaux plats lorsque vous choisissez d’utiliser ces extensions ou personnalisations.

## Protection d&#39;origine très rapide

Par défaut, la protection d’origine Fastly n’est pas activée. L’objectif de l’protection d’origine de Fastly est de réduire directement le trafic vers l’origine Adobe Commerce : lorsqu’une demande est reçue, un emplacement de périphérie Fastly (ou &quot;point de présence&quot; / POP) recherche le contenu mis en cache et le fournit. S’il n’est pas mis en cache, il continue à vérifier si le contenu y est mis en cache (si le contenu a déjà été demandé à partir d’un autre POP global, il sera mis en cache). Enfin, s’il n’est pas mis en cache sur le Protocole POP du Bouclier, il se dirigera uniquement vers le serveur d’origine.

Un protection d’origine rapide peut être activé dans les paramètres du serveur principal de configuration Fastly de votre administrateur Adobe Commerce. Pour des performances optimales, vous devez choisir un emplacement de protection le plus proche de votre centre de données d’origine Adobe Commerce.

## Optimisation rapide des images

Une fois que l’option de protection d’origine Fastly est activée, vous pouvez également activer Fastly Image Optimizer. Lorsque les images des catalogues de produits sont stockées sur Adobe Commerce, ce service permet de décharger rapidement et hors d’Adobe Commerce toutes les transformations d’images de catalogues de produits gourmands en ressources. Les temps de réponse des utilisateurs finaux sont également améliorés pour les temps de chargement des pages, car les images sont transformées à l’emplacement de périphérie, ce qui élimine la latence en réduisant le nombre de requêtes à l’origine Adobe Commerce.

L’optimisation rapide des images peut être activée en &quot;activant l’optimisation des images profondes&quot; dans la configuration Fastly dans l’administration, bien que seulement après l’activation de votre protection d’origine. Vous trouverez plus d’informations sur les configurations pour l’optimisation rapide des images dans Adobe Commerce. [documentation destinée aux développeurs](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Capture d’écran des paramètres d’optimisation des images Fastly dans l’administrateur Adobe Commerce](../assets/commerce-at-scale/image-optimization.svg)

## Désactiver les modules inutilisés

Si vous exécutez Adobe Commerce sans interface utilisateur, si vous ne diffusez que des requêtes par le biais du point de terminaison GraphQL et qu’aucune page de magasin front-end n’est diffusée directement à partir d’Adobe Commerce, de nombreux modules deviennent redondants et ne sont pas utilisés. En désactivant les modules inutilisés, votre base de code Adobe Commerce devient plus petite, moins complexe et pourrait donc offrir des améliorations de performances. La désactivation des modules sur Adobe Commerce peut être gérée à l’aide du compositeur. Les modules pouvant être désactivés dépendent des exigences de votre site. Aucune liste recommandée ne peut donc être fournie, car elle serait spécifique à l’implémentation d’Adobe Commerce par chaque client.

## Activation de la connexion MySQL et Redis

Par défaut, les connexions MySQL et Redis Slave ne sont pas activées dans Adobe Commerce sur le cloud. Cela est dû au fait que ces paramètres ne conviennent qu’aux clients qui attendent une charge très élevée. La latence Cross-AZ (Cross-Available Zones) est plus élevée avec des connexions esclaves activées. Ce paramètre réduit donc les performances d’une instance Adobe Commerce sur l’instance cloud dans le cas où l’instance ne reçoit que des niveaux de charge réguliers.

Si l’instance Adobe Commerce attend une charge extrême, l’activation de master-slave pour MySQL et Redis permet d’optimiser les performances en répartissant la charge sur la base de données MySQL ou les redis sur différents noeuds.

À titre de guide, dans les environnements à charge normale, l’activation de la connexion esclave ralentit les performances de 10 à 15 %. Mais sur les clusters avec une charge et un trafic élevés, il y a une amélioration des performances d&#39;environ 10 à 15 %. Par conséquent, il est important de charger le test de votre environnement avec les niveaux de trafic prévus afin d’évaluer si ce paramètre serait bénéfique pour les temps de performance en cours de chargement.

Pour activer/désactiver les connexions esclaves pour mysql et redis, vous devez modifier votre `.magento.env.yaml` afin d’inclure les éléments suivants :

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Pour l’architecture mise à l’échelle (architecture fractionnée - voir ci-dessous), les connexions esclaves Redis ne doivent pas être activées, car des erreurs s’affichent. Dans le cas d’une architecture partagée, il est recommandé de mettre en oeuvre la mise en cache L2 pour Redis.

## Passage à une Adobe Commerce sur une architecture mise à l’échelle (fractionnée) dans le cloud

Si, après toutes les configurations ci-dessus, les résultats du test de charge ou l’analyse des performances de l’infrastructure active indiquent toujours que les niveaux de charge vers Adobe Commerce sont d’un niveau qui atteint systématiquement le maximum des ressources du processeur et d’autres ressources système, alors un passage à une architecture mise à l’échelle (fractionnée) doit être pris en compte.

Avec une architecture Pro standard, il existe 3 noeuds, chacun contenant une pile technique complète. En effectuant une conversion vers une architecture à plusieurs niveaux, cela se transforme en 6 noeuds au minimum : 3 d’entre eux contiennent Elasticsearch, MariaDB, Redis et d’autres services principaux ; les 3 autres pour le traitement du trafic web contiennent phpfpm et NGINX. Il existe des possibilités de mise à l’échelle plus importantes avec un niveau partagé : les noeuds principaux contenant des bases de données peuvent être mis à l’échelle verticalement ; les noeuds web peuvent être mis à l’échelle horizontalement et verticalement, offrant ainsi une grande flexibilité pour développer l’infrastructure à la demande pendant la période définie d’activité à charge élevée et sur les noeuds où les ressources supplémentaires sont nécessaires.

Si une décision a été prise de passer à une architecture à plusieurs niveaux en raison des fortes attentes en matière de charge sur votre site, une discussion doit être engagée avec votre équipe de compte d’Adobe sur les étapes à suivre pour activer cette fonctionnalité.
