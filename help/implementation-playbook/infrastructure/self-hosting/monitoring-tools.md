---
title: Outils de surveillance Adobe Commerce auto-hébergés
description: Découvrez les outils de surveillance d’auto-hébergement, les idées, les concepts et les bonnes pratiques à prendre en compte.
landing-page-description: Découvrez quelques concepts et éléments à prendre en compte concernant les outils de surveillance lors de l’hébergement d’Adobe Commerce vous-même.
short-description: Découvrez vous-même les stratégies et les concepts d’outils de surveillance pour héberger Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 728e9439-63d0-4481-b014-7ba2ce97b9d0
feature: Install, Logs, Observability
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# Outils et télémétrie de surveillance Adobe Commerce auto-hébergée

L’utilisation d’outils de surveillance permet de détecter les modifications sans avoir à payer quelqu’un pour tout regarder en permanence. Avec la plupart des outils, vous pouvez ajouter des alertes et des notifications si un seuil est atteint, par exemple un disque dur qui manque d’espace. Certains outils fournissent une sortie qui doit être suivie et calculée, comme les résultats du test de charge. Quel que soit l’outil, chaque outil a un rôle et, lorsqu’il est utilisé de manière cohérente, il peut vous aider à gérer votre application. Il existe des options gratuites pour tous les outils, mais n&#39;oubliez pas de payer pour un service, souvent, vous garantissez un support plus rapide et plus fiable et peut valoir la peine de l&#39;investissement. New Relic est un exemple d’outil offrant un niveau de gratuité et une version payante qui libère beaucoup plus de puissance et de capacités. Il existe d’autres types, tels que DataDog ou Dynatrace. Trouvez une bonne option et utilisez-la de manière cohérente.

## Surveillance des infrastructures

Dans ce contexte, le terme infrastructure est assez vague. Pour cette rubrique, cela signifie tout serveur, processus ou périphérique utilisé pour faire fonctionner le site. Par exemple :

* Disques durs
* Utilisation du processeur
* Utilisation de la RAM
* Redis
* Charge moyenne par serveur
* trafic réseau

Seuils de recherche pour créer des alertes efficaces. N’en affectez pas un pour les éléments importants tels que la capacité du disque dur. Configurez quelques groupes pour avertir différents lorsque les choses empirent. Par exemple, voici un ensemble de règles lorsqu’un disque dur est saturé.

* Notification de Slack à 70 % pour le canal DevOps
* 80 % Notifier le canal Op de développement de la salle des Slack et une liste de distribution des emails des coéquipiers DevOps
* 90 % Notifier le canal DevOps du Slack et le canal du Slack d’assistance à la production, le groupe de distribution Email DevOps et le responsable de l’ingénierie
* 95 % Notifier les opérations de développement de Slack et les canaux de Slack d’assistance à la production, liste de distribution des emails de tous les ingénieurs et Director d’ingénierie
* 98 % Notifier tous les canaux de Slack P1 et les opérations de développement et les canaux de Slack d’assistance à la production, la liste de distribution par e-mail des ingénieurs et le Director d’ingénierie et de VP de la technologie

Il existe de nombreuses façons d’avertir une équipe. Par conséquent, veillez à en choisir une fiable qui ne sera pas inondée de trop d’alertes. Il est important de réserver des alertes lorsque cela est important, faute de quoi vous risquez de devenir dépassé et de commencer à ignorer les alertes.

Il existe souvent de bons modèles à suivre pour la plupart des outils tels que New Relic, DataDog et Dynatrace. Prenez le temps de trouver les bonnes idées qui conviennent le mieux à votre application. Avec Adobe Commerce sur l’infrastructure cloud, des alertes et des triggers sont en place lorsque le projet est configuré. Cela permet à l’équipe d’assistance à la production d’Adobe d’appliquer ses outils pour la surveillance de la disponibilité et de la haute disponibilité.

