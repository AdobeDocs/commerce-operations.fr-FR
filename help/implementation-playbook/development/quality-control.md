---
title: Contrôle de la qualité
description: Découvrez les processus de contrôle qualité d’Adobe Commerce liés aux projets d’implémentation.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Processus et outils de contrôle de la qualité

![Diagramme du processus de contrôle qualité](../../assets/playbooks/quality-control-diagram.svg)

Le processus de contrôle qualité dans le diagramme précédent peut être décrit brièvement comme suit.

<table>
<thead>
  <tr>
    <th>Processus de développement logiciel</th>
    <th>Processus CQ</th>
    <th>CQ</th>
    <th>Chef de file du Québec</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Développement</td>
    <td>Planification</td>
    <td></td>
    <td>Révision et contribution aux plans de test</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Créer des spécifications de test (cas de test/scénarios de test)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Préparation et acquisition de données de test</td>
  </tr>
  <tr>
    <td></td>
    <td>Analyse et conception des tests</td>
    <td>Révision et contribution aux plans de test</td>
    <td>Lancer la préparation, les spécifications</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Créer des spécifications de test (cas de test/scénarios de test)</td>
    <td>Rédiger ou réviser une stratégie de test pour le projet</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Préparation et acquisition de données de test</td>
    <td> Diriger, guider et suivre l'analyse, la conception</td>
  </tr>
  <tr>
    <td>Tests internes</td>
    <td>Test de mise en oeuvre et d’exécution</td>
    <td>Mise en oeuvre de tests, exécution et consignation des tests</td>
    <td>Surveillance de l’implémentation et de l’exécution des tests</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Vérifier les performances et analyser la sécurité : évaluez les résultats et les écarts par rapport aux résultats attendus.</td>
    <td>Assurer la traçabilité des tests sur la base des tests et suivre les bogues sur le système de suivi des bogues</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Publier les bogues sur le système de suivi des bogues (Jira/Redmine/Trello)</td>
    <td>Définir la priorité/planifier les tests pour s'aligner sur la planification du projet définie par le PM</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Retest (test de confirmation) après correction de bogues</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Évaluation et création de rapports</td>
    <td>Effectuer un test de rapport sur l’état d’avancement du prospect et du PM CQ</td>
    <td>Évaluation des résultats et de la progression des tests</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Rédigez des rapports de synthèse de test en fonction des informations collectées lors du test.</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Vérifier les commentaires des clients ou les demandes de modification (CR)</td>
    <td>Suivi</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Effectuez de nouveau les tests et les tests de régression après avoir modifié le code source.</td>
    <td>Contrôle</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Mise à jour des spécifications de test</td>
    <td></td>
  </tr>
  <tr>
    <td>Maintenance</td>
    <td>Maintenance</td>
    <td>Révision et contribution aux tâches</td>
    <td>Révision et estimation du temps pour les tâches</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Créer/mettre à jour des spécifications de test</td>
    <td>Progression du test de relance</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Exécution de tests pour ces tâches</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Test de régression</td>
    <td></td>
  </tr>
</tbody>
</table>

Semblable au [outils](project-management-tools.md) nous avons identifié pour le processus de développement, nous avons sélectionné une poignée de solutions et de plateformes de choix que nous utilisons souvent pour les tests de contrôle de la qualité.

| Objectif | Outil |
|---------------------------|---------------------------------------------------|
| Index de performance du site web | Google PageSpeed, Webpagetest, JMeter |
| Sécurité | Outil d’analyse de sécurité Adobe Commerce, SonarQube, ZAP |
| Système de gestion des problèmes | JIRA |
| Tests de l’interface utilisateur | Pixel parfait, BrowserStack |
| Test d’API | Postman, SoapUI |
| Tests d’automatisation | Selenium |


## Index de performance du site web

GooglePageSpeed indique les performances d’une page sur les appareils mobiles et de bureau et fournit des suggestions sur la manière d’améliorer cette page.

WebPageTest est un outil de performances Web qui utilise des navigateurs réels pour accéder aux pages Web et collecter des mesures de minutage.

JMeter est un projet Apache qui peut être utilisé comme outil de test de charge pour analyser et mesurer les performances de divers services, en se concentrant sur les applications web.

## Sécurité

SonarQube et ZAP ont été introduits dans le processus de développement, mais nous l’incluons également ici avec plus d’informations sur sa participation au processus de CQ.

SonarQube est également utilisé pour l’inspection continue de la qualité du code afin d’effectuer des révisions automatiques avec une analyse statique du code pour détecter des bogues, des odeurs de code et des vulnérabilités de sécurité.

OWASPZAP (Zed Attack Proxy) est destiné à être utilisé par les personnes qui découvrent la sécurité des applications, ainsi que par les testeurs de pénétration professionnels. Certaines des fonctionnalités intégrées incluent l’interception de serveurs proxy, d’outils de balayage web traditionnels et AJAX, de scanner automatisé, de scanner passif, de navigation forcée, de Fuzzier, de prise en charge de WebSocket, de langages de script et de prise en charge de Plug-in-Hack.

## Tests de l’interface utilisateur

Perfect Pixel permet aux développeurs et aux concepteurs de balises de placer une superposition d’image semi-transparente au-dessus du HTML développé et d’effectuer une comparaison parfaite en pixels entre eux.

BrowserStack est une plateforme de test web et mobile cloud qui permet aux développeurs de tester leurs sites web et leurs applications mobiles sur des navigateurs, des systèmes d’exploitation et des appareils mobiles réels à la demande.

## Test d’API

Postman est la plateforme de collaboration pour le développement d’API. Postman simplifie chaque étape de création d’une API et simplifie la collaboration afin que vous puissiez créer de meilleures API.

SoapUI est une application de test de service Web Open Source pour Simple Object Access Protocol (SOAP) et les transferts d’état de représentation (REST). Ses fonctionnalités couvrent l’inspection du service Web. appel, développement, simulation et moquerie; les tests fonctionnels; test de charge et de conformité.

## Tests d’automatisation

Selenium est composé de plusieurs composants (API client Selenium, Selenium WebDriver), chacun d’eux jouant un rôle spécifique dans le développement de l’automatisation de test des applications web.
