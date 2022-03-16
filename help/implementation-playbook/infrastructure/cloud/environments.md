---
title: Environnements de l’infrastructure cloud
description: Utilisez les environnements appropriés pour les cas d’utilisation appropriés.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Environnements

L’architecture d’Adobe Commerce sur l’infrastructure cloud Pro prend en charge les environnements que vous pouvez utiliser pour développer, tester et lancer votre boutique. Chaque environnement contient une base de données et un serveur web. Les quatre environnements utilisés par Adobe Commerce sont les suivants :

- **Intégration**: fournit une branche d’environnement unique et vous pouvez créer jusqu’à quatre branches d’environnement supplémentaires. Cela permet de déployer au maximum cinq branches principales vers des conteneurs Platform as a Service (PaaS).

- **Évaluation**: fournit une branche d’environnement unique déployée sur des conteneurs IaaS dédiés.

- **Production**: fournit une branche d’environnement unique déployée sur des conteneurs IaaS dédiés.

- **Principal mondial**: fournit une branche principale déployée sur les conteneurs Platform as a Service (PaaS).

![Diagramme montrant la relation entre les environnements cloud Adobe Commerce](../../../assets/playbooks/environment-diagram.svg)

## Branches Git

L’environnement d’intégration fournit une branche d’intégration de base unique contenant votre code Adobe Commerce déployé sur des conteneurs Platform as a Service (PaaS).

Adobe Commerce sur les environnements d’infrastructure cloud prend en charge un processus d’intégration flexible et continu. Commencez par cloner la branche d’intégration dans votre dossier de projet local. Créez une ou plusieurs branches afin de développer de nouvelles fonctionnalités, de configurer des modifications et d’ajouter des extensions. Avec une branche de code développée et les fichiers de configuration correspondants, vos modifications de code sont prêtes à être fusionnées dans la branche d’intégration pour des tests plus complets.

![Diagramme présentant la stratégie d’embranchement basée sur Git pour les environnements cloud Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
