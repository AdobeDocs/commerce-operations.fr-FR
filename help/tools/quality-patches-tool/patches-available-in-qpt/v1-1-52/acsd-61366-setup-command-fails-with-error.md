---
title: 'ACSD-61366 : la commande « bin/magento setup:static-content:deploy —jobs 4 » rencontre plusieurs échecs de tâche avec une erreur'
description: Appliquez le correctif ACSD-61366 pour résoudre le problème d’Adobe Commerce où la commande « bin/magento setup:static-content:deploy —jobs 4 » rencontre plusieurs échecs de tâche avec l’erreur « Le port doit être configuré dans le paramètre hôte », bien que le port pour la connexion à la base de données ait été spécifié.
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366 : la commande `bin/magento setup:static-content:deploy --jobs 4` rencontre plusieurs échecs de tâche avec une erreur

Le correctif ACSD-61366 corrige le problème où la commande `bin/magento setup:static-content:deploy --jobs 4` rencontre plusieurs échecs de tâche avec l’erreur *Le port doit être configuré dans le paramètre host*, bien que spécifiant le port pour la connexion à la base de données. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-61366. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La commande `bin/magento setup:static-content:deploy --jobs 4` rencontre plusieurs échecs de tâche avec l’erreur *Le port doit être configuré dans le paramètre host*, bien que le port de la connexion à la base de données ait été spécifié.

<u>Procédure à suivre </u> :

1. Spécifiez un port dans la connexion à la base de données dans `app/etc/env.php`.
1. Exécutez `bin/magento setup:static-content:deploy --jobs 4` commande .

<u>Résultats attendus</u> :

Le déploiement du contenu statique s’est terminé avec succès.

<u>Résultats réels</u> :

La commande échoue avec l’erreur *Le port doit être configuré dans le paramètre hôte*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
