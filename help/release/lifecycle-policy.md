---
title: Stratégie de cycle de vie du logiciel
description: Découvrez les dates clés de fin de la prise en charge logicielle des versions d’Adobe Commerce.
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Stratégie de cycle de vie Adobe Commerce

Pour Adobe Commerce 2.4 et les versions ultérieures :

- Pour rationaliser davantage notre stratégie de cycle de vie, Adobe fournit des correctifs de qualité à la ligne de mise à jour 2.4 jusqu’à la date de fin de prise en charge de la version PHP sur laquelle elle est basée. Un client peut accéder à des correctifs de qualité en contactant [Prise en charge d’Adobe Commerce](https://developer.adobe.com/commerce/contributor/community/support/) ou par le libre-service [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;} si leur version est toujours éligible à la prise en charge de la qualité. Reportez-vous au tableau ci-dessous pour connaître les dates de fin de prise en charge des logiciels pour les lignes de mise à jour d’Adobe Commerce.

- Adobe ne fournit des correctifs de sécurité que par le biais du dernier correctif ou de la dernière version de correctif de sécurité, même si la version d’un client est toujours éligible à la prise en charge de la qualité. Contrairement aux correctifs de qualité, les correctifs de sécurité ne peuvent pas être rétroportés aux versions mineures précédentes ni aux versions de correctif antérieures dans les versions mineures prises en charge.

- Pour les problèmes de sécurité critiques, tels que les vulnérabilités de zéro jour, Adobe fournit [correctifs](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) pour tous les clients utilisant une version prise en charge, même s’ils ne se trouvent pas sur la dernière version de correctif ou de correctif de sécurité. Il est important de noter qu’un correctif n’est pas un fourre-tout et ne traite pas tous les problèmes de sécurité qui seraient résolus en effectuant une mise à niveau vers la dernière version.

## Fin de la prise en charge logicielle

| Version | Date de publication | Fin de la prise en charge logicielle<sup>1</sup> | Version PHP dépendante |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 28 novembre 2018 | 8 septembre 2022<sup>2</sup> | PHP 7.3 et 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 28 juillet 2020 | 28 novembre 2022 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 12 avril 2022 | 25 novembre 2024 | PHP 8.1 |

<sup>1 Fin de la prise en charge logicielle comprend à la fois des correctifs de fin de qualité et des correctifs de fin de sécurité.</sup><br>
<sup>2 La date de fin de la prise en charge logicielle de la version 2.3 a été étendue au 8 septembre 2022 afin que les clients disposent de plus de temps pour la mise à niveau vers la version 2.4.4, qui sera disponible en général le 8 mars 2022.</sup><br>
<sup>3 2.3.0-2.3.6 dépendent de PHP 7.3 ; 2.3.7 dépend de PHP 7.4.</sup>

>[!NOTE]
>
>Voir [Stratégie de cycle de vie logicielle](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7,4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">Nov</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">Mar</td>
    <td rowspan="2" style="background-color:#cd3c3c;">Nov</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">Aug</td>
  </tr>
</tbody>
</table>

## Clé

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Pris en charge</td>
   <td>Version entièrement testée par Adobe et prise en charge.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">Fin de la prise en charge logicielle</td>
   <td>Version qui a atteint la fin de la prise en charge logicielle.</td>
  </tr>
 </tbody>
</table>
