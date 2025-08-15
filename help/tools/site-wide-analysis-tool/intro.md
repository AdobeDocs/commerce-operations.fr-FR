---
title: '[!DNL Site-Wide Analysis Tool]'
description: Découvrez l’outil  [!DNL Site-Wide Analysis] , son utilisation, le processus d’installation et comment y accéder
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 5f39a2d8440225b3a2e463894e2bd866196fbac2
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>À compter du 23 avril 2024, le [!DNL Site-Wide Analysis Tool] sera mis hors service pour tous les clients sur site d’Adobe Commerce.

Ce guide présente une vue d’ensemble de la [!DNL Site-Wide Analysis Tool]. Il décrit les utilisations, des instructions détaillées pour l’installation et la manière d’accéder à l’outil.

## Qu’est-ce qu’[!DNL Site-Wide Analysis Tool] ?

Le [!DNL Site-Wide Analysis Tool] est un outil en libre-service proactif et un référentiel central qui inclut des informations détaillées sur le système et des recommandations pour assurer la sécurité et l’opérabilité de votre installation Adobe Commerce. Il fournit une surveillance des performances en temps réel 24h/24 et 7j/7, des rapports et des conseils pour identifier les problèmes potentiels et une meilleure visibilité sur la santé, la sécurité et les configurations des applications du site. Cela permet de réduire le temps de résolution et d’améliorer la stabilité et les performances du site.

![Tableau de bord de l’outil d’analyse à l’échelle du site](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Voir cette [vidéo d’introduction](https://www.youtube.com/watch?v=KW2R8ki_RG4) pour en savoir plus.

## Présentation de l’outil

- **Tableau de bord**
   - Affiche l’intégrité globale de votre système avec des notifications de problèmes détectés et des recommandations spécifiques par priorité.<br>
Il comprend également un graphique historique permettant de suivre l’évolution de l’intégrité de votre site web au fil du temps.
   - Affiche le **[!UICONTROL Security Center Widget]** qui vous permet d’accéder à :
      - [Conformité technique [!DNL Stack] de version avec  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=fr)
      - [Bulletin de sécurité Adobe](https://helpx.adobe.com/fr/security/security-bulletin.html)
      - [Recommandations de l’ [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=fr)
      - [[!DNL Site-Wide Analysis Tool] Recommandations relatives aux bonnes pratiques de sécurité](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=fr)

- **Informations** - Fournit des coordonnées du client et un résumé des tickets actuels, avec des informations détaillées sur chaque produit Adobe Commerce installé.

- **Recommandations** - Répertorie les recommandations basées sur les bonnes pratiques pour résoudre les problèmes détectés sur votre site :
   - Pour les modifications nécessitant une mise à jour de l’infrastructure, envoyez une demande d’assistance.
   - Pour les modifications nécessitant une mise à jour de l’application, effectuez les modifications vous-même.
   - Pour les modifications nécessitant une intervention manuelle, comme un [déploiement du code](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=fr#deployment-workflow), demandez de l’aide à votre administrateur système ou à vos développeurs.

- **Exceptions** - Répertorie les erreurs générées par l’application en raison de conditions anormales sans gestionnaire d’erreurs.

- **Extensions** - Répertorie toutes les extensions et bibliothèques tierces.

- **Correctifs** - Intégré au [!DNL Quality Patches Tool], il fournit une liste de tous les correctifs disponibles spécifiques à votre instance Adobe Commerce.

## Intégrations à d’autres outils d’assistance Adobe Commerce

Visualisez toutes les informations importantes concernant votre site en un seul endroit. [!DNL Site-Wide Analysis Tool] vous permet d’obtenir un accès direct aux informations et depuis les [!UICONTROL Security Center Widget], [!DNL Upgrade Compatability Tool] et [!DNL Managed Alerts].

- [**[!UICONTROL Security Center Widget]**] - Affiche des informations relatives à la sécurité de votre site.<br>
Les informations de sécurité affichées incluent [Conformité technique [!DNL Stack] version aux recommandations  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=fr), [Adobe Security Bulletin](https://helpx.adobe.com/fr/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=fr), and [[!DNL Site-Wide Analysis Tool]  bonnes pratiques en matière de sécurité](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=fr).<br>
Le [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=fr) fournit aux clients Adobe Commerce et Magento Open-Source des informations en temps réel sur l’état de sécurité de leur boutique en détectant de manière proactive les programmes malveillants et en les avertissant si leur boutique est compromise.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - Exécute l’instance personnalisée Adobe Commerce par rapport à la version de mise à niveau cible et renvoie un résumé des problèmes critiques, des erreurs et des avertissements qui doivent être résolus, ce qui facilite, accélère et réduit le processus d’analyse de la mise à niveau.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - Surveillez plusieurs mesures pour suivre de manière proactive les performances de la plateforme et fournissez des instructions spécifiques sur la résolution des problèmes afin que les commerçants puissent éviter les temps d’arrêt critiques et rester informés sur leur CPU, les performances de l’application, le disque, la mémoire et la base de données.

## À qui s&#39;adresse ce guide ?

Les commerçants et les partenaires qui souhaitent une plus grande visibilité sur leurs sites web Adobe Commerce. Il permet aux commerçants d&#39;améliorer l&#39;expérience de leurs clients et de mieux s&#39;aligner sur les recommandations de bonnes pratiques et les questions fondamentales.

## [!DNL Site-Wide Analysis Tool] de démonstration

Regardez cette vidéo pour en savoir plus sur le [!DNL Site-Wide Analysis Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
