---
title: '[!DNL Dashboard]'
description: En savoir plus sur les [!DNL Dashboard] dans le [!DNL Site-Wide Analysis Tool], les éléments, le moment d’utilisation, les avantages et les bonnes pratiques.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La variable [!UICONTROL Dashboard] affichage en un coup d’oeil de la page [!DNL widgets] qui fournissent un &quot;volet unique de vue en verre&quot; de l’état actuel et de l’intégrité de votre site web Adobe Commerce. Chaque [!DNL widget] contient un lien d’accès à la page de chaque fonctionnalité, à chaque outil lui-même ou aux rapports (en fonction de la variable [!DNL widget]).
Une liste de [!UICONTROL External Resources] les liens pour Adobe Commerce, y compris la variable [Base de connaissances de l’assistance d’Adobe Commerce (centre d’aide)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentation du développeur Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centre de sécurité](https://helpx.adobe.com/security.html), et [Observation pour Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Éléments

* **[!UICONTROL Recommendations]**: affiche les recommandations de bonnes pratiques pour votre site. Recommendations (problèmes détectés et recommandations à corriger) sont triés par priorité : P0 (Critique) à P4 (Notification).
Recommendations comprend la description, la recommandation, l’impact du site, la cause racine, les scénarios/conditions préalables et les outils utilisés.

* **[!UICONTROL Upgrade Compatibility Tool]**: vérifie une instance personnalisée Adobe Commerce par rapport à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce. Il identifie également les problèmes potentiels qui doivent être résolus dans votre code avant de tenter une mise à niveau vers une version plus récente d’Adobe Commerce.
La variable [!UICONTROL Upgrade Compatibility Tool] vous permet d’identifier le moment où des modifications de code principal ont été apportées à des fonctionnalités personnalisées.

* **[!UICONTROL Security Center Widget]**: affiche des informations de sécurité pour votre site.
Les informations de sécurité affichées sont les suivantes : [Tech [!DNL Stack] Conformité aux versions avec [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Recommendations de sécurité des bonnes pratiques](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
La variable [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) analyse les risques de sécurité sur les sites Adobe Commerce. Il peut détecter de manière proactive et efficace les logiciels malveillants dans les magasins marchands et avertir les marchands s’il existe des risques de sécurité, des logiciels malveillants ou des menaces, et peut identifier les correctifs et mises à jour Adobe Commerce manquants.

* **[!UICONTROL Extensions]**: affiche les extensions actuellement installées sur votre instance Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) des informations sont fournies, le cas échéant, pour les extensions répertoriées ici.

* **[!UICONTROL Alerts]**: affiche la dernière version [!DNL New Relic Managed Alerts] pour l’instance Adobe Commerce. En savoir plus sur [Alertes gérées pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) et comment [Accès aux services New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) dans la base de connaissances de prise en charge d’Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: affiche le logiciel non recommandé actuellement utilisé par votre instance Adobe Commerce, en fonction de votre version d’Adobe Commerce. Le logiciel non recommandé est répertorié par [!UICONTROL Name], [!UICONTROL Installed Version], et [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: affiche une liste courte de tous les correctifs recommandés en fonction des deux correctifs que vous avez peut-être déjà installés et de votre version d’Adobe Commerce. La liste complète des correctifs recommandés se trouve sur la page **[!UICONTROL Patches]** de l’onglet Fonctionnalités, qui se trouve également dans la variable [!DNL Site-Wide Analysis Tool]. Les correctifs sont fournis par le [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Tous les correctifs répertoriés sont compatibles avec votre instance Adobe Commerce actuelle.
Si aucun correctif recommandé n’est à afficher pour votre instance Adobe Commerce, procédez comme suit : [!DNL widget] s’affiche, **[!UICONTROL No Recommended Patches]**.

## Quand utiliser

La variable **[!UICONTROL Dashboard]** est votre centre de commande en un coup d’oeil dans la fonction [!DNL Site-Wide Analysis Tool] pour afficher facilement la &quot;vue d’ensemble&quot; de l’état de santé de votre site dans son ensemble, mais vous pouvez également afficher et accéder à des outils, des recommandations et des rapports spécifiques pour votre site web Adobe Commerce à l’aide de chaque [!DNL widget].

## Avantages

* La variable [!DNL widgets] pour [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], et [!UICONTROL Security Scan] tous utilisent des graphiques circulaires interactifs codés par des couleurs faciles à lire avec des légendes de graphiques sur le côté et comptabilisent les totaux au centre pour indiquer le nombre [!UICONTROL Recommendations], [!UICONTROL Extensions], et [!UICONTROL Security Scan Tool] éléments de chaque fonctionnalité. [!UICONTROL Recommendations] et [!UICONTROL Security Scan Tool] les graphiques sont séparés par leur gravité. [!UICONTROL Extensions] sont séparées en quatre classifications : version actuelle, ancienne version, désactivée et inconnue.

* [!DNL New Relic Alerts] sont répertoriées avec la dernière alerte en haut, y compris une brève description et la durée depuis laquelle l’alerte a été effectuée.

* La variable [!UICONTROL Recommendations] et [!UICONTROL Extensions] [!DNL widgets] ont accès à la page complète des données de chaque fonctionnalité en cliquant sur **[!UICONTROL View All]**.

* La variable [!UICONTROL Security Scan Tool] a une **[!UICONTROL View Report]** dans le [!DNL widget] qui permet d’accéder à la [!UICONTROL Recommendations] page.

* La variable [!DNL Upgrade Compatibility Tool] a une **[!UICONTROL Run Upgrade Scan]** dans le [!DNL widget] fenêtre.

## Bonnes pratiques relatives à l’utilisation de [!UICONTROL Dashboard]

* Cliquez sur chaque [!DNL widget] accéder aux données détaillées qu’il fournit pour mieux comprendre la sécurité, l’intégrité, les recommandations et les bonnes pratiques de votre site web afin de l’améliorer.

* Accédez au [!UICONTROL Security Scan Tool] [!DNL widget] et cliquez sur [!UICONTROL View Report] pour afficher un [!UICONTROL Recommendations] rapport pour votre site.

* Utilisez la variable [!DNL External Resources] des liens permettant d’en savoir plus, de se tenir à jour sur les correctifs de sécurité, les mises à jour et les bonnes pratiques, ou de tirer parti des informations de la variable [Base de connaissances de l’assistance d’Adobe Commerce (centre d’aide)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentation du développeur Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centre de sécurité](https://helpx.adobe.com/security.html), et [Observation pour Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
