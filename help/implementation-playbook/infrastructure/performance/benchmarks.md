---
title: Évaluations de performances
description: Examinez les résultats des tests de performance pour les implémentations Adobe Commerce hébergées sur l’infrastructure cloud d’Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Résumé des tests

Les résultats des tests de performances d’Adobe Commerce 2.4.5 reflètent les performances mesurées sur une instance Adobe Commerce déployée avec l’infrastructure suivante et les composants supplémentaires.
- [Environnement cloud professionnel](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) avec [architecture mise à l’échelle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B pour Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Il n’existe aucune personnalisation supplémentaire.

Les informations suivantes résument les résultats des tests d’évaluation et fournissent des informations sur l’environnement et les données utilisés lors des tests.

## Mesures de performances clés

La figure suivante montre la configuration de la boutique Commerce pour l’évaluation des performances et les mesures de performances clés des résultats de test.

![JMeter d’évaluation des performances et infrastructure de production](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Selon des critères de test qui imitent une organisation B2C d’entreprise, le système peut gérer les numéros de trafic et de commande demandés aux heures de pointe, à un flux de charge standard.

### Mise en évidence des performances

- **Commandes**: traitement de 3 481 commandes par minute tout en conservant des temps de réponse de moins de 2 secondes pour le 99e percentile (99 % des demandes ont été traitées avec un temps de réponse inférieur à 2 secondes).
- **Pages vues**: géré plus de 2 millions de pages vues par heure tout en conservant des temps de réponse de moins de 2 secondes pour le 99e percentile.
- **SKU efficaces**— Le profil client comprenait 242 millions de variations de prix différentes (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) pour 250 000 produits.
- **Requêtes GraphQL**: système mis à l’échelle à 10 500 demandes GraphQL non mises en cache par minute tout en conservant des temps de réponse de moins de 2 secondes pour le 99e percentile.
- **Utilisateurs administrateurs simultanés**: système mis à l’échelle pour prendre en charge 500 utilisateurs administrateurs simultanés tout en conservant des temps de réponse de moins de 2 secondes pour le 99e percentile.

## Environnement de test

Les résultats des tests de performance ont été obtenus en comparant une instance Adobe Commerce 2.4.5 déployée dans un environnement cloud Pro avec une architecture mise à l’échelle. Les modules d’intégration Adobe Commerce B2B, Inventory management et Adobe Stock étaient également installés, configurés et activés sur l’instance.

Les données de test de performance du profil de test ont été générées à l’aide de la variable <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Outils de performance</a>.

Les mesures de performances sont basées sur des activités de magasin quotidiennes simulées pour les clients et les utilisateurs professionnels. Les valeurs reflètent un débit proche du maximum pour chaque cas, mais ne reflètent pas de modèles commerciaux uniques, tels que les ventes privées ou les ventes flash.

- **LUMA Storefront**
   - 3 000 utilisateurs simultanés sur storefront
   - Défini sur 30 % du taux d’accès au cache du réseau CDN

      L’utilisation efficace de la couche de cache augmente le nombre de pages vues par heure.

- **API GraphQL**
   - 250 threads simultanés
   - Définir sur 0 % le taux d’accès au cache du réseau CDN

      Les temps de réponse s’améliorent considérablement avec une couche de mise en cache devant GraphQL.

- **Admin Web**
   - 500 utilisateurs simultanés
   - Définir sur 0 % le taux d’accès au cache du réseau CDN

## Spécifications de l’environnement de test

Le test de chargement a été terminé à l’aide des profils de chargement JMeter exécutés sur l’instance Adobe Commerce. Trois noeuds web et trois noeuds de service ont été utilisés pendant le test. L’image suivante présente le point d’entrée de l’infrastructure JMeter et Production.

![JMeter d’évaluation des performances et infrastructure de production](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Application

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> déployé sur l’infrastructure cloud avec l’architecture Pro.

### Infrastructure

Pour la référence de performances, Adobe Commerce 2.4.5 a été déployé sur un [infrastructure évolutive](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) avec la capacité suivante.

- **Spécifications des noeuds web**
   - vCPU 216 (72 x 3 noeuds)
   - Mémoire 432 GiB (144 x 3 noeuds)
   - Bande passante réseau 768 Gbit/s (256 x 3 noeuds)
   - Stockage mis en service 100 Go

- **Spécifications du noeud de service**
   - vCPU 192 (64 x 3 noeuds)
   - Mémoire 768 GiB (256 x 3 noeuds)
   - Bande passante réseau 60 Gbit/s (20 x 3 noeuds)
   - Bande passante EBS 4 080 Mbit/s (1 3600 x 3 noeuds)
   - Stockage mis en service 1 100 Go
