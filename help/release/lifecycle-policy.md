---
title: Politique relative au cycle de vie des logiciels
description: Découvrez les dates clés de fin de prise en charge logicielle des versions d’Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3bf3c4261073ab649376bb5c7fb84ea591a09869
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 7%

---


# Politique relative au cycle de vie d’Adobe Commerce

Afin de rationaliser la politique de cycle de vie d’Adobe Commerce et de répondre aux besoins critiques des clients, Adobe propose une période de prise en charge de trois ans à compter de la date de disponibilité générale (DG) pour chaque version. Elle publie également les correctifs de qualité au cours de cette période. Pour connaître les dates et les détails relatifs à la fin de la prise en charge logicielle pour chaque version, reportez-vous au tableau [Fin de la prise en charge logicielle](#end-of-software-support).

Pendant les trois années de support, les clients ont accès aux éléments suivants :

- **Correctifs de qualité**-Les clients peuvent accéder aux correctifs de qualité en contactant le [support d’Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou par le biais du [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) en libre-service. Le tableau suivant décrit les dates de fin de prise en charge logicielle des lignes de version d’Adobe Commerce.

- **Correctifs de sécurité**-Adobe fournit des correctifs de sécurité par le biais de correctifs de sécurité cumulatifs et de fichiers de correctifs de sécurité non cumulatifs [isolés](versioning-policy.md#isolated-security-fixes) pendant la période de prise en charge de trois ans.

- **Correctifs**-Pour les problèmes de sécurité critiques, tels que les vulnérabilités « jour zéro », Adobe fournit [correctifs](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) à tous les clients disposant d’une version prise en charge, même s’ils ne disposent pas du dernier correctif ou de la dernière version du correctif de sécurité. Notez qu’un correctif n’est pas exhaustif et ne résout pas tous les problèmes de sécurité qui seraient résolus par une mise à niveau vers la version la plus récente.

Adobe ne fournit pas de correctifs de sécurité et de qualité pour les services tiers et les dépendances logicielles (telles que PHP et MySQL) qui peuvent arriver en fin de vie lorsque les clients sont dans la période de prise en charge de trois ans ou prolongée d’Adobe Commerce. Pour obtenir une liste complète des technologies tierces testées et prises en charge[&#128279;](../installation/system-requirements.md) consultez la section Configuration requise.

## Prise en charge étendue

Adobe incite les clients à effectuer la mise à niveau dès que possible. Toutefois, pour offrir une plus grande flexibilité afin de s’aligner sur les plans de mise à niveau et les besoins de l’entreprise, Adobe offre une prolongation de prise en charge d’un an sans frais supplémentaires pour les clients Adobe Commerce utilisant la version 2.4.6. L’extension de prise en charge comprend des correctifs de qualité et de sécurité pour l’application principale pendant un an au maximum. La prise en charge étendue des versions 2.4.4 et 2.4.5 d’Adobe Commerce prend fin en avril et août 2026 comme prévu.

>[!NOTE]
>
>La prise en charge étendue est disponible uniquement pour les clients Adobe Commerce. Il n’est pas disponible pour la base de code Magento Open Source.

## Fin de la prise en charge logicielle

| Libération | Disponibilité générale | Fin de la prise en charge régulière<sup>1</sup> | Fin de la prise en charge étendue |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | mercredi 8 avril 2025 | 31 Mai 2028 | À déterminer |
| Adobe Commerce 2.4.7 | mercredi 9 avril 2024 | 31 Mai 2027 | À déterminer |
| Adobe Commerce 2.4.6 | mercredi 14 mars 2023 | mercredi 11 août 2026 | 30 Août 2027 |
| Adobe Commerce 2.4.5 | mercredi 9 août 2022 | mercredi 12 août 2025 | mercredi 11 août 2026 |
| Adobe Commerce 2.4.4 | mercredi 12 avril 2022 | 12 avril 2022 | mercredi 14 avril 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Si vous êtes un client Adobe Commerce, vous pouvez continuer à recevoir des correctifs de sécurité et de qualité pendant une année supplémentaire pendant la période de prise en charge étendue.
>- Voir [&#x200B; Politique relative au cycle de vie des logiciels &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!IMPORTANT]
>
>La conformité PCI ne peut pas être garantie pour les commerçants exécutant la version 2.4.6 qui continuent à utiliser PHP 8.1, qui a atteint [fin de prise en charge en 2025](https://www.php.net/eol.php). De même, PHP 8.2 atteint [fin de vie à la fin de 2026](https://www.php.net/supported-versions.php), créant le même risque de conformité PCI pour les commerçants qui continuent à l&#39;utiliser en 2027.

## Approvisionnement des correctifs de sécurité supplémentaires pour Adobe Commerce 2.4.4 et 2.4.5

À titre d’exception ponctuelle, Adobe fournit une période d’approvisionnement des correctifs de sécurité étendue pour les versions 2.4.4 et 2.4.5 d’Adobe Commerce afin de donner aux clients et aux clientes un temps supplémentaire pour migrer vers Adobe Commerce as a Cloud Service ou effectuer une mise à niveau vers une ligne de version prise en charge.

Pendant cette période d’approvisionnement des correctifs de sécurité, notez ce qui suit :

- **Fichier de correctif de sécurité isolé uniquement**-Un fichier de correctif de sécurité isolé sera publié pour ces versions selon le calendrier de publication. Aucune version de correctif de sécurité (aucune nouvelle version de -p) ne sera fournie pendant cette période.

  Pour appliquer un fichier de correctif de sécurité isolé, les clients doivent disposer de la dernière version du correctif de sécurité uniquement (la dernière version -p) pour leur ligne de version prise en charge, car les correctifs de sécurité isolés sont testés exclusivement par rapport à cette version.

- **Aucun correctif de qualité ou assistance technique**-Aucun correctif, mise à jour de qualité ([Outil de correctifs de qualité](../tools/quality-patches-tool/usage.md)) ou assistance technique ([Assistance Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) ne sera fourni pour les versions 2.4.4 ou 2.4.5 pendant cette période.

- **La conformité PCI n’est pas garantie :**-Étant donné que les versions 2.4.4 et 2.4.5 utilisent PHP qui ont atteint leur fin de vie, la conformité PCI ne peut pas être garantie pour les commerçants sur ces versions. Continuer à exécuter ces versions peut compromettre votre conformité PCI.

Pour maintenir une couverture de sécurité complète et assurer la conformité PCI, les clients doivent effectuer dès que possible une mise à niveau vers une version d’Adobe Commerce actuellement prise en charge ou migrer vers [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/fr/docs/commerce/cloud-service/overview).

| Libération | Disponibilité générale | Fin de la prise en charge étendue | Fin de la mise en service des correctifs de sécurité |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | mercredi 9 août 2022 | mercredi 11 août 2026 | Mai 2027 |
| Adobe Commerce 2.4.4 | mercredi 12 avril 2022 | mercredi 14 avril 2026 | Mai 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>D’autres correctifs de sécurité ne sont disponibles que pour les clients Adobe Commerce et ne sont pas disponibles pour la base de code Magento Open Source.


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
    <td colspan="6"></td>
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
   <td>Assistance régulière</td>
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
