---
title: Politique relative au cycle de vie des logiciels
description: Découvrez les dates clés de fin de prise en charge logicielle des versions d’Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 2e81a28502d369bc8903e6b9e9154e693260234d
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 7%

---


# Politique relative au cycle de vie d’Adobe Commerce

Pour Adobe Commerce 2.4.4 et les versions ultérieures :

- Afin de rationaliser la politique de cycle de vie d’Adobe Commerce et de répondre aux besoins critiques des clients, Adobe a étendu la période d’assistance à trois ans à compter de la date de disponibilité générale (GA) pour Adobe Commerce 2.4.4 et les versions ultérieures. Adobe fournit des correctifs de qualité pour les versions 2.4.4 et ultérieures pour une période de prise en charge de trois ans. Les clients peuvent accéder aux correctifs de qualité en contactant le support technique d’[Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ou via le [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) en libre-service si leur version est toujours éligible pour le support technique de la qualité. Le tableau suivant décrit les dates de fin de prise en charge logicielle des lignes de version d’Adobe Commerce.

- Adobe fournit des correctifs de sécurité par le biais d’une version de correctif de sécurité pour la période de prise en charge de trois ans.

- Pour les problèmes de sécurité critiques, tels que les vulnérabilités « jour zéro », Adobe fournit des [&#x200B; correctifs logiciels &#x200B;](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) à tous les clients disposant d’une version prise en charge, même s’ils ne disposent pas du dernier correctif ou de la dernière version du correctif de sécurité. Notez qu’un correctif n’est pas exhaustif et ne résout pas tous les problèmes de sécurité qui seraient résolus par une mise à niveau vers la version la plus récente.

- Adobe ne fournit pas de correctifs de sécurité et de qualité pour les services tiers et les dépendances logicielles (telles que PHP et MySQL) qui peuvent arriver en fin de vie lorsque les clients bénéficient de la période de prise en charge de trois ans d’Adobe Commerce. Pour obtenir une liste complète des technologies tierces testées et prises en charge[&#x200B; consultez la section &#x200B;](../installation/system-requirements.md)Configuration requise.

- Pour les clients Adobe Commerce on Cloud utilisant les versions 2.4.4 et 2.4.5, Adobe applique automatiquement les correctifs de sécurité de durée de vie PHP 8.1 à l’infrastructure, de sorte que ces clients ne sont pas affectés par la fin de prise en charge de PHP 8.1. Les clients sur site utilisant Adobe Commerce 2.4.4 et 2.4.5 doivent contacter le support Adobe pour demander des correctifs de sécurité à vie PHP 8.1 si nécessaire.

- Adobe offre une compatibilité avec des services tiers et des dépendances logicielles. En revanche, les clients bénéficient d’une période de prise en charge de trois ans pour Adobe Commerce dans le cadre des versions de correctifs dédiées uniquement à la sécurité, mais uniquement lorsqu’il est possible de le faire sans introduire de modifications rétrocompatibles.

## Prise en charge étendue

Adobe incite les clients à effectuer la mise à niveau dès que possible. Toutefois, pour offrir une plus grande flexibilité afin de s’aligner sur les plans de mise à niveau et les besoins de l’entreprise, Adobe offre une prolongation de prise en charge d’un an sans frais supplémentaires pour les clients Adobe Commerce dans les versions 2.4.4 et 2.4.5. L’extension de prise en charge comprend des correctifs de qualité et de sécurité pour l’application principale pendant un an au maximum.

>[!NOTE]
>
>La prise en charge étendue est disponible uniquement pour les clients Adobe Commerce. Il n’est pas disponible pour la base de code Magento Open Source.

## Fin de la prise en charge logicielle

| Libération | Disponibilité générale | Fin de la prise en charge régulière<sup>1</sup> | Fin de la prise en charge étendue | Version dépendante de PHP | Version dépendante de MariaDB |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | mercredi 8 avril 2025 | mercredi 11 avril 2028 | S.O. | 8.3 et 8.4 | 11,4 |
| Adobe Commerce 2.4.7 | mercredi 9 avril 2024 | samedi 9 avril 2027 | S.O. | 8.2 et 8.3 | 10.11<sup>3</sup> |
| Adobe Commerce 2.4.6 | mercredi 14 mars 2023 | 11 août 2026<sup>2</sup> | S.O. | 8.1 et 8.2 | 10.11<sup>4</sup> |
| Adobe Commerce 2.4.5 | mercredi 9 août 2022 | mercredi 12 août 2025 | mercredi 11 août 2026 | 8,1 | 10,6<sup>5</sup> |
| Adobe Commerce 2.4.4 | mercredi 12 avril 2022 | 12 avril 2022 | mercredi 14 avril 2026 | 8,1 | 10,6<sup>6</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> La fin de la prise en charge logicielle inclut les correctifs de fin de qualité et de fin de sécurité.
>- <sup>2</sup> Mise à jour pour s’aligner sur la fin de la prise en charge étendue de 2.4.5.
>- <sup>3</sup> À partir du correctif de sécurité 2.4.7-p6.
>- <sup>4</sup> À partir du correctif de sécurité 2.4.6-p11.
>- <sup>5</sup> À partir du correctif de sécurité 2.4.5-p11.
>- <sup>6</sup> À partir du correctif de sécurité 2.4.4-p12.
>- Voir [&#x200B; Politique relative au cycle de vie des logiciels &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

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
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
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
 </tbody>
</table>
