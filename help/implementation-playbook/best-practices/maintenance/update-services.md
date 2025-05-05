---
title: Bonnes pratiques relatives aux services de mise à jour
description: Découvrez comment conserver votre Adobe Commerce sur la pile de technologie de l’infrastructure cloud mise à jour.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Bonnes pratiques relatives aux services de mise à jour

Cet article fournit des recommandations pour que votre Adobe Commerce reste à jour sur la pile de technologie de l’infrastructure cloud et fournit des liens vers des ressources utiles.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.4.x et versions ultérieures

## Mise à jour des services

Mettez à niveau les services et les composants utilisés par Adobe Commerce avant qu’ils n’atteignent ou ne se rapprochent de la date de fin de vie. Cela permet de respecter la conformité PCI et de réduire les vulnérabilités de sécurité.

Les clients utilisant des plans de démarrage peuvent se servir eux-mêmes lors des mises à niveau de services. Pour plus d&#39;informations sur la façon de procéder, reportez-vous à la section [Modification de la version de service](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) .

Les clients sur les plans Pro ne peuvent utiliser que les mises à niveau de services en libre-service dans leur [environnement d’intégration](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html?lang=fr). Pour les mises à niveau de services en production, vous devez [envoyer un ticket d&#39;assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=fr#submit-ticket) demandant la mise à niveau.

>[!WARNING]
>
>Les mises à niveau de service ne peuvent pas être transférées vers un environnement de production sans préavis de 48 heures ouvrables à l’équipe d’infrastructure d’Adobe. Cela est nécessaire afin qu’Adobe puisse s’assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais impartis, avec un temps d’arrêt minimal pour votre environnement de production. Adobe recommande de mettre votre site en mode de maintenance lors de la mise à niveau du service.

Vous pouvez afficher la liste des versions de service et des dates de fin de vie dans le fichier suivant : [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Ce fichier ne peut pas être considéré comme une source unique de vérité. Reportez-vous aux sites web officiels des fournisseurs pour ces technologies en cas de doute.

## Informations supplémentaires

[Configuration requise](../../../installation/system-requirements.md)
