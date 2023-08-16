---
title: Journalisation personnalisée
description: Découvrez comment enquêter sur les erreurs à l’aide de la journalisation personnalisée.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Présentation de la journalisation personnalisée

Les journaux offrent une visibilité sur les processus système, par exemple les informations de débogage qui vous aident à comprendre quand une erreur s’est produite ou ce qui a conduit à l’erreur.

Cette rubrique porte sur la journalisation basée sur les fichiers, bien que Commerce offre la possibilité de stocker également les journaux dans la base de données.

Adobe recommande d’utiliser la journalisation centralisée des applications pour les raisons suivantes :

- Il permet le stockage des journaux sur un serveur autre que le serveur d’applications et réduit les opérations d’E/S de disque, ce qui simplifie la prise en charge du serveur d’applications.

- Cela rend le traitement des données de journaux plus efficace à l’aide d’outils spéciaux, tels que [Logstash], [Logplex], ou [fluentd]: sans impact sur un serveur de production.

  >[!INFO]
  >
  >Adobe ne recommande ni n’approuve aucune solution de journalisation particulière.

## Conformité PSR-3

La variable [PSR-3 standard][laminas] définit une interface PHP courante pour les bibliothèques de journalisation. L’objectif principal de PSR-3 est de permettre aux bibliothèques de recevoir une `Psr\Log\LoggerInterface` et écrivez-y des journaux d’une manière simple et universelle.

Cela permet à l’implémentation d’être facilement remplacée sans craindre qu’un tel remplacement puisse endommager le code de l’application. Il garantit également qu’un composant personnalisé fonctionnera même si l’implémentation du journal est modifiée dans une version ultérieure du système.

## Monolog

Commerce 2 est conforme à la norme PSR-3. Par défaut, Commerce utilise [Monolog]. Monolog mis en oeuvre comme préférence pour `Psr\Log\LoggerInterface` dans l’application Commerce [`di.xml`][di].

Monolog est une solution de journalisation PHP courante qui propose un large éventail de gestionnaires et vous permet de créer des stratégies de journalisation avancées. Voici un résumé du fonctionnement de Monolog.

Un monolog _logger_ est un canal qui possède son propre jeu de _gestionnaires_. Monolog comporte de nombreux gestionnaires, notamment :

- Connexion aux fichiers et au fichier syslog
- Envoyer des alertes et des emails
- Journalisation de serveurs spécifiques et connexion en réseau
- Connexion au développement (intégration avec FireBug et Chrome Logger, entre autres)
- Connexion à la base de données

Chaque gestionnaire peut soit traiter le message d’entrée et arrêter la propagation, soit transmettre le contrôle au gestionnaire suivant dans une chaîne.

Les messages du journal peuvent être traités de différentes manières. Par exemple, vous pouvez stocker toutes les informations de débogage dans un fichier sur le disque, placer les messages avec des niveaux de journal supérieurs dans une base de données et enfin envoyer les messages avec le niveau de journal &quot;critique&quot; par e-mail.

D’autres canaux peuvent avoir un ensemble différent de gestionnaires et de logiques.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluentd]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monolog]: https://github.com/Seldaek/monolog
