---
title: Conseils sur les tests de performance
description: Découvrez comment définir des indicateurs de performance clés pour lancer votre solution Adobe Commerce et Adobe Experience Manager.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---

# Conseils sur les tests de performance

Pour évaluer l’efficacité de toutes les modifications ci-dessus, des tests de performance approfondis doivent être exécutés avant la mise en service et avant tout déploiement important futur dans vos environnements de production. Lors de la planification de vos tests de charge, il est important de simuler autant que possible le trafic réel des consommateurs.

Les zones les plus gourmandes en ressources du site AEM/CIF/Adobe Commerce sont celles qui ne peuvent pas être mises en cache, comme le processus de passage en caisse et la recherche de site. La navigation statique des pages, et donc pouvant être mise en cache, comme pour les pages de détails des produits (PDP) et les pages de liste de produits (PLP), constitue la majeure partie du trafic vers un site d’e-commerce en général. Les scripts et les scénarios du test doivent donc refléter cela pour mesurer les limites de la plateforme.

Le fait qu’un seul script s’exécute pour votre test de chargement navigue sur le site sans temps d’attente entre les étapes, et termine toujours le processus de passage en caisse chaque fois ne donne pas une indication fiable des limites de la plateforme, car ce n’est pas ce que serait un scénario réel.

La définition des indicateurs de performance clés doit être la première étape de votre plan de test de performance : définissez des mesures que vous pouvez tester lors de votre test initial, puis mesurer à nouveau à l’avenir, et de manière récurrente une fois le site actif. Cela vous permet de suivre les performances de votre site au fil du temps, avant et après le lancement. Voici des exemples d’indicateurs clés de performance à définir :

- Temps de réponse moyen : temps jusqu’au premier octet ou dernier octet
- Latence
- Octets/s (débit)
- Taux d’erreur
- Commandes par heure
- Pages vues par heure
- Utilisateurs uniques par heure (acheteurs simultanés)

## Instructions Jeter

Les instructions de niveau supérieur Jeter suivantes doivent être prises en compte lors du développement de vos tests de chargement AEM/CIF/Adobe Commerce :

- Divisez votre script en scénarios configurables, qui doivent couvrir, par exemple :
   - Ouvrir la page d’accueil
   - Ouvrir la page de catégorie (PLP)
   - Afficher les produits simples (PDP) : 2 boucles dans chaque itération
   - Afficher les produits configurables - 2 boucles au sein de chaque itération
      - Par exemple, définissez les étapes ci-dessus sur 60 % du trafic.
   - Recherche de produit
      - Par exemple, définissez la recherche dans le catalogue sur 37 % du trafic.
   - Panier et passage en caisse
      - Par exemple, un utilisateur qui exécute la partie Panier et passage en caisse du script doit définir par défaut sur un taux de conversion standard de site d’e-commerce d’environ 3 %.
      - Comme le flux de passage en caisse n’est pas mis en cache et qu’il s’agit généralement d’une opération gourmande en ressources, la définition d’un chiffre irréaliste pour le nombre de personnes qui exécutent des commandes par rapport au nombre de navigateurs du site donne un résultat peu fiable pour le volume de trafic que votre site peut traiter.
- Nettoyez tous les caches avant chaque exécution de test :
   - Le cache du Dispatcher AEM doit être entièrement nettoyé.
   - Adobe Commerce Le cache rapide et interne doit être complètement vidé et nettoyé. Pour ce faire, vous pouvez utiliser le contrôle du cache dans l’administration Adobe Commerce.
