---
title: 'ACSD-61534 : la configuration de conception ne peut pas être définie à l’aide de bin/magento config:set, et les valeurs verrouillées peuvent être modifiées par manipulation de formulaire'
description: Appliquez le correctif ACSD-61534 pour résoudre le problème d’Adobe Commerce en raison duquel la configuration de conception ne peut pas être définie à l’aide de la commande « bin/magento config:set » et les valeurs verrouillées peuvent être modifiées par manipulation de formulaire.
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534 : la configuration de conception ne peut pas être définie à l’aide de `bin/magento config:set` et les valeurs verrouillées peuvent être modifiées par manipulation de formulaire

Le correctif ACSD-61534 corrige le problème en raison duquel la configuration de conception ne peut pas être définie à l’aide de la commande `bin/magento config:set` et les valeurs verrouillées peuvent être modifiées par manipulation de formulaire. Ce correctif est disponible lorsque la version 1.1.55 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61534. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La configuration de conception ne peut pas être définie à l’aide de la commande `bin/magento config:set` et les valeurs verrouillées peuvent être modifiées par manipulation de formulaire. Avec ce correctif, les valeurs verrouillées définies à partir de l’outil de ligne de commande (CLI) avec `--lock-env` ou `--lock-conf` ne peuvent pas être mises à jour.

<u>Procédure à suivre </u> :

1. Verrouillez une valeur de configuration à l’aide d’une variable d’environnement cloud, comme `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`.
1. Accédez au panneau *[!UICONTROL Admin]* .
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Cliquez sur **[!UICONTROL Edit]** près de la **[!UICONTROL Global/Main website]** dans la deuxième ligne.
1. Modifier le thème d’une vue de magasin.
1. Ouvrez la tête d’HTML.
1. Activez le champ **[!UICONTROL Scripts and Style Sheets]** désactivé à l’aide des outils de développement.
1. Modifiez la valeur et enregistrez-la.

<u>Résultats attendus</u> :

Impossible d’enregistrer une valeur verrouillée.

<u>Résultats réels</u> :

Le tableau `core_config_data` contient une valeur mise à jour pour `design/head/includes`.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
