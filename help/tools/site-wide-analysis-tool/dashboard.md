---
title: '[!DNL Dashboard]'
description: Découvrez l’onglet  [!DNL Dashboard] dans les éléments  [!DNL Site-Wide Analysis Tool], le moment d’utilisation, les avantages et les bonnes pratiques.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La page [!UICONTROL Dashboard] présente en un coup d’oeil [!DNL widgets] qui fournit une &quot;seule vitre&quot; de l’état d’intégrité et de l’état actuel de votre site web Adobe Commerce. Chaque [!DNL widget] contient un lien d’accès à la page de chaque fonctionnalité, à chaque outil lui-même ou aux rapports (selon le [!DNL widget]).
Il existe également une liste de [!UICONTROL External Resources] liens pour Adobe Commerce, y compris la [base de connaissances du centre d’aide Adobe Commerce (centre d’aide)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), la [documentation du développeur Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool] : recherchez des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, le [centre de sécurité](https://helpx.adobe.com/security.html) et l’ [observation pour Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html)}}.

## Éléments

* **[!UICONTROL Recommendations]** : affiche les recommandations de bonnes pratiques pour votre site. Recommendations (problèmes détectés et recommandations à corriger) sont triés par priorité : P0 (Critique) à P4 (Notification).
Recommendations comprend la description, la recommandation, l’impact du site, la cause racine, les scénarios/conditions préalables et les outils utilisés.

* **[!UICONTROL Upgrade Compatibility Tool]** : vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce. Il identifie également les problèmes potentiels qui doivent être résolus dans votre code avant de tenter une mise à niveau vers une version plus récente d’Adobe Commerce.
[!UICONTROL Upgrade Compatibility Tool] vous permet d’identifier le moment où des modifications de code principal ont été apportées à des fonctionnalités personnalisées.

* **[!UICONTROL Security Center Widget]** : affiche des informations de sécurité pour votre site.
Les informations de sécurité affichées comprennent la [conformité de la version à la  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] meilleure pratique de la sécurité Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html). [!DNL Stack] <br>
Le [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) surveille les sites Adobe Commerce pour les risques de sécurité. Il peut détecter de manière proactive et efficace les logiciels malveillants dans les magasins marchands et avertir les marchands s’il existe des risques de sécurité, des logiciels malveillants ou des menaces, et peut identifier les correctifs et mises à jour Adobe Commerce manquants.

* **[!UICONTROL Extensions]** : affiche les extensions actuellement installées sur votre instance Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) des informations sont fournies, le cas échéant, pour les extensions répertoriées ici.

* **[!UICONTROL Alerts]** : affiche le dernier [!DNL New Relic Managed Alerts] pour l’instance Adobe Commerce. En savoir plus sur [les alertes gérées pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) et sur la façon d’ [accéder aux services New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) dans la base de connaissances du support Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]** : affiche le logiciel non recommandé actuellement utilisé par votre instance Adobe Commerce, en fonction de votre version d’Adobe Commerce. Les logiciels non recommandés sont répertoriés par [!UICONTROL Name], [!UICONTROL Installed Version] et [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]** : affiche une liste courte de tous les correctifs recommandés en fonction des deux correctifs que vous avez peut-être déjà installés et de votre version d’Adobe Commerce. La liste complète des correctifs recommandés se trouve dans l’onglet de la fonctionnalité **[!UICONTROL Patches]**, qui se trouve également dans [!DNL Site-Wide Analysis Tool]. Les correctifs sont fournis par [[!DNL Quality Patches Tool] : recherchez des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Tous les correctifs répertoriés sont compatibles avec votre instance Adobe Commerce actuelle.
S&#39;il n&#39;existe aucun correctif recommandé à afficher pour votre instance Adobe Commerce, cet [!DNL widget] s&#39;affichera, **[!UICONTROL No Recommended Patches]**.

## Quand utiliser

La page **[!UICONTROL Dashboard]** est votre centre de commande en un coup d’oeil dans le [!DNL Site-Wide Analysis Tool] pour afficher non seulement facilement la &quot;vue d’ensemble&quot; de l’intégrité de votre site, mais vous pouvez également afficher et accéder à des outils, des recommandations et des rapports spécifiques pour votre site web Adobe Commerce par le biais de chaque [!DNL widget].

## Avantages

* Les [!DNL widgets] pour [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] et [!UICONTROL Security Scan] utilisent tous des graphiques circulaires interactifs codés par des couleurs faciles à lire avec des légendes de graphique sur le côté et comptabilisent les totaux au centre pour indiquer le nombre d’éléments [!UICONTROL Recommendations], [!UICONTROL Extensions] et [!UICONTROL Security Scan Tool] de chaque fonctionnalité. Les graphiques [!UICONTROL Recommendations] et [!UICONTROL Security Scan Tool] sont séparés par la gravité. [!UICONTROL Extensions] sont séparés en quatre classifications : version actuelle, ancienne version, désactivée et inconnue.

* [!DNL New Relic Alerts] sont répertoriés avec l’alerte la plus récente en haut, y compris une brève description et la durée depuis laquelle l’alerte s’est produite.

* Les [!UICONTROL Recommendations] et [!UICONTROL Extensions] [!DNL widgets] ont accès à la page complète des données de chaque fonctionnalité en cliquant sur **[!UICONTROL View All]**.

* [!UICONTROL Security Scan Tool] comporte un lien **[!UICONTROL View Report]** dans la fenêtre [!DNL widget] qui vous permet d’accéder à la page [!UICONTROL Recommendations].

* [!DNL Upgrade Compatibility Tool] comporte un bouton **[!UICONTROL Run Upgrade Scan]** dans la fenêtre [!DNL widget].

## Bonnes pratiques pour l’utilisation de [!UICONTROL Dashboard]

* Cliquez sur chaque [!DNL widget] pour accéder aux données détaillées qu’il fournit afin de mieux comprendre la sécurité, l’intégrité, les recommandations et les bonnes pratiques de votre site web pour l’améliorer.

* Accédez à [!UICONTROL Security Scan Tool] [!DNL widget] et cliquez sur [!UICONTROL View Report] pour afficher un rapport [!UICONTROL Recommendations] pour votre site.

* Utilisez les liens [!DNL External Resources] pour en savoir plus, rester à jour sur les correctifs de sécurité, les mises à jour et les bonnes pratiques, ou tirer parti des informations de la [base de connaissances du centre d’aide Adobe Commerce (centre d’aide)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), de la [documentation du développeur Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), de la [[!DNL Quality Patches Tool] : rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, du [centre de sécurité](https://helpx.adobe.com/security.html)}} et de [ ](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) Observation pour Adobe Commerce (OAC).
