---
title: Mise à niveau
description: Découvrez les différentes phases de mise en oeuvre de la mise à niveau pour les projets Adobe Commerce et Magento Open Source.
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 1%

---


# Mise à niveau

L’implémentation de la mise à niveau se compose de cinq phases :

- Analyse de la mise à niveau
- Développement et assurance qualité
- Test d’acceptation utilisateur (UAT) et préparation au lancement
- Launch
- Post-lancement

## Analyse de la mise à niveau

L’analyse est sans doute la partie la plus importante du processus de mise à niveau. Une analyse bien exécutée vous permet de gagner du temps et de limiter les surprises à l’avenir. Le résultat de cette phase doit être une liste de contrôle de mise à niveau détaillée et un document avec toutes les dépendances.

Vous trouverez ci-dessous des éléments que vous pouvez inclure dans une analyse approfondie :

- **Portée de la version cible**—Documentation sur [Documents de développement Commerce](https://devdocs.magento.com) et les informations des webinaires de version des partenaires fournissent tous les détails que vous devez connaître sur votre mise à niveau vers target.

- **[!DNL Upgrade Compatibility Tool]résultats**—Cet outil facilite toute mise à niveau en comparant votre code actuel au code de la version cible et en produisant un rapport de tous les problèmes qui doivent être résolus. Voir [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Voici les principaux détails du rapport :

   - Version installée actuelle
   - Mise à niveau de la version cible
   - Nombre et détails des erreurs critiques détectées

- Mise à niveau des services pour la prise en charge de la version cible. Utilisez le modèle de tableau suivant pour déterminer les services à mettre à niveau. Utilisez la variable [configuration requise](../../installation/system-requirements.md) pour déterminer les éléments à ajouter à la variable _Mettre à niveau vers_ colonne .


   | Service | Version actuelle | Mettre à niveau vers | Remarques |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.2.33 | 8.1 |  |
   | Redis | 5,05 | 6.0 |  |
   | [!DNL RabbitMQ] | 3,7 | 3,8 | Non utilisé actuellement, mais nous devrions envisager de l’utiliser |
   | MariaDB (Cloud) | 10.2.33 | 10.4 |  |
   | MySQL | 8,0 |  |  |
   | Compositeur | 1.9.2 | 2,0 |  |
   | Elasticsearch | 7,7 | 7,10 |  |

- **Extensions et modules tiers**: utilisez ce modèle de tableau pour vous aider à comprendre l’état de vos extensions et personnalisations afin que vous puissiez prendre des décisions stratégiques et définir des actions. Il s’agit d’une opportunité de remplacer toutes les extensions qui peuvent être natives d’Adobe Commerce ou de Magento Open Source afin de minimiser la complexité de votre projet. Utilisez la variable `bin/magento module:status` pour afficher une liste de modules et d’extensions.

   | # | Extension/<br>nom du module | Module de compositeur | Fournisseur | Version actuelle | Fonctionnalité | Compatible avec la dernière version<br>Version commerciale ? | Problèmes | Natif de Commerce ? | Action | Remarques |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Nom et lien de l’extension | extension/<br>extensionx-magento-2 | Nom du fournisseur | Version installée | Exigences commerciales | Oui/Non | Liste des problèmes identifiés rencontrés avec cette extension | Oui/Non | Conserver/Remplacer<br>Supprimer |  |

- **Modules personnalisés**: à l’instar du tableau des modules tiers, ce modèle vous permet de suivre et de comprendre l’état et les actions requis pour la mise à niveau des modules personnalisés.

   | # | Nom du module | Fonctionnalité | Obligatoire ? | Natif de Commerce ? | Action | Remarques |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Nom du module | Exigences commerciales | Oui/Non | Oui/Non | Conserver/Remplacer/Supprimer |  |

- **Modules compositeur et dépendances dans le fichier compositeur.json qui nécessitent une mise à jour.**

En outre, les partenaires peuvent participer au [Programme Adobe Commerce bêta](https://devdocs.magento.com/release/beta-program.html) et utiliser les opportunités de préversion pour obtenir un accès anticipé au code pour une prochaine version. L’accès anticipé au code aide les développeurs à se préparer avec suffisamment de temps pour terminer la mise à niveau d’ici la date de disponibilité générale (GA). Le code bêta est généralement publié cinq semaines avant la date de disponibilité générale et les versions préliminaires sont publiées deux semaines à l’avance. Pour la version 2.4.4, Adobe a commencé à publier le code bêta cinq mois avant la date de disponibilité générale (8 mars 2022), de sorte que les partenaires puissent commencer à préparer cette mise à niveau dès maintenant. [inscription au programme](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Développement et assurance qualité

Le test est la phase de mise à niveau qui nécessite le plus de temps. Par conséquent, ce processus doit être aussi automatisé que possible. Le _[Guide de test d’application](https://developer.adobe.com/commerce/testing/guide/)_ fournit des détails sur la configuration et l’utilisation des outils de test de plateforme et système pour une AQ plus rapide. Utilisez un environnement d’évaluation pour tester et valider votre mise à niveau avant de passer en production.

## UAT et préparation du lancement

UAT est l’une des dernières étapes de la mise à niveau qui nécessite la révision et la validation du site. Vous devez également décider quand déployer et si vous avez besoin d’une page de maintenance. Planifiez les processus cron et les messages tiers.

À l’approche de la date de déploiement, la communication est essentielle. Si plus de gens sont au courant du changement à l&#39;horizon, de son impact et de la manière dont ils doivent y faire face, alors il est plus probable que vous ayez un lancement réussi. N&#39;ayez pas peur de trop communiquer à chaque étape du chemin, cela augmente la probabilité de critiques éclatantes de la part de tous les participants une fois que vous êtes en ligne !

## Launch

Effectuez la mise à niveau en effectuant le déploiement vers les extensions de production et de mise à jour. Assurez-vous de tester les flux de chemins critiques avec des commandes simulées. Consultez ces [bonnes pratiques](../prepare/best-practices.md) pour obtenir des conseils sur le lancement avec un minimum de problèmes.

Suivez votre plan de communication et assurez-vous que toutes les parties prenantes sont informées de la mise à niveau et sont entièrement formées pour la prendre en charge.

Enfin, faites-le part à votre équipe afin de déterminer les leçons à tirer et les pièges à éviter. Cette rétrospective vous aide à améliorer le processus la prochaine fois.

## Après le lancement

Une fois votre site lancé, vérifiez vos données d’analyse, la console de recherche Google et d’autres ressources afin de vous assurer qu’il n’y a aucun problème inattendu et que tout fonctionne comme prévu.

Il est toujours préférable de garder un oeil sur les performances grâce à des outils de surveillance bien conçus. Il existe de nombreux outils et moyens pour surveiller les performances de votre site. Vous devez donc veiller à en choisir un qui corresponde bien à votre entreprise. Nous recommandons aux clients Adobe Commerce qui utilisent notre système de gestion de l’infrastructure cloud de profiter de services tels que [Nouvelle relique](https://devdocs.magento.com/cloud/project/new-relic.html) pour surveiller les performances du site.
