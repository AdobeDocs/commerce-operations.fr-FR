---
title: Managed Services
description: Examinez les responsabilités d’Adobe Managed Services, des clients et des fournisseurs de services cloud pour votre implémentation d’infrastructure cloud Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Services gérés

Adobe Commerce sur les services gérés de l’infrastructure cloud est sécurisé par défaut.

![Diagramme présentant les services gérés Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilité partagée

Les plans d’Adobe Commerce Pro reposent sur un modèle de sécurité de la responsabilité partagée. Dans ce modèle, les différentes parties ont des responsabilités différentes pour maintenir la sécurité du système. Cette approche offre à la fois une certaine flexibilité et l’utilisation des meilleures technologies cloud de marque.

![Diagramme montrant le modèle de responsabilité partagée Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilités des services gérés par l’Adobe

Adobe Managed Services est responsable de la sécurité et de la disponibilité de l’environnement cloud Adobe Commerce Pro, du code de l’application principale Adobe Commerce Pro et des systèmes de commerce interne. Cela inclut, sans s’y limiter :

- Application de correctifs au niveau du serveur
- Exploitation des services nécessaires pour la diffusion des forfaits Adobe Commerce Pro
- Test de vulnérabilité
- Journalisation et surveillance des événements de sécurité
- Gestion des incidents
- Surveillance opérationnelle
- Prise en charge 24/7
- Assurer que l’infrastructure client est disponible conformément aux contrats de niveau de service

Adobe Managed Services est également responsable de la gestion des configurations de pare-feu de serveur (iptables) et des configurations de pare-feu de périmètre (groupes de sécurité). Adobe peut également publier des mises à jour de sécurité de l’application principale de manière périodique. Il est de la responsabilité des clients d&#39;appliquer ces correctifs. Ces zones sont toutes couvertes par la certification PCI d’Adobe Commerce sur le système d’infrastructure cloud.

### Responsabilités AWS

Adobe Managed Services utilise Amazon Web Services (AWS) pour l’infrastructure de serveur cloud. AWS est responsable de la sécurité du réseau, notamment le routage, le changement et la sécurité du réseau de périmètre par le biais de systèmes de pare-feu et de systèmes de détection d’intrusion (IDS). AWS est responsable de la sécurité physique des centres de données qui gèrent les environnements cloud d’Adobe Commerce, ainsi que de la sécurité environnementale pour garantir la mise en place de contrôles adéquats en matière d’alimentation, de refroidissement et de mécanisme.

Adobe Commerce Pro prévoit d’utiliser :

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Cloud privé virtuel Amazon (VPC)
- Equilibrage de charge adaptatif Amazon (ELB)
- Amazon Cloud Trail Services.

Amazon dispose d’un programme de conformité étendu, qui comprend des certifications PCI DSS, SOC 2 et ISO 27001.

### Responsabilités du partenaire/client de la solution

Le client est principalement responsable de la sécurité de sa mise en oeuvre personnalisée de l’application Adobe Commerce s’exécutant dans l’environnement cloud de planification Adobe Commerce Pro. Cela inclut :

- Assurer une configuration et un codage sécurisés des activités de surveillance de l’application et de la sécurité, y compris des tests de pénétration et des analyses régulières des vulnérabilités.

- La sécurité de toute personnalisation, extension, autre application ou intégration utilisée dans leur système.

- La sécurité de leurs utilisateurs et l&#39;accès à leur configuration et à leur application.

- Le client contrôle tous les déploiements de code vers ses environnements hors production. Ce contrôle s’accompagne également de la responsabilité d’appliquer des correctifs de sécurité d’application à l’application principale Adobe Commerce, aux extensions ou à tout code personnalisé.

- Le client doit effectuer des tests de pénétration de son application personnalisée. Ces responsabilités peuvent être gérées par des ressources techniques fournies par le client, les partenaires d’implémentation ou les services professionnels d’Adobe Commerce.

- Les clients sont responsables des exigences PCI de leur application personnalisée et de leurs propres processus. La conformité PCI du client s’appuie sur les certifications PCI d’AWS et d’Adobe Commerce afin de minimiser les domaines à examiner.
