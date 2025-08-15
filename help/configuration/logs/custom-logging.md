---
title: Journalisation personnalisée
description: Découvrez comment rechercher des erreurs à l’aide de la journalisation personnalisée.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Présentation de la journalisation personnalisée

Les journaux offrent une visibilité sur les processus système ; par exemple, des informations de débogage qui vous aident à comprendre quand une erreur s’est produite ou ce qui a provoqué l’erreur.

Cette rubrique traite de la journalisation basée sur des fichiers, bien que Commerce offre la possibilité de stocker également les journaux dans la base de données.

Adobe recommande d’utiliser la journalisation centralisée des applications pour les raisons suivantes :

- Il permet de stocker les journaux sur un serveur autre que le serveur d’applications et réduit les opérations d’E/S de disque, simplifiant ainsi la prise en charge du serveur d’applications.

- Le traitement des données des journaux est ainsi plus efficace grâce à l’utilisation d’outils spéciaux, tels que [Logstash], [Logplex] ou [fluentd], sans impact sur le serveur de production.

  >[!INFO]
  >
  >Adobe ne recommande ni n’approuve aucune solution de journalisation particulière.

## Conformité au RSP-3

La norme [PSR-3][laminas] définit une interface PHP commune pour les bibliothèques de journalisation. L’objectif principal de PSR-3 est de permettre aux bibliothèques de recevoir un objet `Psr\Log\LoggerInterface` et d’y écrire des journaux de manière simple et universelle.

Cela permet de remplacer facilement l’implémentation sans craindre que ce remplacement n’enfreigne le code de l’application. Cela garantit également qu’un composant personnalisé fonctionnera même lorsque l’implémentation du journal sera modifiée dans une future version du système.

## Monologue

Commerce 2 est conforme à la norme PSR-3. Par défaut, Commerce utilise [Monologue]. Monologue implémenté en tant que préférence pour `Psr\Log\LoggerInterface` dans le [`di.xml`][di] d’application Commerce.

Monolog est une solution de journalisation PHP populaire avec un large éventail de gestionnaires qui vous permettent de créer des stratégies de journalisation avancées. Voici un résumé du fonctionnement de Monolog.

Un Monologue _logger_ est un canal qui a son propre ensemble de _gestionnaires_. Monolog comporte de nombreux gestionnaires, notamment :

- Consigner dans les fichiers et le journal système
- Envoyer des alertes et des e-mails
- Enregistrer les serveurs spécifiques et la journalisation en réseau
- Journalisation du développement (intégration à FireBug et Chrome Logger, entre autres)
- Connexion à la base de données

Chaque gestionnaire peut soit traiter le message d&#39;entrée et arrêter la propagation, soit transmettre le contrôle au gestionnaire suivant dans une chaîne.

Les messages de journal peuvent être traités de différentes manières. Par exemple, vous pouvez stocker toutes les informations de débogage dans un fichier sur le disque, placer les messages avec des niveaux de journal supérieurs dans une base de données et enfin envoyer des messages avec un niveau de journal « critique » par e-mail.

Les autres canaux peuvent avoir un ensemble différent de gestionnaires et de logiques.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluide]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monologue]: https://github.com/Seldaek/monolog
