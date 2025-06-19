---
title: 'ACSD-52906 : résolution du problème de cookie X-Magento-Vary pour la mise en cache client connectée'
description: Appliquez le correctif ACSD-52906 pour résoudre le problème d’Adobe Commerce en raison duquel le cookie X-Magento-Vary est défini de manière incorrecte pour les clients connectés.
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906 : résolution du problème de cookie X-Magento-Vary pour les clients connectés

Le correctif ACSD-52906 corrige le problème en raison duquel le cookie X-Magento-Vary est incorrectement défini pour les clients connectés. Ce correctif est disponible lorsque la version 1.1.36 de [!DNL Quality Patches Tool (QPT)] est installée. L’ID du correctif est ACSD-52906. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cookie X-Magento-Vary est défini de manière incorrecte pour les clients connectés appartenant au même segment client, ce qui entraîne une mise en cache incorrecte de certaines pages.

<u>Conditions préalables</u> :

Les modules Adobe Commerce Inventory management (MSI) sont installés et activés.

<u>Procédure à suivre </u> :

1. Configurez le cache [!DNL Varnish] ou [!DNL Fastly].
1. Créez un segment client et affectez-le aux clients *enregistrés*.
1. Créez deux clients, par exemple, client1 et client2.
1. Effacez le cache.
1. Connectez-vous en tant que client1 et accédez à la page d’accueil.
1. Ouvrez une page en mode privé dans votre navigateur.
1. Accédez à n’importe quelle page autre que la page d’accueil.
1. Connectez-vous en tant que customer2.
1. Accédez à la page d’accueil.
1. Vérifiez si la page est mise en cache dans la console de développement du navigateur.

<u>Résultats attendus</u> :

La page est récupérée à partir du cache.

<u>Résultats réels</u> :

La page n’est pas mise en cache.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
