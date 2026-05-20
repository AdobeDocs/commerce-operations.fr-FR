---
title: Politique relative au cycle de vie d’Adobe Commerce
description: Découvrez les périodes de prise en charge d’Adobe Commerce, les dates de fin de prise en charge et d’application dans le cloud, les dispositions transitoires et les chemins d’accès vers une version prise en charge.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 2%

---


# Politique relative au cycle de vie d’Adobe Commerce

Adobe Commerce suit une politique définie en matière de cycle de vie des logiciels pour s’assurer que les clients utilisent des versions sécurisées et prises en charge. Si vous utilisez une ligne de version plus ancienne, il est essentiel de comprendre où vous en êtes dans ce cycle de vie et d’agir avant les dates limites d’application. Cette rubrique couvre les définitions du niveau de prise en charge, les dates de fin de prise en charge et d’application, les dispositions transitoires pour les versions approchant de la fin de vie et les chemins d’accès pour rester sur une version prise en charge.

>[!IMPORTANT]
>
>Adobe introduit une politique de mise à niveau de version forcée pour Adobe Commerce on Cloud (PaaS). À compter du **1er juin 2027**, Adobe cessera de gérer les environnements cloud exécutant des versions de Commerce non prises en charge et se réserve le droit de les désactiver. Si vous exécutez sur Cloud (PaaS), vous devez passer à une version d’Adobe Commerce prise en charge ou migrer vers [!DNL Adobe Commerce as a Cloud Service] avant la date de [fin de prise en charge étendue](lifecycle-policy.md#end-of-support-dates) publiée pour votre ligne de version. Consultez [Politique d’application de la mise à niveau des versions du cloud](version-upgrade-enforcement-policy.md) pour connaître les dates d’application, les versions affectées et ce qui se passe si vous utilisez une version non prise en charge.

## Présentation des niveaux d’assistance

Adobe Commerce définit trois niveaux de prise en charge pour les lignes de version. Les sections suivantes décrivent chaque niveau.

### Assistance régulière

Période d’assistance standard de trois ans à compter de la date de disponibilité générale (GA). La prise en charge régulière inclut des correctifs de qualité, des correctifs de sécurité et une prise en charge complète d’Adobe Commerce sur appel.

- **Correctifs de qualité** - Les clients peuvent accéder aux correctifs de qualité en contactant le [support d’Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou par l’intermédiaire du [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en libre-service.

- **Correctifs de sécurité** - Adobe fournit des correctifs de sécurité par le biais de correctifs de sécurité cumulatifs et de fichiers de correctifs de sécurité non cumulatifs [isolés](versioning-policy.md#isolated-security-patch-file) pendant la période de prise en charge de trois ans.

- **Correctifs** - Pour les problèmes de sécurité critiques, tels que les vulnérabilités « jour zéro », Adobe fournit [correctifs](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) à tous les clients disposant d’une version prise en charge, même s’ils ne disposent pas du dernier correctif ou de la dernière version du correctif de sécurité. Notez qu’un correctif n’est pas exhaustif et ne résout pas tous les problèmes de sécurité qui seraient résolus par une mise à niveau vers la version la plus récente.

### Prise en charge étendue

Extension d’un an de l’assistance disponible pour des lignes de version spécifiques, au-delà de l’assistance standard. Comprend des correctifs de qualité et de sécurité. Disponible uniquement pour les clients Adobe Commerce — non disponible pour Magento Open Source.

### Période transitoire réservée à la sécurité

Période transitoire unique et limitée dans le temps disponible pour des versions spécifiques dont la prise en charge étendue a pris fin en 2025 ou 2026. La période de transition de sécurité uniquement fournit uniquement des correctifs de sécurité isolés limités. La prise en charge d’Adobe Commerce sur appel n’est pas incluse. Cette période n’équivaut pas à un soutien régulier ou prolongé et ne sera pas prolongée davantage. Traitez-la comme une période de migration et non comme un niveau d’assistance à long terme. Voir [Dispositions transitoires concernant uniquement la sécurité](#security-only-transitional-provisions).

## Dates de fin de prise en charge

Le tableau suivant présente le cycle de vie complet de chaque version d’Adobe Commerce, y compris les nouvelles dates d’application de la mise à niveau des versions pour les environnements Adobe Commerce on Cloud (PaaS).

| Libération | Disponibilité générale | Fin de la prise en charge régulière | Fin de la prise en charge étendue | Fin de la période réservée à la sécurité | [Date d’application de la mise à niveau de la version (cloud uniquement)](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | 12 Mai 2026 | 31 Mai 2029 | À déterminer | S.O. | À déterminer |
| Adobe Commerce 2.4.8 | mercredi 8 avril 2025 | 31 Mai 2028 | À déterminer | S.O. | À déterminer |
| Adobe Commerce 2.4.7 | mercredi 9 avril 2024 | 31 Mai 2027 | 31 Mai 2028 | S.O. | 1er juin 2028 |
| Adobe Commerce 2.4.6 | mercredi 14 mars 2023 | mercredi 11 août 2026 | 30 Août 2027 | 31 Mai 2028 | 1er juin 2028 |
| Adobe Commerce 2.4.5 | mercredi 9 août 2022 | mercredi 12 août 2025 | 12 Août 2026 | 31 Mai 2027 | 1er juin 2027 |
| Adobe Commerce 2.4.4 | mercredi 12 avril 2022 | 12 avril 2022 | mercredi 14 avril 2026 | 31 Mai 2027 | 1er juin 2027 |

{style="table-layout:auto"}

Si votre ligne de version approche de ces dates ou les dépasse, consultez [Options de mise à niveau et de migration](#upgrade-and-migration-options). Pour plus d’informations sur l’application cloud, voir [ Politique d’application de mise à niveau de version cloud ](version-upgrade-enforcement-policy.md).

### Chronologie de la prise en charge par trimestre

Utilisez ce graphique pour voir les fenêtres de prise en charge qui se chevauchent sur les lignes de version. Pour connaître les dates de fin exactes, consultez les tableaux ci-dessus. La prise en charge étendue des versions 2.4.8 et 2.4.9 est à déterminer et n’est pas affichée.

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
    <th colspan="4">2029</th>
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
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
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
   <td>Assistance régulière</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Prise en charge étendue</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Période transitoire réservée à la sécurité</td>
  </tr>
 </tbody>
</table>

## Dispositions transitoires concernant uniquement la sécurité {#security-only-transitional-provisions}

En tant que mesure ponctuelle pour les versions 2.4.4, 2.4.5 et 2.4.6 avec prise en charge étendue qui a déjà pris fin en 2025 et 2026, Adobe fournit les dispositions transitoires suivantes pour vous donner plus de temps pour planifier et exécuter votre migration ou mise à niveau. Ces dispositions ne remplacent pas l’application de la mise à niveau de la version [Cloud](version-upgrade-enforcement-policy.md) pour les environnements PaaS. Vous devez toujours effectuer la mise à niveau ou la migration avant la date d’application publiée.

| Version | Disposition transitoire | Période | Éléments inclus | Éléments non inclus |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4 et 2.4.5 | Période transitoire réservée à la sécurité | Jusqu’Au 31 Mai 2027 | Correctifs de sécurité isolés limités au cas par cas | Prise en charge d’Adobe Commerce on-call, correctifs de qualité, mises à jour des dépendances de plateforme |
| 2.4.6 | Prise en charge étendue + période transitoire réservée à la sécurité | Prise en charge étendue jusqu’au 30 août 2027. Période de sécurité uniquement jusqu’au 31 mai 2028. | Période de prise en charge étendue : correctifs de qualité et de sécurité. Période de sécurité uniquement : correctifs de sécurité isolés limités. | Pendant la période de sécurité uniquement : prise en charge d’Adobe Commerce sur appel, correctifs de qualité, mises à jour des dépendances de la plateforme. |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>La période transitoire réservée à la sécurité est une exception ponctuelle. Il ne sera pas prolongé au-delà des dates publiées. Traitez la période de sécurité uniquement comme une période de migration et non comme un niveau d’assistance à long terme.

## Dépendances de la plateforme

La conservation d’une version de Commerce prise en charge nécessite également des dépendances de plateforme prises en charge. Adobe ne fournit pas de correctifs de sécurité et de qualité pour les services tiers et les dépendances logicielles telles que PHP, MariaDB, OpenSearch, Redis, Valkey, RabbitMQ, etc., qui peuvent atteindre la fin de vie pendant que vous bénéficiez de la période de prise en charge de trois ans ou prolongée d’Adobe Commerce.

Il vous incombe de gérer toutes les dépendances tierces et tous les services Platform sur les versions qui sont activement prises en charge. Consultez [Configuration requise](../installation/system-requirements.md) pour obtenir la liste complète des technologies tierces testées et prises en charge.

Adobe ne fournit pas de prise en charge ni d’assistance en matière de sécurité pour les déploiements exécutant des versions dépendantes non prises en charge. Voir [Sécurité de la responsabilité partagée et modèle opérationnel](../security-and-compliance/shared-responsibility.md) pour plus de détails.

>[!IMPORTANT]
>
>L’exécution de versions de dépendance non prises en charge peut entraîner une vulnérabilité de sécurité sur votre instance cloud qu’Adobe ne peut pas résoudre. Dans ce cas, Adobe se réserve le droit d’imposer une mise à niveau de la dépendance logicielle concernée ou de désactiver le service si une mise à niveau n’est pas possible, quel que soit votre statut de prise en charge de la version d’Adobe Commerce.

## Fin de vie de PHP et conformité PCI

Vous êtes responsable de la surveillance de l&#39;état de prise en charge des versions PHP utilisées dans vos environnements.

Les versions PHP suivantes utilisées par les anciennes lignes de versions de Commerce ont atteint ou atteindront leur fin de vie, ce qui a des implications directes sur la conformité PCI.

| Version PHP | Date de fin de vie | Versions de Commerce affectées | Impact sur la conformité PCI |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | 31 Décembre 2025 | 2.4.4, 2.4.5 et 2.4.6 (où PHP 8.1 est utilisé) | Conformité PCI en danger : l&#39;exécution de PHP 8.1 au-delà de sa date de fin de vie signifie que les vulnérabilités de sécurité de PHP peuvent ne pas recevoir de correctifs, ce qui met la conformité PCI en danger. Évaluez le statut de conformité et hiérarchisez les mises à niveau. |
| PHP 8.2 | 31 Décembre 2026 | 2.4.6 (où PHP 8.2 est utilisé) | Conformité PCI menacée à partir de la fin de 2026 : planifiez la mise à niveau ou la migration avant la fin de 2026 pour maintenir la conformité PCI. |

{style="table-layout:auto"}

### Avis de conformité PCI

La conformité PCI est la responsabilité du commerçant d&#39;évaluer. Adobe recommande vivement aux commerçants des versions concernées de consulter leur évaluateur de sécurité qualifié et de passer en priorité à une version Commerce prise en charge et à une version PHP prise en charge dès que possible. Pour les délais de support PHP, voir [Versions supportées PHP](https://www.php.net/supported-versions.php) et [Fin de vie PHP](https://www.php.net/eol.php).

## Options de mise à niveau et de migration

Si vous utilisez une version dont les dates de fin de prise en charge sont approchées ou dépassées, prenez des mesures dès maintenant. Si vous conservez une version non prise en charge, votre boutique risque de présenter des vulnérabilités en matière de sécurité, des problèmes de conformité et une perte de prise en charge. Adobe fournit les chemins d’accès suivants pour migrer vers une version prise en charge.

### Chemin recommandé : migrer vers Adobe Commerce as a Cloud Service (ACCS)

[!DNL Adobe Commerce as a Cloud Service] est la plateforme commerciale hébergée de nouvelle génération d’Adobe et la destination à long terme recommandée par Adobe pour tous les clients Adobe Commerce on Cloud.

- Adobe gère automatiquement l’ensemble de l’infrastructure, des correctifs et des mises à niveau.
- Vous disposez toujours d’une infrastructure compatible et prise en charge. La situation de fin de vie ne se reproduit pas.
- Vous avez accès aux dernières fonctionnalités d’Adobe : marchandisage optimisé par l’IA, architecture de storefront composable et intégrations natives de Adobe Experience Cloud.
- Vous éliminez les cycles de mise à niveau récurrents.

Contactez l’équipe de votre compte Adobe pour commencer une évaluation de la migration. Voir [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview) pour la présentation du produit.

### Chemin alternatif : effectuer une mise à niveau vers une version prise en charge d’Adobe Commerce on cloud ou on-premise

Si vous ne pouvez pas migrer vers [!DNL Adobe Commerce as a Cloud Service] immédiatement, vous pouvez effectuer une mise à niveau vers la dernière version d’Adobe Commerce on-premise ou sur le cloud actuellement prise en charge. Vous passez ainsi à une pile d’infrastructure moderne entièrement prise en charge tout en préservant votre modèle de déploiement PaaS existant.

Notez que ce chemin d’accès n’élimine pas les futures obligations de mise à niveau. Les clients PaaS doivent continuer la mise à niveau lorsque les lignes de version atteignent leurs dates d&#39;application de mise à niveau de version.