- Inclure une période de progression dans le test Jeter : n’avoir aucune période de progression signifie pas d’augmentation progressive du trafic et aucune chance pour le site de mettre en cache les pages et composants fréquemment consultés de la page. Dans la vie réelle, il serait inhabituel que tout le trafic de pointe arrive sur un site entièrement non mis en cache exactement au même moment. Par conséquent, une période de progression doit être incluse dans les scripts de test Jeter pour permettre au cache de se développer comme ce serait le cas sur un site de commerce électronique réel.
- Un &quot;temps d’attente&quot; entre chaque étape d’une itération doit être utilisé ; en réalité, un utilisateur ne le ferait pas.
saut immédiatement à la page suivante du site pendant leur parcours : il y aurait un temps d’attente pendant que l’utilisateur lisait la page et décidait de sa prochaine action.
- Si vous définissez les groupes de threads sur une boucle infinie, mais pour une durée définie de x (par exemple, 60 minutes), vous obtiendrez un test répétable, avec des temps de réponse médians comparables aux exécutions de test précédentes. Cela signifie qu’après la période de montée en charge de la configuration, le nombre cible d’utilisateurs virtuels s’exécute simultanément, ce qui se poursuit pendant la durée de la boucle définie.
- Le temps médian doit être utilisé pour améliorer/diminuer le temps de réponse moyen, et non pas la moyenne. If
il existe plusieurs résultats de périphérie qui prennent beaucoup plus de temps que les autres résultats, alors cela ferait biaiser ce résultat moyen, mais ce qui nous intéresse dans le temps de réponse de l’utilisateur final pour la majorité des utilisateurs, qui est plus adapté à la mesure médiane.
- Les ressources incorporées ne sont pas collectées par défaut dans jmètre (par exemple, JS, CSS et d’autres ressources téléchargées lorsqu’un utilisateur réel visite la page). Cela peut être activé, mais uniquement pour le domaine que vous testez - les appels de ressources externes doivent toujours être exclus (par exemple, nous ne voulons pas inclure de temps de réponse provenant de services hébergés en externe, par exemple. code google analytics, car nous n’avons aucun contrôle sur eux).
- HTTP Cache Manager doit être activé, ce qui permet à Jeter de mettre en cache les éléments de page pendant un parcours comme
le parcours d’un vrai utilisateur lors de sa navigation sur le site web dans son propre navigateur. Pendant leur parcours sur le site, le navigateur de l’utilisateur téléchargerait la ressource incorporée associée une seule fois, puis celles-ci seraient mises en cache par le navigateur de l’utilisateur. En outre, si le même utilisateur revient sur le site un certain temps après sa visite initiale, il se peut que ce soit toujours le cache dans lequel ces ressources sont mises en cache.
- Les écouteurs doivent être maintenus dans les exécutions de test de charge réelles (par exemple, &quot;Afficher l’arborescence des résultats&quot; et &quot;Rapport d’agrégation&quot;). L’inclusion de cela dans l’exécution de test de charge réel autre qu’une interface utilisateur graphique peut avoir un impact sur les résultats de performances signalés par Jeter, car les ressources sont utilisées lors de l’exécution de test réelle pour générer les rapports. Ces écouteurs ont été supprimés du script de test pour être remplacés par un fichier de résultats JTL, qui peut ensuite être traité à l’aide de la fonctionnalité Tableau de bord des rapports de Jeter.
- Délai de réponse cible pour l’évaluation de sorte que le &quot;score Apdex&quot; du rapport de tableau de bord puisse être utilisé rapidement pour mesurer l’effet des modifications sur les performances entre les exécutions de test. Le score Apdex est basé sur un certain nombre de personnes qui peuvent accéder au site en un temps tolérable . Si le temps de réponse est supérieur à une certaine quantité &quot;frustrante&quot;, cela réduit le score. Les heures peuvent être définies à l’aide des paramètres &quot;apdex_content_seuil&quot; et &quot;apdex_tolerated_seuil&quot;.
- Définissez une mesure &quot;Commandes par heure&quot; cible à présenter aux utilisateurs professionnels, et non à un nombre d’utilisateurs virtuels. &quot;Utilisateurs virtuels&quot; peut être un sujet complexe pour comprendre ce que le test mesure dans la vie réelle. En calculant le taux de conversion du site, les commandes par heure, le temps moyen passé par un utilisateur sur le site et le temps d’analyse entre chaque chargement de page, vous pouvez utiliser les calculs standard du secteur pour présenter différents scénarios de test de charge en fonction des commandes par heure à réaliser.
- Enfin, votre serveur de test Jeter doit être exécuté sur un serveur géographiquement proche de l’endroit d’où provient la majorité du trafic de vos utilisateurs et de l’endroit où votre infrastructure cloud est hébergée. Espérons que ce serait le même.
