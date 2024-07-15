---
title: Stratégie de cycle de vie du logiciel
description: Découvrez les dates clés de fin de prise en charge logicielle des versions d’Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Stratégie de cycle de vie Adobe Commerce

Pour Adobe Commerce 2.4.4 et les versions ultérieures :

- Afin de rationaliser la politique de cycle de vie d’Adobe Commerce et de prendre en charge les besoins critiques des clients, Adobe a étendu la période de prise en charge à trois ans à compter de la date de disponibilité générale (GA) d’Adobe Commerce 2.4.4 et versions ultérieures. Adobe fournit des correctifs de qualité aux versions 2.4.4 et ultérieures pour une période de prise en charge de trois ans. Les clients peuvent accéder aux correctifs de qualité en contactant le [support Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) ou par le biais du [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en libre-service si leur version est toujours éligible à la prise en charge de la qualité. Reportez-vous au tableau ci-dessous pour connaître les dates de fin de la prise en charge logicielle des lignes de mise à jour d’Adobe Commerce.

- Adobe fournit des correctifs de sécurité par le biais d’une version de correctif de sécurité pour la période de prise en charge de trois ans.

- Pour les problèmes de sécurité critiques, tels que les vulnérabilités de zéro jour, Adobe fournit des [correctifs](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) pour tous les clients sur une version prise en charge, même s’ils ne sont pas sur le dernier correctif ou la dernière version de correctif de sécurité. Il est important de noter qu’un correctif n’est pas un fourre-tout et ne traite pas tous les problèmes de sécurité qui seraient résolus en effectuant une mise à niveau vers la dernière version.

- Adobe ne fournit pas de correctifs de sécurité et de qualité pour les services tiers et les dépendances logicielles (comme PHP et MySQL) qui peuvent atteindre la fin de vie pendant que les clients sont sur la période de prise en charge de trois ans d’Adobe Commerce. Pour obtenir la liste complète des technologies tierces testées et prises en charge, reportez-vous à la [configuration requise](../installation/system-requirements.md).

- Adobe offre une compatibilité avec les services tiers et les dépendances logicielles, tandis que les clients bénéficient d’une période de prise en charge de trois ans pour Adobe Commerce dans le cadre des mises à jour de correctifs propres à la sécurité, mais uniquement lorsqu’il est possible de le faire sans introduire de modifications rétrocompatibles.

## Fin de la prise en charge des logiciels

| Version | Disponibilité générale | Fin de la prise en charge du logiciel<sup>1</sup> | Version de PHP dépendante | Version MariaDB dépendante |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 avril 2024 | 9 avril 2027 | 8.2 et 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 mars 2023 | 14 mars 2026 | 8.1 et 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 août 2022 | 9 août 2025 | 8,1 | 10.5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 12 avril 2022 | 24 avril 2025 | 8,1 | 10.5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> La fin de la prise en charge du logiciel inclut à la fois des correctifs de fin de qualité et des correctifs de fin de sécurité.
>- <sup>2</sup> À partir du correctif de sécurité 2.4.5-p8.
>- <sup>3</sup> à partir du correctif de sécurité 2.4.4-p9.
>- Voir [Stratégie de cycle de vie des logiciels](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Clé**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Pris en charge</td>
   <td>Correctifs de sécurité et de qualité pour Adobe Commerce</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
