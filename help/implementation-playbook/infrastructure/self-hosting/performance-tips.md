---
title: Conseils sur les performances d’Adobe Commerce en auto-hébergement
description: Découvrez les conseils sur les performances de l’auto-hébergement, ainsi que les concepts et bonnes pratiques à prendre en compte.
landing-page-description: Découvrez quelques concepts et éléments de performance à prendre en compte lors de l’hébergement d’Adobe Commerce par vous-même.
short-description: Découvrez les stratégies et les concepts de performances pour héberger vous-même Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Conseils de performance Adobe Commerce pour l’auto-hébergement

L&#39;utilisation d&#39;une plate-forme de commerce électronique flexible et puissante ne signifie pas que vous devez sacrifier les performances. De nombreuses améliorations ont été apportées à l’application principale depuis la création d’Adobe Commerce. Dans la version 2.5.4, l’équipe d’ingénierie d’Adobe Commerce a effectué un test défini pour tester l’application. Les résultats du test ont démontré qu’Adobe Commerce est capable de gérer un catalogue volumineux de plus de 240 millions de SKU, les délais de demande d’API sont exceptionnels, en moyenne, 300 ms, et le nombre de pages vues et de commandes passées par heure est phénoménal et atteint 2 millions de pages vues et 208 000 commandes par heure.

