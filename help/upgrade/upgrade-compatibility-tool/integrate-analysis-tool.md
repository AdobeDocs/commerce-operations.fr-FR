---
title: Intégrer le  [!DNL Site-Wide Analysis Tool]
description: Suivez ces étapes pour récupérer le rapport  [!DNL Upgrade Compatibility Tool] du tableau de bord  [!DNL Site-Wide Analysis Tool]  de votre projet Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Intégrer le [!DNL Site-Wide Analysis Tool]

[!DNL Site-Wide Analysis Tool] fournit 24/7 surveillance des performances, rapports et recommandations en temps réel afin d’assurer la sécurité et l’opérabilité des instances Adobe Commerce.

[!DNL Upgrade Compatibility Tool] est désormais intégré à [!DNL Site-Wide Analysis Tool] afin de permettre aux personnes non techniques d&#39;exécuter le [!DNL Upgrade Compatibility Tool] et d&#39;obtenir un [rapport](../upgrade-compatibility-tool/reports.md) contenant une liste de problèmes pour chaque fichier.

Pour plus d’informations, consultez le [[!DNL Site-Wide Analysis Tool] guide de l’utilisateur](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/site-wide-analysis-tool/access) .

## Exécutez le [!DNL Upgrade Compatibility Tool] à partir du [!DNL Site-Wide Analysis Tool]

Accédez au tableau de bord [!DNL Site-Wide Analysis Tool] de votre projet et localisez le widget [!DNL Upgrade Compatibility Tool].

![Widget UCT SWAT - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Cliquez sur **[!UICONTROL Run Upgrade Scan]**. L’analyse peut prendre un certain temps en fonction de la taille du projet. Un compteur indique que l’analyse est en cours.

![Widget UCT SWAT - En cours](../../assets/upgrade-guide/uct-swat-progress.png)

Une fois l’analyse terminée, les résultats de haut niveau s’affichent dans le widget.

![Widget UCT SWAT - Résultats](../../assets/upgrade-guide/uct-swat-results.png)

Cliquez sur **[!UICONTROL Download Report]** pour récupérer le [!DNL Upgrade Compatibility Tool] [rapport d&#39;HTML](../upgrade-compatibility-tool/reports.md#html-report) et passez en revue les détails.


>[!NOTE]
>
> L’exécution de [!DNL Upgrade Compatibility Tool] via [!DNL Site-Wide Analysis Tool] optimise vos résultats et vous aide à vous concentrer sur les problèmes nouveaux et critiques pour la mise à niveau de votre cible. Il utilise l’option [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) et affiche toujours les résultats en comparant la version de votre projet à la dernière version publiée.