Les tableaux de bord offrent un accès rapide aux aspects fréquents ou importants de votre site. Les éléments de tableau de bord peuvent être constitués de pages vues, de l’utilisation du processeur par hôte, de la liste de tous les serveurs, des temps de chargement des pages, des durées de transaction et même des résultats de tests de surveillance synthétiques au cours des derniers jours. Ces tableaux de bord doivent être créés pour permettre un triage rapide en cas de problème ou différents tableaux de bord configurés pour différentes expériences utilisateur. Avec un peu de chance, vous pouvez concevoir plusieurs tableaux de bord et profiter de la surveillance de votre application en temps réel. C&#39;est très satisfaisant, surtout quand le propriétaire du projet ou un responsable vous demande comment fonctionne le site, et vous pouvez trouver la réponse en quelques secondes, et non en quelques heures.

## Agrégation et rotation des logs

Les fichiers journaux se trouvent sur les serveurs d’applications qui traitent les demandes ou les journaux MySQL lorsque leur exécution prend trop de temps. Le problème avec les logs, c&#39;est qu&#39;ils sont séparés les uns des autres et qu&#39;ils trouvent tous, analyser les informations de chaque log peut être fastidieux. Il y a de nombreuses années, ce problème a été résolu à l’aide d’une technique appelée _agrégation des logs_. Cela permet de transférer les fichiers journaux de tous les emplacements de journaux vers un emplacement centralisé. Une fois que les sont déplacés, un logiciel peut les lire et fournir des moyens de rechercher, de filtrer et de consulter les informations. Ce processus peut être délicat à mettre en oeuvre. Il existe de nombreuses options, mais si vous avez de la chance, vos outils de surveillance peuvent lire et agréger vos fichiers journaux, tels que New Relic. En trouvant un bon outil, vous pouvez gagner un temps incalculable à l&#39;avenir. À moins qu’un seul serveur ne fasse tout ce qui est en son pouvoir pour que votre site fonctionne, l’agrégation des journaux est essentielle. Cela s’avère particulièrement utile lorsque vous essayez de déterminer si vous êtes confronté à une attaque DDoS ou que vous rencontrez un pic de trafic légitime, ou lorsque vous recherchez les raisons de l’échec d’une certaine requête.

Un autre élément clé pour les journaux est de s’assurer que la rotation se produit. Historiquement, cela se rapporte à `run-away logs` qui peut accidentellement remplir votre disque dur et provoquer l’arrêt du site. Une version de la rotation du journal peut se produire lorsqu’un fichier journal atteint une certaine taille, telle que 1 Go. Il existe des outils au niveau du serveur tels que `logrotate` qui peuvent les supprimer automatiquement. Par exemple, il peut supprimer les fichiers journaux trop volumineux une fois qu’ils sont supérieurs à 1 Go ou supprimer les fichiers journaux datant de plus de 90 jours. Vous définissez une stratégie de journal. Il est donc important de comprendre les limites de vos ressources.

## Analyses de programmes malveillants

De nombreuses sociétés qui hébergent des sites web dédiés à Adobe Commerce disposeraient d&#39;une bibliothèque d&#39;exploits et de maliciels connus. Ils doivent effectuer une analyse automatiquement ou sur demande. Là où ils sont efficaces, ils sont réactionnaires et ne fonctionnent que lorsque de nouveaux logiciels malveillants sont détectés. Il peut être judicieux d’avoir un outil proactif qui puisse examiner le code et la base de données pour détecter les logiciels malveillants connus. Certaines options sont disponibles, telles que [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Ils peuvent effectuer une analyse à distance depuis l’extérieur ou être installés et mettre à jour/analyser/surveiller de manière proactive après avoir été configurés sur les serveurs. Il peut s’agir d’une excellente option, car leur bibliothèque est constamment mise à jour, car elles sont installées et surveillent des milliers de sites si vous choisissez une solution fournie telle que Sansec. Lorsqu&#39;un nouveau logiciel malveillant est détecté, chaque projet qu&#39;ils surveillent bénéficie des informations et est désormais alerté s&#39;il est détecté.

Il y a quelques versions gratuites à considérer, mais pour les maliciels, vous devriez vraiment envisager une solution payante. Il peut s’agir d’une différence entre le fait que votre site a été infecté pendant quelques minutes et quelques mois. Avoir un exploit sur votre site provoque d&#39;énormes maux de tête, c&#39;est un domaine que vous devriez envisager de payer pour un service.

## Adobe de l’outil d’analyse à l’échelle du site

