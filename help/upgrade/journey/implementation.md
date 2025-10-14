---
title: Mise à niveau de l’implémentation
description: Découvrez les différentes phases de la mise en œuvre de la mise à niveau pour les projets Adobe Commerce.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# Mise à niveau de l’implémentation

L’implémentation de la mise à niveau se compose de cinq phases :

- Analyse de la mise à niveau
- Développement et assurance qualité (QA)
- Test d’acceptation utilisateur (UAT) et préparation du lancement
- Launch
- Après le lancement

## Analyse de la mise à niveau

L’analyse est sans doute la partie la plus importante du processus de mise à niveau. Une analyse bien exécutée vous permet de gagner du temps et limite les surprises à l’avenir. Le résultat de cette phase doit être une liste de contrôle de mise à niveau détaillée et un document avec toutes les dépendances.

Voici des éléments que vous pouvez inclure dans une analyse approfondie :

- **Portée de la mise à jour de Target**—La documentation sur [Experience League](../../release/release-notes/overview.md) ainsi que les informations des webinaires de mise à jour des partenaires fournissent tous les détails que vous devez connaître sur votre mise à niveau de Target.

- **[!DNL Upgrade Compatibility Tool]des résultats** : cet outil accélère et facilite toute mise à niveau en comparant votre code actuel au code de la version cible et en générant un rapport sur tous les problèmes à résoudre. Voir la [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Les principaux détails du rapport sont les suivants :

   - Version installée actuelle
   - Mettre à niveau la version cible
   - Nombre et détails des erreurs critiques détectées

  >[!TIP]
  >
  >Toutes ces informations (et d’autres encore) sont disponibles dans le tableau de bord de l’outil d’analyse à l’échelle du site [&#128279;](../../tools/site-wide-analysis-tool/dashboard.md).

- Mise à niveau des services pour la prise en charge de la version cible. Utilisez le modèle de tableau suivant pour indiquer les services à mettre à niveau. Utilisez la [configuration requise](../../installation/system-requirements.md) pour déterminer les éléments à ajouter à la colonne _Mettre à niveau vers_.


  | Service | Version actuelle | Mettre à niveau vers | Remarques |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7,4 | 8,1 |                                                          |
  | Redis | 6,0 | 6,2 |                                                          |
  | [!DNL RabbitMQ] | 3,8 | 3,9 | Actuellement non utilisé, mais nous devrions envisager de l’utiliser |
  | MariaDB (cloud) | 10,4 | 10,6 |                                                          |
  | MySQL | 8,0 | -/-/ |                                                          |
  | Compositeur | 1,9,2 | 2.2 |                                                          |
  | Elasticsearch | 7,10 | 7,17 |                                                          |

- **Extensions et modules tiers** : utilisez ce modèle de tableau pour mieux comprendre le statut de vos extensions et de vos personnalisations afin de pouvoir prendre des décisions stratégiques et définir des actions. Il s’agit d’une opportunité de remplacer toutes les extensions qui peuvent être natives d’Adobe Commerce afin de minimiser la complexité de votre projet. Utilisez la commande `bin/magento module:status` pour afficher la liste des modules et des extensions.

  | # | Extension/<br>nom du module | Package du compositeur | Fournisseur | Version actuelle | Fonctionnalité | Compatible avec la dernière version de <br>Commerce ? | Événements | Vous êtes natif de Commerce ? | Action | Remarques |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Nom de l’extension et lien | extension/<br>extensionx-magento-2 | Nom du fournisseur | Version installée | Exigences de l’entreprise | Oui/Non | Liste des problèmes identifiés rencontrés avec cette extension | Oui/Non | Conserver/Remplacer/<br>Supprimer |       |

- **Modules personnalisés** : tout comme le tableau des modules tiers, ce modèle vous aide à suivre et à comprendre le statut et les actions requis pour mettre à niveau les modules personnalisés.

  | # | Nom du module | Fonctionnalité | Obligatoire ? | Vous êtes natif de Commerce ? | Action | Remarques |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Nom du module | Exigences de l’entreprise | Oui/Non | Oui/Non | Conserver/Remplacer/Supprimer |       |

- **Packages de compositeurs et dépendances de composer.json nécessitant une mise à jour.**

En outre, les partenaires peuvent participer aux [versions bêta d’Adobe Commerce](../../release/beta.md) et utiliser les opportunités de version préliminaire pour obtenir un accès anticipé au code d’une prochaine version. Accéder au code dès le début permet aux développeurs de se préparer suffisamment à temps pour terminer la mise à niveau à la date de disponibilité générale (GA). Le code Beta est généralement publié cinq semaines avant la date de disponibilité générale et les versions préliminaires sont publiées deux semaines à l’avance.

## Développement et assurance qualité

Les tests sont la phase d’une mise à niveau qui nécessite le plus de temps. Par conséquent, ce processus doit être aussi automatisé que possible. Le _[Guide de test de l’application &#x200B;](https://developer.adobe.com/commerce/testing/guide/)_ fournit des détails sur la configuration et l’utilisation des outils de test de plateforme et de système pour accélérer l’assurance qualité. Utilisez un environnement d’évaluation pour tester et valider votre mise à niveau avant de passer en production.

## UAT et préparation du lancement

L’UAT est l’une des dernières étapes de la mise à niveau qui nécessite l’examen et la validation du site. Vous devez également décider quand déployer et si vous avez besoin d’une page de maintenance. Planifiez les processus cron et les messages tiers.

À l’approche de la date de déploiement, la communication est essentielle. Si plus de gens sont au courant du changement à l&#39;horizon, de ses répercussions sur eux et de la façon dont ils doivent y faire face, alors vous avez plus de chances de réussir votre lancement. N&#39;ayez pas peur de trop communiquer à chaque étape - cela augmente la probabilité d&#39;avoir des commentaires élogieux de la part de toutes les personnes impliquées une fois que vous êtes en ligne !

## Launch

Effectuez la mise à niveau en déployant en production et en mettant à jour les extensions. Veillez à tester les flux de chemins critiques avec des commandes simulées. Consultez ces [bonnes pratiques](../prepare/best-practices.md) pour obtenir quelques conseils sur le lancement d’avec un minimum de problèmes.

Suivez votre plan de communication et assurez-vous que toutes les parties prenantes sont au courant de la mise à niveau et qu’elles sont entièrement formées pour la prendre en charge.

Enfin, faites le point avec votre équipe pour déterminer les leçons apprises et les pièges à éviter. Cette rétrospective vous aidera à améliorer le processus la prochaine fois.

## Après le lancement

Une fois votre site lancé, vérifiez vos données d’analyse, la console de recherche Google et d’autres ressources pour vous assurer qu’il n’y a aucun problème inattendu et que tout fonctionne comme prévu.

Il est toujours préférable de surveiller les performances à l’aide d’outils de surveillance bien conçus. Il existe de nombreux outils et moyens de surveiller les performances de votre site. Veillez donc à en choisir un qui correspond bien à votre organisation. Nous recommandons aux clients Adobe Commerce qui utilisent notre système de gestion de l’infrastructure cloud de tirer parti de services tels que [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=fr) pour surveiller les performances du site.
