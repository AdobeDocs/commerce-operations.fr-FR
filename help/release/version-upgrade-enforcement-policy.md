---
title: Politique d’application de la mise à niveau de la version cloud
description: 'Découvrez l’application des mises à niveau de version pour Adobe Commerce sur le cloud : pourquoi Adobe applique-t-il les mises à niveau, les dates d’application, le déclassement et les actions requises ? Consultez la politique relative au cycle de vie pour connaître les dispositions transitoires et les chemins de migration.'
nudge: true
source-git-commit: eacee993ec38cce7763d4c99b1bbb67a319d8c1a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Politique d’application de la mise à niveau de version pour Adobe Commerce on Cloud

Lorsque la prise en charge régulière et la prise en charge étendue d’une version d’Adobe Commerce prennent fin, Adobe se réserve le droit de mettre hors service Adobe Commerce sur les environnements cloud qui exécutent toujours cette version non prise en charge. L’application de la mise à niveau de version s’applique uniquement aux environnements Adobe Commerce sur le cloud ; les clients sur site gèrent leur propre infrastructure.

Vous devez passer à une version d’Adobe Commerce prise en charge ou migrer vers [!DNL Adobe Commerce as a Cloud Service] avant la date de publication [fin de la prise en charge étendue](lifecycle-policy.md#end-of-support-dates) pour votre ligne de mise à jour.

Les sections suivantes expliquent pourquoi Adobe applique les mises à niveau, comment les dates d’application sont calculées et ce qui se passe à la date d’application. Pour les dates d’application spécifiques à une version, reportez-vous au tableau [Dates de fin de prise en charge](lifecycle-policy.md#end-of-support-dates) dans la politique relative au cycle de vie.

>[!NOTE]
>
>Cette rubrique traite uniquement de l’application des mises à niveau vers Cloud . Pour les définitions du niveau de prise en charge, le tableau [dates de fin de prise en charge](lifecycle-policy.md#end-of-support-dates), les [dispositions transitoires réservées à la sécurité](lifecycle-policy.md#security-only-transitional-period), les [dépendances de logiciels tiers](lifecycle-policy.md#platform-dependencies), les [fin de vie de PHP et conformité PCI](lifecycle-policy.md#php-end-of-life-and-pci-compliance) et les [options de mise à niveau et de migration](lifecycle-policy.md#upgrade-and-migration-options), consultez la politique [cycle de vie](lifecycle-policy.md). En plus de la mise à niveau vers une version d’Adobe Commerce prise en charge, Adobe exige également que vous conserviez les dépendances de logiciels tiers sur les versions activement prises en charge.

## Pourquoi Adobe introduit-il cette politique ?

Adobe est responsable de la sécurité et de la conformité de l’infrastructure de plateforme hébergée sur laquelle s’exécutent les clients Adobe Commerce on Cloud. Cela inclut la mise à jour de toutes les dépendances logicielles sous-jacentes, l’application de correctifs de sécurité et le respect des normes de conformité, telles que PCI, sur lesquelles les clients comptent.

Lorsque la prise en charge de la sécurité des dépendances logicielles sous-jacentes est officiellement arrêtée par les fournisseurs, Adobe ne peut plus fournir le niveau de couverture de sécurité et de prise en charge de la plateforme requis. Continuer à gérer des magasins sur des infrastructures non prises en charge expose les clients, leurs acheteurs et Adobe à des risques inacceptables. Adobe introduit donc une politique d’application de mise à niveau de version formelle qui définit le moment où Adobe Commerce sur les environnements cloud exécutant des versions Commerce non prises en charge sera désactivé.

## Calcul des dates d’application de la mise à niveau

Pour chaque ligne de version d’Adobe Commerce, la date d’application de la mise à niveau est calculée comme suit :

**Date d’application de la mise à niveau** = Date de disponibilité générale + 3 ans d’assistance régulière + jusqu’à 1 an d’assistance étendue

La prise en charge étendue est annoncée peu avant la fin de la prise en charge régulière de chaque ligne de version.

## Ce qui se passe à la date d’application de la mise à niveau de version

À la date d’application de la mise à niveau publiée, Adobe arrêtera la maintenance de tous les environnements Adobe Commerce sur Cloud qui exécutent toujours la version affectée et se réserve le droit de les mettre hors service. Vous recevrez des notifications avancées aux jalons clés menant à la date d’application de la mise à niveau de version. Adobe fournit une fenêtre d’exportation des données avant la désactivation de l’environnement afin que vous puissiez récupérer vos données.

La première date d’application de cette politique est le **1er juin 2027** pour les lignes de version qui atteignent la fin de la prise en charge étendue avant cette date. Consultez le tableau [Dates de fin de prise en charge](lifecycle-policy.md#end-of-support-dates) pour connaître les dates d’application spécifiques à chaque version.
