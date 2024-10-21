---
title: "ACSD-61366 : la commande `bin/magento setup:static-content:deploy —jobs 4` rencontre plusieurs échecs de tâche avec une erreur"
description: Appliquez le correctif ACSD-61366 pour résoudre le problème Adobe Commerce en raison duquel la commande `bin/magento setup:static-content:deploy —jobs 4` rencontre plusieurs échecs de tâche avec le *Port doit être configuré dans l’erreur de paramètre d’hôte*, même si le port de la connexion DB est spécifié.
feature: SCD
role: Admin, Developer
source-git-commit: b671dc30cd511d63dbbbaa6edd47ee36c1351620
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366 : la commande `bin/magento setup:static-content:deploy --jobs 4` rencontre plusieurs échecs de tâche avec une erreur

Le correctif ACSD-61366 corrige le problème en raison duquel la commande `bin/magento setup:static-content:deploy --jobs 4` rencontre plusieurs échecs de tâche avec l’erreur *Port doit être configurée dans le paramètre hôte*, bien que la spécification du port pour la connexion DB. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 est installé. L’ID de correctif est ACSD-61366. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La commande `bin/magento setup:static-content:deploy --jobs 4` rencontre plusieurs échecs de tâche avec le *port doit être configuré dans l’erreur de paramètre hôte*, même si vous spécifiez le port pour la connexion DB.

<u>Étapes à reproduire</u> :

1. Spécifiez un port dans la connexion à la base de données dans `app/etc/env.php`.
1. Exécutez la commande `bin/magento setup:static-content:deploy --jobs 4`.

<u>Résultats attendus</u> :

Le déploiement du contenu statique se termine correctement.

<u>Résultats réels</u> :

La commande échoue avec l&#39;erreur *Port doit être configurée dans le paramètre d&#39;hôte*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].