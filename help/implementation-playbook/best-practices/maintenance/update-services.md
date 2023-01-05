---
title: Bonnes pratiques relatives aux services de mise à jour
description: Découvrez comment conserver votre Adobe Commerce sur la pile de technologie de l’infrastructure cloud mise à jour.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Bonnes pratiques relatives aux services de mise à jour

Cet article fournit des recommandations pour que votre Adobe Commerce reste à jour sur la pile de technologie de l’infrastructure cloud et fournit des liens vers des ressources utiles.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.4.x et versions ultérieures

## Mise à jour des services

Mettez à niveau les services et les composants utilisés par Adobe Commerce avant qu’ils n’atteignent ou ne se rapprochent de la date de fin de vie. Cela permet de respecter la conformité PCI et de réduire les vulnérabilités de sécurité.

Les clients utilisant des plans de démarrage peuvent se servir eux-mêmes lors des mises à niveau de services. Voir [Modification de la version du service](https://devdocs.magento.com/cloud/project/services.html#change-service-version) pour plus d’informations sur la manière de procéder.

Les clients des forfaits Pro ne peuvent être en libre-service que lors des mises à niveau de services dans leurs [Environnement d’intégration](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Pour les mises à niveau de services en production, vous devez [envoi d’un ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) demande de mise à niveau.

>[!WARNING]
>
>Les mises à niveau de service ne peuvent pas être transmises à l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production.

Vous pouvez afficher la liste des versions de service et des dates de fin de vie dans le fichier suivant : [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Ce fichier ne peut pas être considéré comme une source unique de vérité. Reportez-vous aux sites web officiels des fournisseurs pour ces technologies en cas de doute.

## Informations supplémentaires

[Configuration requise](../../../installation/system-requirements.md)
