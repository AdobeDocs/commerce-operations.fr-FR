---
title: '"Intégrez la variable [!DNL Site-Wide Analysis Tool]"'
description: Procédez comme suit pour récupérer la variable [!DNL Upgrade Compatibility Tool] du rapport [!DNL Site-Wide Analysis Tool] tableau de bord de votre projet Adobe Commerce.
source-git-commit: 1fc12289125a5954243e177a0c21505234eb2e81
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Intégrez la variable [!DNL Site-Wide Analysis Tool]

Le [!DNL Site-Wide Analysis Tool] fournit 24/7 surveillance des performances, rapports et recommandations en temps réel afin d’assurer la sécurité et la maniabilité des instances Adobe Commerce.

Le [!DNL Upgrade Compatibility Tool] est désormais intégré à la fonction [!DNL Site-Wide Analysis Tool] afin que les personnes non techniques puissent exécuter la variable [!DNL Upgrade Compatibility Tool] et obtenez une [rapport](../upgrade-compatibility-tool/reports.md) contenant une liste de problèmes pour chaque fichier.

Voir [[!DNL Site-Wide Analysis Tool] guide de l’utilisateur](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) pour plus d’informations.

## Exécutez la variable [!DNL Upgrade Compatibility Tool] de la [!DNL Site-Wide Analysis Tool]

Accédez au [!DNL Site-Wide Analysis Tool] tableau de bord de votre projet et recherchez la variable [!DNL Upgrade Compatibility Tool] widget.

![Widget UCT SWAT - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Cliquez sur **[!UICONTROL Run Upgrade Scan]**. L’analyse peut prendre un certain temps en fonction de la taille du projet. Un compteur indique que l’analyse est en cours.

![Widget UCT SWAT - En cours](../../assets/upgrade-guide/uct-swat-progress.png)

Une fois l’analyse terminée, les résultats de haut niveau s’affichent dans le widget.

![Widget UCT SWAT - Résultats](../../assets/upgrade-guide/uct-swat-results.png)

Cliquez sur **[!UICONTROL Download Report]** pour récupérer la variable [!DNL Upgrade Compatibility Tool] [Rapport HTML](../upgrade-compatibility-tool/reports.md#html-report) et passez en revue les détails.


>[!NOTE]
>
> L’exécution de la variable [!DNL Upgrade Compatibility Tool] via la [!DNL Site-Wide Analysis Tool] optimise vos résultats et vous aide à vous concentrer sur les problèmes nouveaux et critiques pour la mise à niveau de Target. Elle utilise la variable [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) et affiche toujours les résultats en comparant la version de votre projet à la dernière version publiée.
