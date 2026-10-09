---
title: Bonnes pratiques relatives à la mise à jour des services
description: Découvrez comment mettre à jour votre pile technologique Adobe Commerce sur l’infrastructure cloud.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%
---
# Bonnes pratiques relatives à la mise à jour des services

Cet article fournit des recommandations pour que votre pile technologique Adobe Commerce sur les infrastructures cloud soit mise à jour et fournit des liens vers des ressources utiles.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud 2.4.x et ultérieures

## Mettre à jour les services

Mettez à niveau les services et les composants utilisés par Adobe Commerce avant qu’ils n’atteignent leur date de fin de vie ou qu’ils n’en soient proches. Cela permet de respecter la conformité PCI et de réduire les vulnérabilités de sécurité.

Les clients disposant de plans de démarrage peuvent se servir des mises à niveau des services. Pour plus d’informations sur la procédure à suivre, voir [Modifier la version du service](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure/service/services-yaml#change-service-version).

Les clients avec forfaits Pro ne peuvent se servir que des mises à niveau de services dans leur [environnement d’intégration](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27242). Pour les mises à niveau des services en production, vous devez [soumettre un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) demander la mise à niveau.

>[!WARNING]
>
>Les mises à niveau de service ne peuvent pas être envoyées à un environnement de production sans préavis de 48 heures ouvrables à l’équipe d’infrastructure d’Adobe. Cela est nécessaire afin qu’Adobe puisse s’assurer qu’un ingénieur d’assistance en infrastructure est disponible pour mettre à jour votre configuration dans le délai souhaité avec un temps d’arrêt minimal pour votre environnement de production. Adobe recommande de mettre votre site en mode de maintenance pendant la mise à niveau du service.

Vous pouvez consulter la liste des versions de service et des dates de fin de vie dans le fichier suivant : [&#128279;](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Ce fichier ne peut pas être considéré comme une source unique de vérité. En cas de doute, consultez les sites web officiels des fournisseurs pour ces technologies.

## Informations supplémentaires

[Configuration requise](../../../installation/system-requirements.md)
