---
title: Politique d’application de la mise à niveau de la version cloud
description: 'Découvrez l’application des mises à niveau de version pour Adobe Commerce sur le cloud : pourquoi Adobe applique-t-il les mises à niveau, les dates d’application, le déclassement et les actions requises ? Consultez la politique relative au cycle de vie pour connaître les dispositions transitoires et les chemins de migration.'
nudge: false
source-git-commit: 3e0d993078c73a191809c85c1a0ef03ff29a78a6
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Politique d’application de la mise à niveau de version pour Adobe Commerce on Cloud

Lorsque la prise en charge régulière et la prise en charge étendue d’une version d’Adobe Commerce prennent fin, Adobe se réserve le droit de mettre hors service Adobe Commerce sur les environnements cloud qui exécutent toujours cette version non prise en charge. L’application de la mise à niveau de version s’applique uniquement à Adobe Commerce sur les environnements cloud. Les clients sur site gèrent leur propre infrastructure. Adobe vous informe à l’avance et fournit des ressources d’assistance bien avant ces dates afin de vous aider à planifier la mise à niveau ou la migration.

Vous devez passer à une version d’Adobe Commerce prise en charge ou migrer vers [!DNL Adobe Commerce as a Cloud Service] avant la date de publication [fin de la prise en charge étendue](lifecycle-policy.md#end-of-support-dates) pour votre ligne de mise à jour.

Les sections suivantes expliquent pourquoi Adobe applique les mises à niveau, comment les dates d’application sont calculées et ce qui se passe à la date d’application. Pour les dates d’application spécifiques à une version, reportez-vous au tableau [Dates de fin de prise en charge](lifecycle-policy.md#end-of-support-dates) dans la politique relative au cycle de vie.

>[!NOTE]
>
>Cette rubrique traite uniquement de l’application des mises à niveau vers Cloud . Consultez la [politique de cycle de vie](lifecycle-policy.md) pour obtenir des définitions de niveau de prise en charge, [dates de fin de prise en charge](lifecycle-policy.md#end-of-support-dates), [dispositions transitoires de sécurité uniquement](lifecycle-policy.md#security-only-transitional-period), [dépendances de logiciels tiers](lifecycle-policy.md#platform-dependencies), [fin de vie PHP et conformité PCI](lifecycle-policy.md#php-end-of-life-and-pci-compliance) et [options de mise à niveau et de migration](lifecycle-policy.md#upgrade-and-migration-options). En plus de la mise à niveau vers une [!DNL Adobe Commerce version] prise en charge, Adobe exige également que vous conserviez les dépendances de logiciels tiers sur les versions activement prises en charge. Pour connaître les actions et les délais spécifiques requis qui s’appliquent aux versions [!DNL Adobe Commerce on Cloud] 2.4.4 à 2.4.9, consultez l’[avis de sécurité et de conformité](security-enforcement-policy.md).

## Pourquoi Adobe introduit-il cette politique ?

Adobe est responsable de la sécurité et de la conformité de l’infrastructure de plateforme hébergée sur laquelle s’exécutent les clients Adobe Commerce on Cloud. Cela inclut la mise à jour de toutes les dépendances logicielles sous-jacentes, l’application de correctifs de sécurité et le respect des normes de conformité, telles que PCI, sur lesquelles les clients comptent.

Lorsque les fournisseurs mettent officiellement fin à la prise en charge de la sécurité des dépendances logicielles sous-jacentes, Adobe ne peut plus fournir le niveau de sécurité requis ni la prise en charge de la plateforme. Continuer à gérer des magasins sur des infrastructures non prises en charge expose les clients, leurs acheteurs et Adobe à des risques inacceptables. Adobe introduit donc une politique d’application de mise à niveau formelle qui définit le moment où Adobe Commerce sur les environnements cloud exécutant des versions de Commerce non prises en charge sont désactivées, ainsi que la prise en charge fournie par Adobe pour vous aider à planifier votre mise à niveau ou migration. Pour plus d’informations, consultez l’[avis de sécurité et de conformité].

## Calcul des dates d’application de la mise à niveau

Pour chaque ligne de version d’Adobe Commerce, la date d’application de la mise à niveau est calculée comme suit :

**Date d’application de la mise à niveau** = Date de disponibilité générale + 3 ans d’assistance régulière + jusqu’à 1 an d’assistance étendue

La prise en charge étendue est annoncée peu avant la fin de la prise en charge régulière de chaque ligne de version.

## Ce qui se passe à la date d’application de la mise à niveau de version

À la date d’application de la mise à niveau publiée, Adobe arrêtera la maintenance de tous les environnements Adobe Commerce sur Cloud qui exécutent toujours la version affectée et se réserve le droit de les mettre hors service. Vous recevrez des notifications avancées aux jalons clés menant à la date d’application de la mise à niveau de version. Adobe fournit une fenêtre d’exportation des données avant la désactivation de l’environnement afin que vous puissiez récupérer vos données.

La première date d’application de cette politique est le **1er juin 2027** pour les lignes de version qui atteignent la fin de la prise en charge étendue avant cette date. Consultez le tableau [Dates de fin de prise en charge](lifecycle-policy.md#end-of-support-dates) pour connaître les dates d’application spécifiques à chaque version.
