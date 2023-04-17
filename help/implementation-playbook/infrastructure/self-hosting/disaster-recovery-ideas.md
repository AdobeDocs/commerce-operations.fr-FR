---
title: Récupération après sinistre Adobe Commerce auto-hébergée
description: Découvrez les idées et les concepts de reprise sur sinistre auto-hébergés ainsi que les bonnes pratiques à prendre en compte.
landing-page-description: Découvrez quelques concepts et éléments à prendre en compte lors de l’hébergement d’Adobe Commerce seul.
short-description: Découvrez les stratégies et les concepts de reprise après sinistre pour héberger vous-même Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 6e361169889c8fe1c176d3a3283d52699dfa3b85
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---


# Idées de reprise sur sinistre d’Adobe Commerce auto-hébergées

La reprise sur sinistre de cet article englobe un déploiement en échec. Bien que l&#39;ensemble du processus ne soit pas le même, des principes similaires s&#39;appliquent. Une catastrophe peut être due à un déploiement de production en échec, à un serveur qui ne répond plus, à la découverte d’un exploit et à de nombreux autres scénarios. Lorsque le processus de récupération d’un déploiement en échec ne nécessite que deux étapes simples, la récupération d’un exploit peut être beaucoup plus difficile. En raison de la complexité des environnements, des variations d’hébergement et d’autres complexités, cet article fournit des idées et des concepts, mais vous devez poursuivre l’enquête par vous-même. Vous pouvez ainsi vous assurer de concevoir une stratégie adaptée aux besoins de votre entreprise.

## Processus de récupération pratique

Pratique, Pratique, Pratique. Il existe une raison pour laquelle les pratiques apparaissent en premier sur la liste de la reprise après sinistre. Il est beaucoup trop facile de mettre en place un plan de récupération, mais ne jamais l&#39;exécuter. Si vous ne vous entraînez pas suffisamment, vous êtes susceptible d’erreurs, d’étapes manquées et de prolonger une récupération réelle. C’est à vous et à vos partenaires d’affaires de décider de la reprise de vos activités. Faire du processus de récupération un événement annuel peut être suffisant, mais une discussion approfondie avec les décideurs de votre entreprise doit inclure plusieurs sujets clés. Ces rubriques les aident à comprendre pourquoi la pratique est importante et devrait être attendue. Voici quelques rubriques qui vous aideront à démarrer la conversation :

* La pratique réduit le temps d’arrêt réel lorsqu’un événement se produit. Si une exécution d’entraînement à sec diminue votre site d’une heure par an, le temps d’arrêt réel d’un événement réel peut être réduit de plusieurs heures. Il n’est pas rare qu’une récupération d’un site dure huit heures ou plus. En vous entraînant souvent à cet événement, vous pouvez réduire le temps nécessaire à chaque phase et vous pouvez ainsi récupérer plus rapidement.
* Les temps d’arrêt planifiés pour ces exécutions d’entraînement peuvent coïncider avec les correctifs du serveur, les ajustements d’inventaire ou toute autre opération qui doit être effectuée de manière régulière.
* Pratiquez différents scénarios plutôt que le même. Prenez le temps occasionnellement d’effectuer une récupération complète à partir d’une date précédente. Cela inclut des éléments tels que la recherche et l’utilisation d’une copie archivée de la base de données, la restauration du code pour qu’il corresponde à la date. Il peut être plus facile de récupérer d’un déploiement en échec, où vous devez simplement restaurer la validation précédente.
* Vérifiez que le processus de récupération fonctionne, et que parfois les bases de données archivées peuvent devenir corrompues. Ce faisant, il garantit que tout peut être récupéré et qu&#39;il est fonctionnel. Trouver et restaurer une ancienne base de données prend du temps, il faut savoir combien de temps cette partie du processus peut durer.
* Vérifiez que toutes les modifications apportées aux configurations sont documentées. Cela garantit que toute récupération d’une base de données plus ancienne bénéficie de nouvelles modifications de configuration qui doivent être fonctionnelles. Par exemple, si votre clé API a été remplacée par votre processeur de paiement au cours des derniers jours. En disposant d’un bon processus de gestion des changements, la recherche de ces mises à jour clés permet au processus de se dérouler comme prévu.

## Sauvegardes de base de données

