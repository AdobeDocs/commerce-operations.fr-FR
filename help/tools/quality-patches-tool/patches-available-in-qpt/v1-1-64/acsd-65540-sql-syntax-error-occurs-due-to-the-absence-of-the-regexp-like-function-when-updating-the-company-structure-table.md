---
title: 'ACSD-65540 : une erreur SQL se produit en raison de l''absence de la fonction REGEXP_LIKE dans les mises à jour de la structure de l''entreprise'
description: Appliquez le correctif ACSD-65540 pour résoudre le problème Adobe Commerce où une erreur SQL se produit en raison d'une fonction REGEXP_LIKE manquante dans les mises à jour de la structure de l'entreprise.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '275'
ht-degree: 0%
---
# ACSD-65540 : une erreur SQL se produit en raison d&#39;une fonction `REGEXP_LIKE` manquante dans les mises à jour `company_structure`

Le correctif ACSD-65540 corrige le problème où l’erreur SQL se produit en raison d’une fonction `REGEXP_LIKE` manquante dans les mises à jour `company_structure`. Ce correctif est disponible lorsque la version 1.1.64 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-65540.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce B2B (toutes les méthodes de déploiement) 1.5.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce B2B (toutes les méthodes de déploiement) 1.5.2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur de syntaxe SQL se produit en raison d&#39;une fonction `REGEXP_LIKE` manquante dans les mises à jour `company_structure`.

<u>Procédure à suivre </u> :

1. Mettez à jour [!DNL B2B] vers la version 1.5.2.
1. Exécutez la commande suivante :

```shell
bin/magento setup:upgrade
```

<u>Résultats attendus</u> :

La mise à niveau est terminée.

<u>Résultats réels</u> :

```text
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
