---
title: '[!DNL Dashboard]'
description: Découvrez l’onglet  [!DNL Dashboard]  dans les éléments  [!DNL Site-Wide Analysis Tool], quand l’utiliser, les avantages et les bonnes pratiques.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La page [!UICONTROL Dashboard] affiche d’un coup d’œil les [!DNL widgets] qui fournissent un « panneau unique » de l’intégrité et de l’état actuel de votre site web Adobe Commerce. Chaque [!DNL widget] contient un lien d’accès à la page de chaque fonctionnalité, à chaque outil lui-même ou aux rapports (selon le [!DNL widget]).
Il existe également une liste de liens [!UICONTROL External Resources] pour Adobe Commerce, y compris la [base de connaissances de l’assistance du centre d’aide d’Adobe Commerce (centre d’aide)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) [documentation pour les développeurs d’Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool] : rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [centre de sécurité](https://helpx.adobe.com/security.html) et [observation pour Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Éléments

* **[!UICONTROL Recommendations]** : affiche les recommandations de bonnes pratiques pour votre site. Les recommandations (problèmes détectés et recommandations à corriger) sont triées par priorité (P0 (critique) à P4 (notification)).
Les recommandations incluent la description, la recommandation, l’impact sur le site, la cause première, les scénarios/conditions préalables et les outils utilisés.

* **[!UICONTROL Upgrade Compatibility Tool]** : compare une instance personnalisée Adobe Commerce à une version spécifique en analysant tous les modules et le code principal qui y sont installés. Elle renvoie une liste des problèmes, erreurs et avertissements critiques qui doivent être résolus avant la mise à niveau vers la dernière version d’Adobe Commerce. Il identifie également les problèmes potentiels qui doivent être corrigés dans votre code avant d’essayer d’effectuer une mise à niveau vers une version plus récente d’Adobe Commerce.
Le [!UICONTROL Upgrade Compatibility Tool] vous permet d’identifier les modifications de code de base qui ont été apportées aux fonctionnalités personnalisées.

* **[!UICONTROL Security Center Widget]** : affiche des informations relatives à la sécurité de votre site.
Les informations de sécurité affichées incluent [Conformité technique [!DNL Stack] version aux recommandations  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool]  bonnes pratiques en matière de sécurité](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
Le [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) surveille les sites Adobe Commerce en termes de risques de sécurité. Il peut détecter de manière proactive et efficace les programmes malveillants sur les boutiques marchandes et informer les commerçants de tout risque de sécurité, programme malveillant ou menace, et peut identifier les correctifs et mises à jour d&#39;Adobe Commerce manquants.

* **[!UICONTROL Extensions]** : affiche les extensions actuellement installées sur votre instance Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) des informations sont fournies, le cas échéant, pour les extensions qui y sont répertoriées.

* **[!UICONTROL Alerts]** : affiche la dernière [!DNL New Relic Managed Alerts] de l’instance Adobe Commerce. Pour en savoir plus sur les [alertes gérées pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) et sur l’[accès aux services New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html), consultez la base de connaissances de l’assistance Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]** : affiche le logiciel non recommandé actuellement utilisé par votre instance Adobe Commerce, en fonction de votre version d’Adobe Commerce. Les logiciels non recommandés sont répertoriés par [!UICONTROL Name], [!UICONTROL Installed Version] et [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]** : affiche une courte liste des correctifs recommandés en fonction des correctifs que vous avez peut-être déjà installés et de votre version d’Adobe Commerce. La liste complète des correctifs recommandés se trouve dans l&#39;onglet Fonctionnalité **[!UICONTROL Patches]**, qui se trouve également dans le [!DNL Site-Wide Analysis Tool]. Les correctifs sont fournis par le [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Tous les correctifs répertoriés sont compatibles avec votre instance Adobe Commerce actuelle.
S’il n’existe aucun correctif recommandé à afficher pour votre instance Adobe Commerce, ce [!DNL widget] s’affiche, **[!UICONTROL No Recommended Patches]**.

## Quand l’utiliser

La page **[!UICONTROL Dashboard]** est votre centre de commande d’un coup d’œil dans le [!DNL Site-Wide Analysis Tool]. Elle permet non seulement d’afficher facilement la « vue d’ensemble » de l’intégrité de votre site dans son ensemble, mais également d’afficher des outils, des recommandations et des rapports spécifiques pour votre site web Adobe Commerce et d’y accéder à chaque [!DNL widget].

## Avantages

* Les [!DNL widgets] de [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] et [!UICONTROL Security Scan] utilisent toutes des graphiques circulaires interactifs à code couleur faciles à lire, avec des légendes de graphique sur le côté et des totaux au centre pour indiquer le nombre d’éléments [!UICONTROL Recommendations], [!UICONTROL Extensions] et [!UICONTROL Security Scan Tool] dont dispose chaque fonctionnalité. Les graphiques [!UICONTROL Recommendations] et [!UICONTROL Security Scan Tool] sont séparés par gravité. [!UICONTROL Extensions] sont séparées en quatre classifications : version actuelle, ancienne version, désactivée et inconnue.

* Les [!DNL New Relic Alerts] sont répertoriées avec l’alerte la plus récente en haut de la page, y compris une brève description et la durée de l’alerte.

* Les [!UICONTROL Recommendations] [!UICONTROL Extensions] et [!DNL widgets] ont accès à la page complète de données de chaque fonctionnalité en cliquant sur **[!UICONTROL View All]**.

* La [!UICONTROL Security Scan Tool] comporte un lien **[!UICONTROL View Report]** dans la fenêtre [!DNL widget] qui vous mène à la page [!UICONTROL Recommendations].

* La [!DNL Upgrade Compatibility Tool] comporte un bouton **[!UICONTROL Run Upgrade Scan]** dans la fenêtre de [!DNL widget].

## Bonnes pratiques relatives à l’utilisation de l’[!UICONTROL Dashboard]

* Cliquez sur chaque [!DNL widget] pour accéder aux données détaillées qu’il fournit afin d’insight et de comprendre la sécurité, l’intégrité, les recommandations et les bonnes pratiques de votre site web pour l’améliorer.

* Accédez à la [!UICONTROL Security Scan Tool] [!DNL widget] et cliquez sur [!UICONTROL View Report] pour afficher un rapport de [!UICONTROL Recommendations] pour votre site.

* Utilisez les liens [!DNL External Resources] pour obtenir plus d’informations, vous tenir au courant des correctifs de sécurité, des mises à jour et des bonnes pratiques ou tirer parti d’insight de la [base de connaissances de l’assistance du centre d’aide d’Adobe Commerce (centre d’aide)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), de la [documentation Adobe Commerce destinée aux développeurs (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool] : rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [centre de sécurité](https://helpx.adobe.com/security.html) et [observation pour Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
