---
title: "ACSD-62485: `async.operations.all` le consommateur cesse de fonctionner lors de la création de l’entreprise"
description: Appliquez le correctif ACSD-62485 pour résoudre le problème Adobe Commerce en raison duquel le consommateur "async.operations.all" cesse de fonctionner lors de la création d’une entreprise B2B.
feature: B2B, Companies
role: Admin, Developer
source-git-commit: 8061f6df01c3c308b46e6164300192b01359ce94
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485 : `async.operations.all` le consommateur cesse de fonctionner lors de la création de l’entreprise

Le correctif ACSD-62485 corrige le problème où le consommateur `async.operations.all` cesse de fonctionner lorsqu’une société B2B est créée. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-62485. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le consommateur `async.operations.all` cesse de traiter les messages si une société B2B est créée de manière asynchrone alors que le consommateur est toujours en cours d’exécution.

<u>Conditions préalables</u> :

Les modules B2B sont installés et activés.

<u>Étapes à reproduire</u> :

1. Créez deux clients.
1. Envoyez une requête en bloc REST pour créer deux sociétés, en attribuant les clients créés en tant qu’administrateurs d’entreprise.
1. Démarrez le consommateur à l’aide de la commande suivante :

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Résultats attendus</u> :

Le consommateur traite 20 000 messages et se termine avec succès.

<u>Résultats réels</u> :

Le consommateur cesse de travailler immédiatement lors de son exécution.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
