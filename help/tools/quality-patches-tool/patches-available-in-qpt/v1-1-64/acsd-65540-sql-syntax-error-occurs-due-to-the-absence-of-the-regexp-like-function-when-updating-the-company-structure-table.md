---
title: 'ACSD-65540 : une erreur SQL se produit en raison de l''absence de la fonction REGEXP_LIKE dans les mises à jour de la structure de l''entreprise'
description: Appliquez le correctif ACSD-65540 pour résoudre le problème Adobe Commerce où une erreur SQL se produit en raison d'une fonction REGEXP_LIKE manquante dans les mises à jour de la structure de l'entreprise.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
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

```
bin/magento setup:upgrade
```

<u>Résultats attendus</u> :

La mise à niveau est terminée.

<u>Résultats réels</u> :

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