Les sauvegardes de la base de données doivent être assez régulières. Il n’est pas rare d’avoir des instantanés horaires, quotidiens, hebdomadaires et mensuels. Les sauvegardes doivent finalement être déplacées vers un stockage à long terme. Ce stockage à long terme peut se produire chaque fois que l’équipe commerciale ou technologique décide de suffisamment de temps pour qu’une récupération rapide ne soit plus nécessaire. Une récupération à partir d’un stockage à long terme ajoute du temps au processus de récupération. Il faut donc faire attention à la date à laquelle cela doit se produire. Les sauvegardes de la base de données doivent être automatisées et ne pas dépendre d’une interaction humaine. Vous en avez ainsi assez pour assurer un processus de récupération sécurisé et prévisible. Cela aide aussi dans toute activité médico-légale, si une telle activité est nécessaire, est réalisable et fiable. Il se peut que vous ayez besoin d’une recherche médico-légale après la détection d’un exploit, ou lorsque vous essayez de diagnostiquer une activité de fraude à la carte de crédit ou même lorsqu’une personne s’est jointe à votre site web. Il n’y a pas de limite à la manière dont vous utilisez ces sauvegardes, mais avoir une bonne cadence de sauvegardes est votre grâce d’enregistrement lorsque vous en avez réellement besoin.

Voici un exemple de politique de conservation des données :

* Toutes les huit heures. Les sauvegardes doivent être facilement accessibles.
* Sauvegardes quotidiennes des sept derniers jours et doivent être facilement accessibles. Une copie d’eux pourrait être un candidat pour être déplacé hors site.
* Les sauvegardes hebdomadaires des quatre dernières semaines envisagent de se déplacer hors site.
* les sauvegardes mensuelles des trois derniers mois ont été déplacées hors site.
* Les anciennes sauvegardes sont déplacées vers le stockage à long terme hors site.

## Infrastructure en tant que code

Cette méthodologie signifie que vous disposez d’outils et de code pour reconstruire des parties ou l’ensemble de l’infrastructure de votre projet. Cela peut être nécessaire lorsqu’un serveur rencontre des problèmes et doit être retiré de l’utilisation. Être en mesure d’apporter rapidement un nouveau serveur en ligne, de déployer le code, de créer toutes les configurations PHP, Nginx ou Apache, etc., signifie automatiquement moins de temps d’arrêt. Même les étapes bien documentées d’un runbook sont plus faciles à configurer, l’exécution des étapes prend beaucoup plus de temps. Considérez également l’erreur humaine qui peut se produire lorsque vous êtes stressé pour remettre en ligne un site qui ne répond pas.

## base de données Secondaire

L&#39;utilisation d&#39;une base de données secondaire peut s&#39;avérer utile pour plusieurs raisons. Voici quelques exemples :

* Réchauffer Secondaire en cas d’échec Principal du disque
* Autorisation des requêtes prêtes de l’application
* Autoriser mysqldump et autoriser les transactions normales sans verrouiller la base de données
* Permet d’accéder aux données d’une source de données externe sans réduire la capacité des sites web à traiter les informations à la demande du client.

La base de données secondaire peut être utilisée comme `warm standby`. Cela peut être utile lorsque vous envisagez de récupérer à partir d’une Principale erreur de base de données. La conversion de la base de données secondaire en Principale est plus complexe que la reconstruction et la restauration d’une base de données vers une instance Mysql nouvellement créée. Cela réduit le temps d’arrêt réel lors d’une opération de récupération.

Il est possible de dérouter certaines requêtes vers la base de données secondaire. Si cette méthode est utilisée, il est conseillé de créer la base de données secondaire en lecture seule. En permettant à l’application Adobe Commerce d’utiliser cette base de données secondaire pour les opérations de lecture, il est utile de prendre certaines des requêtes de lecture et de permettre à la base de données secondaire de répondre. Cependant, cette modification ne représente que 30 à 50 % de toutes les demandes, mais toute charge que vous pouvez retirer de la base de données Principale est une victoire.

## Création d’un plan de déploiement qui comprend une restauration

Chaque déploiement doit inclure un plan de restauration. Oui, chaque déploiement. Si vous le planifiez, vous n&#39;êtes jamais surpris et êtes prêt pour le mauvais événement. Parfois, les mises à jour de code les plus simples peuvent échouer de manière catastrophique pour une raison quelconque.

