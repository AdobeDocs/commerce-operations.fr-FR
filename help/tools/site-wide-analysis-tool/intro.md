---
title: '[!DNL Site-Wide Analysis Tool]'
description: Découvrez l’outil  [!DNL Site-Wide Analysis] , son utilisation, le processus d’installation et comment y accéder
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 62ca9093228d4d928d6c61c4c5dcf26e142c9fdb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>À compter du 23 avril 2024, le [!DNL Site-Wide Analysis Tool] sera mis hors service pour tous les clients sur site d’Adobe Commerce.

Ce guide présente une vue d’ensemble de la [!DNL Site-Wide Analysis Tool]. Il décrit les utilisations, des instructions détaillées pour l’installation et la manière d’accéder à l’outil.

## Quel est le [!DNL Site-Wide Analysis Tool] ?

Le [!DNL Site-Wide Analysis Tool] est un outil en libre-service proactif et un référentiel central qui inclut des informations détaillées sur le système et des recommandations pour assurer la sécurité et l’opérabilité de votre installation Adobe Commerce. Il fournit une surveillance des performances en temps réel 24h/24 et 7j/7, des rapports et des conseils pour identifier les problèmes potentiels et une meilleure visibilité sur la santé, la sécurité et les configurations des applications du site. Cela permet de réduire le temps de résolution et d’améliorer la stabilité et les performances du site.

>[!NOTE]
>
>Après l’application d’une recommandation, sa mise à jour dans le tableau de bord de l’outil d’analyse à l’échelle du site ou dans le rapport généré peut prendre quelques jours.
>
>Le [!DNL Site-Wide Analysis Tool] génère des rapports sur les données au niveau du système. Pour obtenir des rapports sur les données de produit, de vente, de marketing et d’autres données d’application commerciales d’Adobe Commerce, consultez [Rapports Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu).

![Tableau de bord de l’outil d’analyse à l’échelle du site](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Voir cette [vidéo d’introduction](https://www.youtube.com/watch?v=KW2R8ki_RG4) pour en savoir plus.

## Présentation de l’outil

- **Tableau de bord**
   - Affiche l’intégrité globale de votre système avec des notifications de problèmes détectés et des recommandations spécifiques par priorité.<br>
Il comprend également un graphique historique permettant de suivre l’évolution de l’intégrité de votre site web au fil du temps.
   - Affiche le **[!UICONTROL Security Center Widget]** qui fournit des liens vers les ressources suivantes :
      - [Conformité technique [!DNL Stack] de version avec  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
      - [Bulletin de sécurité Adobe](https://helpx.adobe.com/security/security-bulletin.html)
      - [Recommandations de l’ [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool] Recommandations relatives aux bonnes pratiques de sécurité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **Informations** - Fournit des coordonnées du client et un résumé des tickets actuels, avec des informations détaillées sur chaque produit Adobe Commerce installé.

- **Recommandations** - Fournit un [score d’index d’intégrité SWAT](#swat-health-index.md) pour effectuer le suivi de l’intégrité du site et répertorie les recommandations en fonction des bonnes pratiques pour résoudre les problèmes détectés sur votre site :
   - Pour les modifications nécessitant une mise à jour de l’infrastructure, envoyez une demande d’assistance.
   - Pour les modifications nécessitant une mise à jour de l’application, effectuez les modifications vous-même.
   - Pour les modifications nécessitant une intervention manuelle, comme un [déploiement du code](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), demandez de l’aide à votre administrateur système ou à vos développeurs.

- **Exceptions** - Répertorie les erreurs générées par l’application en raison de conditions anormales sans gestionnaire d’erreurs.

- **Extensions** - Répertorie toutes les extensions et bibliothèques tierces.

- **Correctifs** - Intégré au [!DNL Quality Patches Tool], il fournit une liste de tous les correctifs disponibles spécifiques à votre instance Adobe Commerce.

## Intégrations à d’autres outils d’assistance Adobe Commerce

Affichez des informations importantes sur votre site en un seul endroit. [!DNL Site-Wide Analysis Tool] vous permet d’obtenir un accès direct aux informations et depuis les [!UICONTROL Security Center Widget], [!DNL Upgrade Compatibility Tool] et [!DNL Managed Alerts].

- **[!UICONTROL Security Center Widget]** : affiche des informations relatives à la sécurité de votre site.<br>
Les informations de sécurité comprennent [Conformité technique [!DNL Stack] de version aux recommandations  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirement), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool]  bonnes pratiques de sécurité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations).

  Le [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) fournit aux clients Adobe Commerce et Magento Open-Source des informations en temps réel sur la position de sécurité de leur boutique en détectant de manière proactive les programmes malveillants et en les alertant si leur boutique est compromise.

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - Compare votre instance Adobe Commerce à la version mise à niveau et signale les problèmes critiques, les erreurs et les avertissements à corriger avant la mise à niveau. La résolution de ces problèmes simplifie le processus de mise à niveau. »

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** - Surveillez les mesures clés (CPU, performances des applications, disque, mémoire et intégrité de la base de données) et fournissez des étapes de dépannage claires pour aider les commerçants à anticiper les problèmes et à éviter les temps d’arrêt.

## À qui s&#39;adresse ce guide ?

Les commerçants et les partenaires qui souhaitent une plus grande visibilité sur leurs sites web Adobe Commerce. Il permet aux commerçants d’améliorer l’expérience de leurs clients et de mieux s’aligner sur les recommandations de bonnes pratiques et les questions fondamentales.

## [!DNL Site-Wide Analysis Tool] de démonstration

Regardez cette vidéo pour en savoir plus sur le [!DNL Site-Wide Analysis Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