L’outil d’analyse à l’échelle du site est un outil en libre-service proactif et un référentiel central qui comprend des informations détaillées sur le système et des recommandations pour garantir la sécurité et la maniabilité de votre installation Adobe Commerce. Il fournit 24/7 surveillance des performances, rapports et conseils en temps réel afin d’identifier les problèmes potentiels et d’améliorer la visibilité sur l’intégrité, la sécurité et les configurations d’application du site. Cela permet de réduire le temps de résolution et d’améliorer la stabilité et les performances du site.

La page Recommendations de l’outil d’analyse à l’échelle du site répertorie les recommandations basées sur les bonnes pratiques pour résoudre les problèmes détectés sur votre site. Les recommandations sont triées par priorité PO vers P4, où PO est critique et P4 est faible. Les résultats incluent la description, la recommandation, l’impact du site, la cause racine, les scénarios/conditions préalables, le résultat attendu et les outils utilisés.

Découvrez les bonnes pratiques pour améliorer les performances de votre site. Suivez et implémentez les recommandations répertoriées par priorité.

Pour plus d’informations sur la façon d’installer ceci sur votre projet, consultez la page [Guide d’installation de l’outil d’analyse à l’échelle du site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Surveillance SSL

Le certificat SSL est l’un des éléments les plus oubliés pour un projet. Ils n&#39;ont besoin d&#39;attention qu&#39;une fois par an, donc les oublier est très facile. L’expiration de votre certificat de sécurité peut entraîner un avertissement ou un refus des navigateurs modernes d’afficher les pages de votre site. Les clients peuvent commencer à envoyer des e-mails ou à appeler l’assistance en cas de problème, et il se peut que vous ne puissiez pas agir jusqu’à ce qu’il soit résolu. Chaque minute compte, donc reconnaître l&#39;expiration se fait à l&#39;avance et s&#39;assurer que les choses sont renouvelées est essentiel pour maintenir le site opérationnel. Il existe de nombreuses façons d’effectuer la surveillance SSL. Envisagez d’utiliser des outils de surveillance de synthèse pour votre site, en utilisant des outils gratuits ou peu coûteux comme Pingdom, Keysest ou Sucuri, et abonnez-vous même à un service qui propose des alertes d’expiration de certificat SSL. Ces outils simples peuvent vous assurer que les certificats de votre site sont valides et réduire le risque de temps d’arrêt pour vos clients.

## Test automatisé

L’exécution de tests automatisés, tels que des tests fonctionnels ou des tests unitaires, permet souvent de détecter des problèmes liés au code nouvellement introduit. Ces tests peuvent ne pas tout capturer, car Adobe Commerce et les tests unitaires offrent généralement une couverture de moins de 50 %. Cela ne signifie pas que vous devriez éviter de les écrire et de les tester. Ces outils sont là pour ajouter une autre couche de sécurité que tout ce qui est validé n’affecte pas négativement l’usine et les tests personnalisés que votre équipe de développement crée. En exécutant ces tests sur chaque déploiement, tous les problèmes majeurs sont détectés tôt et évitent de permettre aux éléments de se frayer un chemin vers la production.

Les tests de charge peuvent s’avérer difficiles à obtenir. Une grande partie de la complexité vient de la manière dont le front-end est utilisé et mis en oeuvre. Si votre site dispose d’un front-end sans interface utilisateur graphique, vous pouvez charger les API GraphQL et REST. C’est à vous et à l’équipe des opérations de développement de décider de terminer le test de chargement. Sachez que chaque test de charge, effectué dès que possible, fournit des informations sur l’état du projet. Il fournit également des points de référence pour les futurs tests afin de déterminer s’il existe des changements radicaux dans les résultats du test de charge. Si tel est le cas, et s’ils sont négatifs, c’est l’occasion de passer en revue les dernières modifications du code et de rechercher les performances ayant un impact sur les sections à améliorer.

Adobe Commerce dispose de bons conseils pour vous aider à comprendre comment exécuter des tests unitaires. Voir [test unitaire PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} dans le _Guide de test d’application_ sur le site de documentation Adobe Developer.

Pour plus d’informations sur les tests fonctionnels, consultez [Présentation de la structure de tests fonctionnels](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
