---
title: Intégrez le  [!DNL Site-Wide Analysis Tool]
description: Pour récupérer le rapport  [!DNL Upgrade Compatibility Tool]  partir du tableau de bord  [!DNL Site-Wide Analysis Tool]  votre projet Adobe Commerce, procédez comme suit.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Intégrer le [!DNL Site-Wide Analysis Tool]

Le [!DNL Site-Wide Analysis Tool] fournit une surveillance des performances en temps réel, des rapports et des recommandations 24h/24 et 7j/7 pour assurer la sécurité et l’opérabilité des instances Adobe Commerce.

Le [!DNL Upgrade Compatibility Tool] est désormais intégré au [!DNL Site-Wide Analysis Tool] afin de permettre à des personnes n’ayant pas de connaissances techniques d’exécuter le [!DNL Upgrade Compatibility Tool] et d’obtenir un [rapport](../upgrade-compatibility-tool/reports.md) contenant une liste des problèmes pour chaque fichier.

Pour plus d’informations, consultez le [[!DNL Site-Wide Analysis Tool] guide d’utilisation](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/site-wide-analysis-tool/access).

## Exécuter le [!DNL Upgrade Compatibility Tool] à partir de l’[!DNL Site-Wide Analysis Tool]

Accédez au tableau de bord [!DNL Site-Wide Analysis Tool] de votre projet et recherchez le widget [!DNL Upgrade Compatibility Tool].

![Widget SWAT UCT - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Cliquez sur **[!UICONTROL Run Upgrade Scan]**. L’analyse peut prendre un certain temps en fonction de la taille du projet. Une double flèche indique que l’analyse est en cours.

![Widget SWAT UCT - En cours](../../assets/upgrade-guide/uct-swat-progress.png)

Une fois l’analyse terminée, les résultats de haut niveau s’affichent dans le widget.

![Widget SWAT UCT - Résultats](../../assets/upgrade-guide/uct-swat-results.png)

Cliquez sur **[!UICONTROL Download Report]** pour récupérer le [!DNL Upgrade Compatibility Tool] rapport HTML [&#128279;](../upgrade-compatibility-tool/reports.md#html-report) et consulter les détails.


>[!NOTE]
>
> L’exécution du [!DNL Upgrade Compatibility Tool] dans le [!DNL Site-Wide Analysis Tool] optimise vos résultats et vous permet de vous concentrer sur les problèmes nouveaux et critiques pour votre mise à niveau de Target. Elle utilise l’option [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) et affiche toujours les résultats en comparant la version de votre projet à la dernière version publiée.
