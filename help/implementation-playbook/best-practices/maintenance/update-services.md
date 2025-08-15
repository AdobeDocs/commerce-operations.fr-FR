---
title: Bonnes pratiques relatives à la mise à jour des services
description: Découvrez comment mettre à jour votre pile technologique Adobe Commerce sur l’infrastructure cloud.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Bonnes pratiques relatives à la mise à jour des services

Cet article fournit des recommandations pour que votre pile technologique Adobe Commerce sur les infrastructures cloud soit mise à jour et fournit des liens vers des ressources utiles.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud 2.4.x et ultérieures

## Mettre à jour les services

Mettez à niveau les services et les composants utilisés par Adobe Commerce avant qu’ils n’atteignent leur date de fin de vie ou qu’ils n’en soient proches. Cela permet de respecter la conformité PCI et de réduire les vulnérabilités de sécurité.

Les clients disposant de plans de démarrage peuvent se servir des mises à niveau des services. Pour plus d’informations sur la procédure à suivre, voir [Modifier la version du service](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version).

Les clients avec forfaits Pro ne peuvent se servir que des mises à niveau de services dans leur [environnement d’intégration](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html?lang=fr). Pour les mises à niveau des services en production, vous devez [soumettre un ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=fr#submit-ticket) demander la mise à niveau.

>[!WARNING]
>
>Les mises à niveau de service ne peuvent pas être envoyées à un environnement de production sans préavis de 48 heures ouvrables à l’équipe d’infrastructure d’Adobe. Cela est nécessaire afin qu’Adobe puisse s’assurer qu’un ingénieur d’assistance en infrastructure est disponible pour mettre à jour votre configuration dans le délai souhaité avec un temps d’arrêt minimal pour votre environnement de production. Adobe recommande de mettre votre site en mode de maintenance pendant la mise à niveau du service.

Vous pouvez consulter la liste des versions de service et des dates de fin de vie dans le fichier suivant : [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Ce fichier ne peut pas être considéré comme une source unique de vérité. En cas de doute, consultez les sites web officiels des fournisseurs pour ces technologies.

## Informations supplémentaires

[Configuration requise](../../../installation/system-requirements.md)
