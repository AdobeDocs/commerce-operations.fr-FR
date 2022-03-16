---
title: Contrats de niveau de service
description: Découvrez les contrats de niveau de service et comment les utiliser pour prendre en charge votre mise en oeuvre Adobe Commerce.
exl-id: 5da42dfa-e165-4142-a863-6f3ce7689478
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# Contrats de niveau de service (SLA)

Le contrat de niveau de service (SLA) définit le niveau de service attendu par un client auprès du fournisseur de services, avec des mesures simples par lesquelles ce service est mesuré, ainsi que les remèdes ou pénalités, le cas échéant, si les niveaux de service convenus ne sont pas atteints.

Les contrats de niveau de service (SLA) pour différents types de critiques d’incident peuvent être conclus, conservés et mesurés. De plus, le type de réponse peut avoir plusieurs standards (Gold, Platine), en fonction du niveau de service requis par le client.

Le tableau suivant décrit une ventilation de mesure SLA type avec plusieurs niveaux de service :

<table>
<thead>
  <tr>
    <th>Type de problème</th>
    <th>Impact</th>
    <th>Exemple</th>
    <th colspan="2">Temps de réponse/restauration pendant les heures de bureau prises en charge</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>Gold</td>
    <td>Platine</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Impact critique</td>
    <td>Service vers le bas ou inutilisable</td>
    <td>1 heure / 4 heures</td>
    <td>1 heure / 4 heures</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Service indisponible</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Le service est inutilisable sur l’ensemble de la base de l’utilisateur final.</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>Impact élevé</td>
    <td>Service gravement endommagé</td>
    <td>2 heures / 12 heures</td>
    <td>2 heures / 8 heures</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Les performances du service sont dégradées.</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Service disponible, mais produisant des messages d’erreur significatifs</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>Impact moyen</td>
    <td>Service partiellement défaillant</td>
    <td>8 heures / 16 heures</td>
    <td>8 heures / 12 heures</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Messages d’erreur générés, sans impact utilisateur final perceptible</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Questions sur les fonctionnalités utilisées dans le lancement client</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## Options de couverture

Les options de couverture pour les contrats de niveau de service (SLA) validés varient selon les types d’offres. En règle générale, la portée des services d’assistance Gold et Platinum ressemble à ce qui suit :

![Infos montrant les options de couverture SLA](../../assets/playbooks/sla-coverage-options.svg)