Consultez les derniers résultats de comparaison en vous rendant sur [Experience League - Adobe Commerce - Manuel de mise en oeuvre - Benchmarks](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Pour optimiser les éléments, suivez ces normes lorsque vous ajoutez des personnalisations et une complexité supplémentaire à votre projet.

Les sections suivantes abordent des sujets à prendre en compte et fournissent des conseils pour optimiser votre mise en oeuvre de l’auto-hébergement.

## Varnish

Le vernis est un proxy inverse HTTP avec cache. Aussi compliqué que cela puisse paraître, les réponses sont rapides pour s’assurer que les demandes sont renvoyées plus rapidement que si l’élément devait être récupéré de la source. L’exécution d’un site Adobe Commerce sans aucune version de vernis ralentit le chargement des pages et ralentit d’autres mesures clés. Le vernis peut être un peu difficile à configurer et à gérer soi-même, mais nous avons ce sujet en Experience League [Configurer le vernis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} pour mieux comprendre son utilisation avec Adobe Commerce. Une alternative consiste à utiliser une solution cloud. Bien qu’il y ait beaucoup à considérer, Fastly a été choisi comme solution pour Adobe Commerce sur le cloud. C&#39;est une version de Fastly, basé sur le cloud, qui utilise des VCL et de nombreuses facettes de vernis.

Trouver une solution qui convienne le mieux à votre application, configuration, budget et capacités techniques est difficile à réaliser. L’utilisation d’une option basée sur le cloud entraîne la disparition de toutes les parties du contenu dur en ce qui concerne la gestion, la configuration, les serveurs et les autres composants d’infrastructure. Elle a été choisie par l’équipe cloud d’Adobe Commerce comme solution en raison de ses performances, de son évolutivité, de son débit et de nombreuses autres mesures clés.

En choisissant une bonne solution pour votre projet en ce qui concerne le vernis, vous vous préparez pour obtenir les meilleures performances pour vos clients et évitez que l’application commerciale ne travaille plus dur.

## CDN

Outre le fait que Varnish est un actif précieux pour votre projet Adobe Commerce, un réseau de diffusion de contenu est ajouté à la suite. Avec votre vernis, un CDN peut fournir des instances en cache pour votre CSS, des ressources de page telles que des images pour réduire la bande passante de votre application Adobe Commerce. Il peut mettre en cache les réponses GraphQL afin d’optimiser les avantages d’un site Adobe Commerce sans interface utilisateur. Certains CDN fournissent une optimisation des images, un pare-feu d’application web et d’autres fonctionnalités.

Adobe Commerce sur le cloud a choisi d’utiliser Fastly pour son cache de vernis, mais aussi comme son réseau de diffusion de contenu. Cette solution unique offre une myriade de fonctionnalités pour offrir une expérience exceptionnelle à Adobe Commerce sur les clients cloud. Vous pouvez lire la présentation des services Fastly dans Experience League [Présentation des services rapides](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Un réseau de diffusion de contenu fournit du contenu de diffusion optimisé et sécurisé pour le projet Adobe Commerce. S’il ne s’agit pas d’un composant obligatoire de votre projet, celui-ci doit être pris en compte au fur et à mesure que votre site se développe et que le nombre de visiteurs augmente. En fournissant un réseau de diffusion de contenu, vous pouvez retarder l’ajout de matériel supplémentaire à l’infrastructure ou mettre à l’échelle l’infrastructure existante en raison de la charge supprimée de chaque demande.

## Désactiver les modules

La désactivation d’un module inutilisé doit être envisagée, mais pas prise à la légère. Cette technique permet de réduire les frais généraux et le temps de traitement de certaines requêtes, mais certains effets secondaires doivent être pris en compte. Il arrive souvent qu’un développeur présume qu’un module est disponible lors de la création de fonctionnalités. Cela est souvent sans danger, à moins qu’ils aient choisi d’utiliser certaines classes trouvées dans un module qui a été désactivé.

La désactivation d’un module tel que la &quot;newsletter&quot; native est un événement assez courant. C’est le cas en particulier lorsque le propriétaire du magasin possède une société tierce qui gère sa newsletter. Cela peut poser problème lorsqu’un module tiers est installé et, pour une raison quelconque, ils ont décidé d’utiliser une classe de la newsletter. Cette dépendance accidentelle sera probablement interceptée lors d’une installation et d’un test initiaux, mais vous êtes alors forcé de décider si vous souhaitez conserver ce module tiers, activer la newsletter, puis tester la régression sur le site à la recherche de tout comportement bizarre introduit. Ou trouvez-vous un remplacement pour ce module tiers. Les deux décisions comportent des risques, du temps et peut-être des bogues.

Avant de désactiver les modules inutilisés, assurez-vous de ne pas avoir de tests unitaires, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} charger des tests ou des demandes d’API qui peuvent être affectées.

## Exiger que les normes de codage Adobe Commerce et PHP soient respectées pour chaque requête de tirage

Adobe Commerce comporte un ensemble de [Normes de codage](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Elles permettent de s’assurer qu’un modèle, un style et une conception similaires sont suivis quel que soit le type de développement logiciel. Lorsque vous contribuez au code base Adobe Commerce, il s’agit d’une exigence. Cependant, si vous choisissez de suivre cette méthodologie pour le développement personnalisé, vous devez établir une pierre angulaire solide pour tous les développeurs, actuels et futurs. Lorsque vous demandez à toutes les demandes d’extraction de transmettre une norme de code, assurez-vous que tout le monde peut comprendre et s’attendre aux mêmes modèles de développement cohérents.

Pour accompagner les normes de codage Adobe Commerce, l’autre base utilisée est les normes de codage de base PHP. Elle doit être clairement définie dans votre développeur afin de déterminer les normes que vous devez respecter et tout écart acceptable. Cependant, une solution de secours doit être apportée au guide géré publiquement qui se trouve à l’adresse [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Une position ferme sur la suite des PSR-1 et PSR-12. S’assurer que les développeurs qui contribuent au projet suivent ces éléments permet de s’assurer qu’il n’existe pas de fichiers et de modèles étrangement structurés. Cela permet également de s’assurer que les futurs développeurs puissent lire et comprendre rapidement le code qu’ils sont en train de vérifier. Plus vous respectez ces modèles et normes de codage, plus les futurs efforts de développement doivent être plus faciles à lire et plus rapides à mettre en oeuvre.

## Exécution de tests de charge après chaque déploiement

L’exécution d’un test de charge après chaque déploiement peut sembler excessive. Cependant, si cette méthodologie est suivie, il est possible de suivre et d’atténuer l’opportunité de nouvelles fonctionnalités qui provoquent une baisse des performances.

Outre la détection de la dégradation des performances à partir du nouveau code, le fait de disposer d’une référence historique des mesures clés de votre site peut vous aider à déterminer quand un nouvel outil ou une nouvelle infrastructure est activé. Par exemple, avant de payer la société d’hébergement pour augmenter la taille de votre environnement et espérer que vous obtenez l’augmentation de performances attendue, vous pouvez configurer un environnement d’évaluation avec les nouvelles configurations et exécuter un test de charge pour voir quel serait le résultat réel.

Ces tests peuvent être automatisés et faire partie de votre pipeline CI/CD. Pour cette raison, vous pouvez également avoir des règles en place qui prennent les résultats et bloquent éventuellement la fusion des fonctionnalités si une trop grande déviation de la norme se produit. Le nombre de cas d’utilisation de ces données est illimité, mais sans démarrer ce processus, vous ne réaliserez peut-être jamais son potentiel.

Adobe Commerce a une bonne écriture sur ce sujet dans Experience League [Conseils sur les tests de performance](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
