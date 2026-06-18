---
title: Politique relative au cycle de vie des logiciels
description: Découvrez les dates clés de fin de prise en charge logicielle des versions d’Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
source-git-commit: 5846c83cd31e3d253a5ae0b0064b860e5c7af286
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 3%

---


# Politique relative au cycle de vie d’Adobe Commerce

Afin de rationaliser la politique de cycle de vie d’Adobe Commerce et de répondre aux besoins critiques des clients, Adobe propose une période de prise en charge standard de trois ans à compter de la date de disponibilité générale (DG) pour chaque version. Elle publie également les correctifs de qualité au cours de cette période. Pour connaître les dates et les détails relatifs à la fin de la prise en charge logicielle pour chaque version, reportez-vous au tableau [Fin de la prise en charge logicielle](#end-of-software-support).

Adobe ne fournit pas de correctifs de sécurité et de qualité pour les services tiers et les dépendances logicielles (telles que PHP et MySQL) qui peuvent arriver en fin de vie lorsque les clients sont dans la période de prise en charge de trois ans ou prolongée d’Adobe Commerce. Pour obtenir une liste complète des technologies tierces testées et prises en charge[&#128279;](../installation/system-requirements.md) consultez la section Configuration requise.

## Prise en charge standard

Période d’assistance standard de trois ans à compter de la date de disponibilité générale (GA). La prise en charge standard inclut des correctifs de qualité, des correctifs de sécurité et une prise en charge complète d’Adobe Commerce sur appel.

- **Correctifs de qualité** - Les clients peuvent accéder aux correctifs de qualité en contactant le [support d’Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou par l’intermédiaire du [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) en libre-service.

- **Correctifs de sécurité** - Adobe fournit des correctifs de sécurité par le biais de correctifs de sécurité cumulatifs et de fichiers de correctifs de sécurité non cumulatifs [isolés](versioning-policy.md#isolated-security-patch-file) pendant la période de prise en charge de trois ans.

- **Correctifs** - Pour les problèmes de sécurité critiques, tels que les vulnérabilités « jour zéro », Adobe fournit [correctifs](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) à tous les clients disposant d’une version prise en charge, même s’ils ne disposent pas du dernier correctif ou de la dernière version du correctif de sécurité. Notez qu’un correctif n’est pas exhaustif et ne résout pas tous les problèmes de sécurité qui seraient résolus par une mise à niveau vers la version la plus récente.

## Prise en charge étendue

Adobe incite les clients à effectuer la mise à niveau dès que possible. Toutefois, pour offrir une plus grande flexibilité afin de s’aligner sur les plans de mise à niveau et les besoins de l’entreprise, Adobe offre une année de prise en charge supplémentaire sans frais supplémentaires pour les clients Adobe Commerce dans les versions 2.4.6 et 2.4.7. L’extension de prise en charge comprend des correctifs de qualité et de sécurité pour l’application principale. La prise en charge étendue des versions 2.4.4 et 2.4.5 d’Adobe Commerce prend fin en avril et août 2026 comme prévu.

>[!NOTE]
>
>Adobe introduit une politique de mise à niveau de version forcée pour Adobe Commerce on Cloud. À compter du **1er juin 2027**, Adobe ne gérera plus les environnements cloud exécutant des versions de Commerce non prises en charge et se réserve le droit de les mettre hors service. Si vous exécutez sur le cloud, vous devez passer à une version d’Adobe Commerce prise en charge ou migrer vers [!DNL Adobe Commerce as a Cloud Service] avant la date [fin de la prise en charge étendue](lifecycle-policy.md#end-of-support-dates) publiée pour votre ligne de mise à jour. Consultez [Politique d’application de la mise à niveau des versions du cloud](version-upgrade-enforcement-policy.md) pour connaître les dates d’application, les versions affectées et ce qui se passe si vous utilisez une version non prise en charge.

## Période transitoire réservée à la sécurité

Une période transitoire unique et limitée dans le temps disponible uniquement pour les versions 2.4.4, 2.4.5 et 2.4.6 dont le support étendu a pris fin en 2025 ou 2026. La période de transition de sécurité uniquement fournit uniquement des correctifs de sécurité isolés limités. Les correctifs de qualité d’Adobe Commerce ne sont pas fournis. Cette période n’est pas équivalente à la prise en charge standard ou étendue et ne sera pas prolongée davantage. Traitez-la comme une période de migration et non comme un niveau d’assistance à long terme.

>[!IMPORTANT]
>
>La période transitoire réservée à la sécurité est une exception ponctuelle. Il ne sera pas prolongé au-delà des dates publiées. Traitez la période de sécurité uniquement comme une période de migration et non comme un niveau d’assistance à long terme.

## Dates de fin de prise en charge

Le tableau suivant présente le cycle de vie complet de chaque version d’Adobe Commerce, y compris les nouvelles dates d’application de la mise à niveau des versions d’Adobe Commerce dans les environnements cloud.

| Libération | Disponibilité générale | Fin de la prise en charge standard | Fin de la prise en charge étendue | Fin de la période réservée à la sécurité | [Date d’application de la mise à niveau de la version (cloud uniquement)](version-upgrade-enforcement-policy.md) |
| --------- | ---------------------- | ------------------------ | ------------------------- |-----------------------------| ----------------------------------------------- |
| Adobe Commerce 2.4.9 | 12 Mai 2026 | 31 Mai 2029 | À déterminer | S.O. | À déterminer |
| Adobe Commerce 2.4.8 | mercredi 8 avril 2025 | 31 Mai 2028 | À déterminer | S.O. | À déterminer |
| Adobe Commerce 2.4.7 | mercredi 9 avril 2024 | 31 Mai 2027 | 31 Mai 2028 | S.O. | 1er juin 2028 |
| Adobe Commerce 2.4.6 | mercredi 14 mars 2023 | mercredi 11 août 2026 | 30 Août 2027 | 31 Mai 2028 | 1er juin 2028 |
| Adobe Commerce 2.4.5 | mercredi 9 août 2022 | mercredi 12 août 2025 | 12 Août 2026 | 31 Mai 2027 | 1er juin 2027 |
| Adobe Commerce 2.4.4 | mercredi 12 avril 2022 | 12 avril 2022 | mercredi 14 avril 2026 | 31 Mai 2027 | 1er juin 2027 |

{style="table-layout:auto"}

## Chronologie de la prise en charge

La chronologie de prise en charge mappe les périodes de prise en charge trimestre par trimestre pour chaque ligne de version d’Adobe Commerce. Utilisez les tableaux fournis précédemment dans cette rubrique pour connaître les dates de fin exactes.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Clé**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Prise en charge standard</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Prise en charge étendue</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Correctifs de sécurité étendus</td>
  </tr>
 </tbody>
</table>

## Dépendances de la plateforme

La conservation d’une version de Commerce prise en charge nécessite également des dépendances de plateforme prises en charge. Adobe ne fournit pas de correctifs de sécurité et de qualité pour les services tiers et les dépendances logicielles, telles que MariaDB, OpenSearch, Redis, Valkey, RabbitMQ, etc., qui peuvent atteindre la fin de vie pendant que vous bénéficiez de la période de prise en charge de trois ans ou prolongée d’Adobe Commerce. Voir [Sécurité de la responsabilité partagée et modèle opérationnel](../security-and-compliance/shared-responsibility.md) pour plus de détails.

Il vous incombe de gérer toutes les dépendances tierces et tous les services Platform sur les versions qui sont activement prises en charge. Consultez [Configuration requise](../installation/system-requirements.md) pour obtenir la liste complète des technologies tierces testées et prises en charge.

## Fin de vie de PHP et conformité PCI

Vous êtes responsable de la surveillance de l&#39;état de prise en charge des versions PHP utilisées dans vos environnements.

Les versions PHP suivantes utilisées par les anciennes lignes de versions de Commerce ont atteint ou atteindront leur fin de vie, ce qui a des implications directes sur la conformité PCI.

| Version PHP | Date de fin de vie | Versions de Commerce affectées | Impact sur la conformité PCI |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 31 Décembre 2025 | 2.4.4, 2.4.5 et 2.4.6 (où PHP 8.1 est utilisé) | Conformité PCI en danger : l&#39;exécution de PHP 8.1 au-delà de sa date de fin de vie signifie que les vulnérabilités de sécurité de PHP peuvent ne pas recevoir de correctifs, ce qui met la conformité PCI en danger. Évaluez le statut de conformité et hiérarchisez les mises à niveau. |
| PHP 8.2 | 31 Décembre 2026 | 2.4.6 (où PHP 8.2 est utilisé) | Conformité PCI menacée à partir de la fin de 2026 : planifiez la mise à niveau ou la migration avant la fin de 2026 pour maintenir la conformité PCI. |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**Avis de conformité PCI :** la conformité PCI est la responsabilité du commerçant d’évaluer. Adobe recommande vivement aux commerçants des versions concernées de consulter leur évaluateur de sécurité qualifié et de passer en priorité à une version Commerce prise en charge et à une version PHP prise en charge dès que possible. Pour les délais de support PHP, voir [Versions supportées PHP](https://www.php.net/supported-versions.php) et [Fin de vie PHP](https://www.php.net/eol.php).

## Options de mise à niveau et de migration

Si vous utilisez une version dont les dates de fin de prise en charge sont approchées ou dépassées, prenez des mesures dès maintenant. Si vous conservez une version non prise en charge, votre boutique risque de présenter des vulnérabilités en matière de sécurité, des problèmes de conformité et une perte de prise en charge. Adobe fournit les chemins d’accès suivants pour migrer vers une version prise en charge.

### Chemin recommandé : migrer vers Adobe Commerce as a Cloud Service

[!DNL Adobe Commerce as a Cloud Service] est la plateforme commerciale hébergée de nouvelle génération d’Adobe et la destination à long terme recommandée par Adobe pour tous les clients Adobe Commerce on Cloud.

- Adobe gère automatiquement l’ensemble de l’infrastructure, des correctifs et des mises à niveau.
- Vous disposez toujours d’une infrastructure compatible et prise en charge. La situation de fin de vie ne se reproduit pas.
- Vous avez accès aux dernières fonctionnalités d’Adobe : marchandisage optimisé par l’IA, architecture de storefront composable et intégrations natives d’Adobe Experience Cloud.
- Vous éliminez les cycles de mise à niveau récurrents.

Contactez l’équipe de votre compte Adobe pour commencer une évaluation de la migration. Voir [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/fr/docs/commerce/cloud-service/overview) pour la présentation du produit.

### Chemin alternatif : effectuer une mise à niveau vers une version prise en charge d’Adobe Commerce on cloud ou on-premise

Si vous ne pouvez pas migrer vers [!DNL Adobe Commerce as a Cloud Service] immédiatement, vous pouvez effectuer une mise à niveau vers la dernière version d’Adobe Commerce on Cloud actuellement prise en charge. Vous passez ainsi à une pile d’infrastructure moderne entièrement prise en charge, tout en préservant votre modèle de déploiement Commerce on Cloud existant.

Notez que ce chemin d’accès n’élimine pas les futures obligations de mise à niveau. Les clients disposant d’Adobe Commerce sur des déploiements cloud doivent continuer la mise à niveau lorsque les lignes de version atteignent leurs dates d’application de mise à niveau.
