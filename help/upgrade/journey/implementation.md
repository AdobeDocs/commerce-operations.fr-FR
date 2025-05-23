---
title: Mise à niveau
description: Découvrez les différentes phases de mise en oeuvre de la mise à niveau pour les projets Adobe Commerce.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# Mise à niveau

L’implémentation de la mise à niveau se compose de cinq phases :

- Analyse de la mise à niveau
- Développement et assurance qualité
- Test d’acceptation utilisateur (UAT) et préparation au lancement
- Launch
- Lancement de Post

## Analyse de la mise à niveau

L’analyse est sans doute la partie la plus importante du processus de mise à niveau. Une analyse bien exécutée vous permet de gagner du temps et de limiter les surprises à l’avenir. Le résultat de cette phase doit être une liste de contrôle de mise à niveau détaillée et un document avec toutes les dépendances.

Vous trouverez ci-dessous des éléments que vous pouvez inclure dans une analyse approfondie :

- **Portée de la version cible** : la documentation sur [Experience League](../../release/release-notes/overview.md) et les informations des webinaires de version des partenaires fournissent tous les détails que vous devez connaître sur la mise à niveau de votre cible.

- **[!DNL Upgrade Compatibility Tool]results** : cet outil facilite et accélère toute mise à niveau en comparant votre code actuel au code de la version cible et en produisant un rapport de tous les problèmes qui doivent être résolus. Voir le [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Les détails clés du rapport sont les suivants :

   - Version installée actuelle
   - Mise à niveau de la version cible
   - Nombre et détails des erreurs critiques détectées

  >[!TIP]
  >
  >Toutes ces informations (et plus encore) sont disponibles dans le [tableau de bord](../../tools/site-wide-analysis-tool/dashboard.md) de l’outil d’analyse à l’échelle du site.

- Mise à niveau des services pour prendre en charge la version cible. Utilisez le modèle de tableau suivant pour déterminer les services à mettre à niveau. Utilisez la [configuration requise](../../installation/system-requirements.md) pour déterminer ce qu’il faut ajouter à la colonne _Mettre à niveau vers_.


  | Service | Version actuelle | Mettre à niveau vers | Remarques |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7,4 | 8,1 |                                                          |
  | Redis | 6,0 | 6,2 |                                                          |
  | [!DNL RabbitMQ] | 3,8 | 3,9 | Non utilisé actuellement, mais nous devrions envisager de l’utiliser |
  | MariaDB (Cloud) | 10,4 | 10,6 |                                                          |
  | MySQL | 8,0 | -/-/ |                                                          |
  | Compositeur | 1.9.2 | 2,2 |                                                          |
  | Elasticsearch | 7,10 | 7,17 |                                                          |

- **Extensions et modules tiers** : utilisez ce modèle de tableau pour vous aider à comprendre l’état de vos extensions et personnalisations afin de pouvoir prendre des décisions stratégiques et définir des actions. Il s’agit d’une opportunité de remplacer toutes les extensions qui peuvent être natives d’Adobe Commerce afin de minimiser la complexité de votre projet. Utilisez la commande `bin/magento module:status` pour afficher une liste de modules et d’extensions.

  | # | Extension/<br>nom du module | Module de compositeur | Fournisseur | Version actuelle | Fonctionnalité | Compatible avec la dernière version de <br>Commerce ? | Problèmes | Est-ce que vous êtes natif de Commerce ? | Action | Remarques |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Nom et lien de l’extension | extension/<br>extension-magento-2 | Nom du fournisseur | Version installée | Exigences commerciales | Oui/Non | Liste des problèmes identifiés rencontrés avec cette extension | Oui/Non | Conserver/Remplacer/<br>Supprimer |       |

- **Modules personnalisés** : à l’instar du tableau de modules tiers, ce modèle vous permet de suivre et de comprendre l’état et les actions requis pour la mise à niveau des modules personnalisés.

  | # | Nom du module | Fonctionnalité | Obligatoire ? | Est-ce que vous êtes natif de Commerce ? | Action | Remarques |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Nom du module | Exigences commerciales | Oui/Non | Oui/Non | Conserver/Remplacer/Supprimer |       |

- **Packages de compositeur et dépendances dans le fichier compositeur.json qui nécessitent une mise à jour.**

En outre, les partenaires peuvent participer aux [versions bêta d’Adobe Commerce](../../release/beta.md) et utiliser les opportunités de version préliminaire pour obtenir un accès anticipé au code pour une prochaine version. L’accès anticipé au code aide les développeurs à se préparer avec suffisamment de temps pour terminer la mise à niveau d’ici la date de disponibilité générale (GA). Le code Beta est généralement publié cinq semaines avant la date de disponibilité générale et les versions préliminaires sont publiées deux semaines à l’avance.

## Développement et assurance qualité

Le test est la phase de mise à niveau qui nécessite le plus de temps. Par conséquent, ce processus doit être aussi automatisé que possible. Le _[Guide de test d’application](https://developer.adobe.com/commerce/testing/guide/)_ fournit des détails sur la configuration et l’utilisation des outils de test de plateforme et système pour une AQ plus rapide. Utilisez un environnement d’évaluation pour tester et valider votre mise à niveau avant de passer en production.

## UAT et préparation du lancement

UAT est l’une des dernières étapes de la mise à niveau qui nécessite la révision et la validation du site. Vous devez également décider quand déployer et si vous avez besoin d’une page de maintenance. Planifiez les processus cron et les messages tiers.

À l’approche de la date de déploiement, la communication est essentielle. Si plus de gens sont au courant du changement à l&#39;horizon, de son impact et de la manière dont ils doivent y faire face, alors il est plus probable que vous ayez un lancement réussi. N&#39;ayez pas peur de trop communiquer à chaque étape du chemin, cela augmente la probabilité de critiques éclatantes de la part de tous les participants une fois que vous êtes en ligne !

## Launch

Effectuez la mise à niveau en effectuant le déploiement vers les extensions de production et de mise à jour. Assurez-vous de tester les flux de chemins critiques avec des commandes simulées. Consultez ces [bonnes pratiques](../prepare/best-practices.md) pour obtenir des conseils sur le lancement avec des problèmes minimaux.

Suivez votre plan de communication et assurez-vous que toutes les parties prenantes sont informées de la mise à niveau et sont entièrement formées pour la prendre en charge.

Enfin, faites-le part à votre équipe afin de déterminer les leçons à tirer et les pièges à éviter. Cette rétrospective vous aide à améliorer le processus la prochaine fois.

## Post-Launch

Une fois votre site lancé, vérifiez vos données d’analyse, la console de recherche Google et d’autres ressources afin de vous assurer qu’il n’y a aucun problème inattendu et que tout fonctionne comme prévu.

Il est toujours préférable de garder un oeil sur les performances grâce à des outils de surveillance bien conçus. Il existe de nombreux outils et moyens pour surveiller les performances de votre site. Vous devez donc veiller à en choisir un qui corresponde bien à votre entreprise. Nous recommandons aux clients Adobe Commerce qui utilisent notre système de gestion de l’infrastructure cloud de profiter de services tels que [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=fr) pour surveiller les performances du site.