Considérez l’histoire vraie d’une équipe qui a validé une petite requête de tirage simple pour exécuter un changement de schéma dans la base de données. Alors que le déploiement passait de 1 minute, à 5, puis 10, et l&#39;équipe s&#39;inquiétait de plus en plus. Ce qu’ils n’ont pas vérifié et pris en compte jusqu’à présent était une incohérence de la base de données de production par rapport à la base de données intermédiaire. Il était courant de supprimer toutes les données client lors de l’actualisation de l’environnement d’évaluation avec une copie de production. Cela signifie que tous les tests et l’assurance qualité avant cela reflétaient le déploiement qui ne devrait prendre que quelques minutes. En réalité, ils avaient plus de 20 millions de clients et ce petit changement de schéma prenait un temps exceptionnel. Parce qu&#39;ils n&#39;avaient aucune idée du temps que cela allait prendre, ils étaient obligés d&#39;arrêter le processus mysql et de restaurer le déploiement.

La préparation d’un processus de restauration pour un déploiement ne prend que quelques minutes, car le processus global sera similaire. Toutefois, vous devez prendre le temps de documenter exactement la validation à laquelle vous réinitialiseriez l’HEAD du référentiel git. Vous devez documenter exactement l’instantané de la base de données à utiliser ou l’emplacement où trouver l’instantané actuel si celui-ci se trouve toujours au même endroit. ont défini des heures pendant lesquelles l’état du déploiement doit être discuté et lorsque les choses prennent automatiquement effet. Par exemple, si un déploiement prend plus de 15 minutes, demandez au chef de projet et aux autres intervenants si les choses doivent continuer. Toutefois, exécutez automatiquement le processus de restauration et informez toutes les parties prenantes si le processus prend 45 minutes, même si le chef de projet et l’architecte hésitent à le faire.

Assurez-vous que plusieurs personnes sont impliquées dans l’ensemble du processus et chaque phase. Le fait que les développeurs de niveau intermédiaire examinent le processus de déploiement, la procédure de restauration et l’emplacement des fichiers est un excellent moyen de les impliquer. Ils finiront par suivre les étapes, de sorte qu&#39;ils comprennent que l&#39;ensemble du processus est la clé du succès à long terme. Assurez-vous que tout le monde a les moyens d’annuler un déploiement. Donner ce poids à votre équipe est donner du pouvoir et de la récompense. Si un développeur débutant ressent vraiment que quelque chose manque, il doit se sentir obligé de prendre la parole et laisser sa prudence se faire entendre. Laissez l&#39;architecte et les chefs de projet confirmer ou atténuer leur peur. Il est important d’avoir une équipe forte qui s’intéresse au projet et qui garde un bilan des déploiements sans défauts.

## Vérifier l’accès à la gestion des noms de domaine, DMS, SSL, WAF

Étant donné que les noms de domaine expirent, les enregistrements DNS peuvent être modifiés accidentellement, les certificats SSL peuvent expirer, et bien plus encore ; vous assurer que vous avez la possibilité de vous connecter et de vérifier que la connectivité doit se produire souvent. En effectuant cette vérification simple chaque trimestre, vous êtes certain que vous savez exactement où se trouvent les choses, surtout en cas d&#39;urgence. Ne supposez pas que votre DNS soit géré dans votre bureau d’enregistrement uniquement pour savoir si vous l’avez géré dans Amazon. Ces enregistrements ne sont pas fréquemment utilisés. Il est donc très probable d’oublier où ils se trouvent. Ne faites pas confiance à la documentation écrite uniquement pour les noms d’utilisateur et les mots de passe. Connectez-vous à chacune d’elles et vérifiez que les configurations que vous recherchez y sont bien gérées. Trop souvent, les choses changent au moment de la gestion du chiffre d&#39;affaires ou de l&#39;acquisition de la société, et une seule personne sait ce qui s&#39;est passé, parce qu&#39;elle a fait la mise à jour. Ils ne savaient pas que vous utilisiez un mot partagé document indiquant l’emplacement, le nom d’utilisateur et le mot de passe. Trouvez un processus de vérification qui soit logique pour vous et votre organisation, mais le faire tous les trois à six mois est un bon point de départ.

{{$include /help/_includes/hosting-related-links.md}}
