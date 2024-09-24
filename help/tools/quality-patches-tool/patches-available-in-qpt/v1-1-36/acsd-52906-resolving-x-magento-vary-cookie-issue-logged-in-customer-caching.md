---
title: "ACSD-52906 : résolution du problème de cookie X-Magento-Vary pour la mise en cache du client connecté"
description: Appliquez le correctif ACSD-52906 pour résoudre le problème Adobe Commerce en raison duquel le cookie X-Magento-Vary est mal défini pour les clients connectés.
feature: Cache
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-52906 : résolution du problème de cookie X-Magento-Vary pour les clients connectés

Le correctif ACSD-52906 corrige le problème en raison duquel le cookie X-Magento-Vary est mal défini pour les clients connectés. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.36 est installé. L’ID de correctif est ACSD-52906. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cookie X-Magento-Vary n’est pas défini correctement pour les clients connectés qui appartiennent au même segment de client, ce qui entraîne une mise en cache incorrecte de certaines pages.

<u>Conditions préalables</u> :

Les modules Adobe Commerce Inventory management (MSI) sont installés et activés.

<u>Étapes à reproduire</u> :

1. Configurez le cache [!DNL Varnish] ou [!DNL Fastly].
1. Créez un segment de client et affectez-le aux clients *Registered*.
1. Créez deux clients, par exemple customer1 et customer2.
1. Effacez le cache.
1. Connectez-vous en tant que customer1 et accédez à la page d’accueil.
1. Ouvrez une page d’incognito dans votre navigateur.
1. Accédez à une page autre que la page d’accueil.
1. Connectez-vous en tant que customer2.
1. Accédez à la page d’accueil.
1. Vérifiez si la page est mise en cache dans la console de développement du navigateur.

<u>Résultats attendus</u> :

La page est récupérée dans le cache.

<u>Résultats réels</u> :

La page n’est pas mise en cache.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
