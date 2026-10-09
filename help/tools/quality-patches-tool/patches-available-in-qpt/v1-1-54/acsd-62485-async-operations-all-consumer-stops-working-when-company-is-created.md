---
title: 'ACSD-62485 : le client « async.operations.all » cesse de fonctionner lors de la création de l’entreprise'
description: Appliquez le correctif ACSD-62485 pour résoudre le problème d’Adobe Commerce en raison duquel le client « async.operations.all » cesse de fonctionner lors de la création d’une société B2B.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%
---
# ACSD-62485 : `async.operations.all` consommateur cesse de fonctionner lors de la création de l’entreprise

Le correctif ACSD-62485 corrige le problème où le consommateur `async.operations.all` cesse de fonctionner lorsqu’une entreprise B2B est créée. Ce correctif est disponible lorsque la version 1.1.54 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-62485. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p7

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le client `async.operations.all` cesse de traiter les messages si une société B2B est créée de manière asynchrone pendant que le client est toujours en cours d’exécution.

<u>Conditions préalables</u> :

Les modules B2B sont installés et activés.

<u>Procédure à suivre </u> :

1. Créez deux clients.
1. Envoyez une requête REST en bloc pour créer deux sociétés et affectez les clients créés en tant qu’administrateurs de société.
1. Démarrez le client à l’aide de la commande suivante :

   `bin/magento queue:consumer:start async.operations.all --max-messages=20000`

<u>Résultats attendus</u> :

Le client traite 20 000 messages et se termine correctement.

<u>Résultats réels</u> :

Le client cesse de travailler immédiatement après l’exécution.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
