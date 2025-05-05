---
title: 'ACSD-61534 : la configuration de conception ne peut pas être définie à l’aide de bin/magento config:set et les valeurs verrouillées peuvent être modifiées par la manipulation de formulaire.'
description: Appliquez le correctif ACSD-61534 pour résoudre le problème Adobe Commerce en raison duquel la configuration de conception ne peut pas être définie à l’aide de la commande bin/magento config:set, et les valeurs verrouillées peuvent être modifiées par la manipulation de formulaire.
feature: Configuration
role: Admin, Developer
source-git-commit: ef00c05593ad319caab8bb9e0f5090959786513f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534 : la configuration de conception ne peut pas être définie à l’aide de `bin/magento config:set`, et les valeurs verrouillées peuvent être modifiées par la manipulation de formulaire.

Le correctif ACSD-61534 corrige le problème en raison duquel la configuration de conception ne peut pas être définie à l’aide de la commande `bin/magento config:set`, et les valeurs verrouillées peuvent être modifiées par la manipulation de formulaire. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-61534. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La configuration de conception ne peut pas être définie à l’aide de la commande `bin/magento config:set` et les valeurs verrouillées peuvent être modifiées par la manipulation de formulaire. Avec ce correctif, les valeurs verrouillées définies à partir de l’outil de ligne de commande avec `--lock-env` ou `--lock-conf` ne peuvent pas être mises à jour.

<u>Étapes à reproduire</u> :

1. Verrouillez une valeur de configuration à l’aide d’une variable d’environnement cloud, telle que `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Accédez au panneau *[!UICONTROL Admin]*.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Cliquez sur **[!UICONTROL Edit]** près de **[!UICONTROL Global/Main website]** dans la deuxième ligne.
1. Thème de modification pour une vue de magasin.
1. Ouvrez la tête de l&#39;HTML.
1. Activez le champ **[!UICONTROL Scripts and Style Sheets]** désactivé à l’aide des outils de développement.
1. Modifiez la valeur et enregistrez-la.

<u>Résultats attendus</u> :

Une valeur verrouillée ne peut pas être enregistrée.

<u>Résultats réels</u> :

La table `core_config_data` contient une valeur mise à jour pour `design/head/includes`.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
